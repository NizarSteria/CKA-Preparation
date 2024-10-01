## Run debug container

### Default Namespace
```
kubectl run -i --tty --rm debug --image=docker-remote.registry.saas.cagip.group.gca/busybox --restart=Never -- sh
```

### Inside client Namespace
```
kubectl run -i --tty --rm debug --requests=cpu=100m,memory=256Mi --limits=memory=256Mi  --image=docker-remote.registry.saas.cagip.group.gca/busybox --restart=Never -n cagip-kapla-development -- sh
```

## Container tcpdump

### Get container id
```bash
kubectl get po <podname> -o jsonpath='{.status.containerStatuses[0].containerID}'
```

### Get iflink
```bash
docker exec <7de19a5ccf29a280127b76acc6468fce751342dcb789a15b451225df5399e058> /bin/bash -c 'cat /sys/class/net/eth0/iflink'
```

### Get the calico id

```bash
ip link | grep ^13
```

### Start dump

```bash
tcpdump -i cali232dceeaea7 -vvvs 1024 -l -A
```

### Number of Pods per Node

```bash
for i in $(kubectl get nodes -l node-role.kubernetes.io/control-plane!= -o custom-columns=NAME:.metadata.name --no-headers); do echo $i; kubectl get po -A -o wide | grep $i | wc -l; done
```

## Debug worker filesystem full

### Verify if /srv/data is full
```bash
df -h /srv/data
```

### Delete all unused images (worker docker)
```bash
docker rmi $(docker images -q)
```

### Verify if /srv/data is full again
```bash
df -h /srv/data
```

### Find in /srv/data the overlay with more GB
```bash
TOP_STORAGE=$(du -hs /srv/data/overlay2/* | grep -Ee '^[0-9]{3}[M]+|[0-9]G' | sort -h |tail -n 10 |tee -a /dev/stderr |awk '{print $2}'|xargs|sed 's/ /|/g')
```

### Get docker containers who use these volumes
```bash
docker inspect $(docker ps -q) | jq '.[]|.Config.Hostname,.Config.Labels."io.kubernetes.pod.name",.GraphDriver.Data.MergedDir,.hovno' | egrep -B2 "$TOP_STORAGE"
```

## Taint

### List node taints
```bash
kubectl get nodes -o custom-columns=NAME:.metadata.name,TAINTS:.spec.taints
```

### Add taint
```bash
kubectl taint --overwrite nodes worker-019 worker-119 os=osf2:NoSchedule
```

### Remove taint
```bash
kubectl taint nodes worker-019 worker-119 os-
```

## etcd-ajout-membre.md

# Ajout d'un membre sortit du Cluster

## Sur master OK (ici master-02 KO)
### Réceupérer l'ID du membre KO
```
ETCDCTL_API=3 etcdctl member list --endpoints https://172.10.0.11:2379,https://172.10.0.12:2379,https://172.10.0.13:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/peer.pem \
--key=/etc/kubernetes/pki/etcd/peer-key.pem
```

### Supprimer le membre KO
```
ETCDCTL_API=3 etcdctl member remove 4b547934d62b605c --endpoints https://172.10.0.11:2379,https://172.10.0.12:2379,https://172.10.0.13:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/peer.pem \
--key=/etc/kubernetes/pki/etcd/peer-key.pem
```


### Ajouter le nouveau membre
```
ETCDCTL_API=3 etcdctl member add master-02 --peer-urls=https://172.10.0.12:2380 --endpoints https://172.10.0.11:2379,https://172.10.0.12:2379,https://172.10.0.13:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/peer.pem \
--key=/etc/kubernetes/pki/etcd/peer-key.pem
```


#### Va printer des vars (à exporter sur le master KO):
```
 export ETCD_NAME="master-02"
 export ETCD_INITIAL_CLUSTER="master-01=https://172.10.0.11:2380,master-03=https://172.10.0.13:2380,master-02=https://172.10.0.12:2380"
 export ETCD_INITIAL_ADVERTISE_PEER_URLS="https://172.10.0.12:2380"
 export ETCD_INITIAL_CLUSTER_STATE="existing"
```

# Sur master-02 KO
```
systemctl stop etcd
rm -rf /var/lib/etcd

export ETCD_NAME="master-02"
export ETCD_INITIAL_CLUSTER="master-01=https://172.10.0.11:2380,master-03=https://172.10.0.13:2380,master-02=https://172.10.0.12:2380"
export ETCD_INITIAL_ADVERTISE_PEER_URLS="https://172.10.0.12:2380"
export ETCD_INITIAL_CLUSTER_STATE="existing"


etcd \
    --name=master-02 \
    --advertise-client-urls=https://172.10.0.12:2379 \
    --cert-file=/etc/kubernetes/pki/apiserver.crt  \
    --client-cert-auth=true \
    --data-dir=/var/lib/etcd \
    --initial-cluster-state=existing \
    --initial-cluster-token=my-etcd-token \
    --initial-advertise-peer-urls=https://172.10.0.12:2380 \
    --initial-cluster="master-01=https://172.10.0.11:2380,master-02=https://172.10.0.12:2380,master-03=https://172.10.0.13:2380" \
    --key-file=/etc/kubernetes/pki/etcd/server.key \
    --listen-client-urls=https://172.10.0.12:2379 \
    --listen-peer-urls=https://172.10.0.12:2380 \
    --peer-cert-file=/etc/kubernetes/pki/etcd/peer.pem \
    --peer-client-cert-auth=true \
    --peer-key-file=/etc/kubernetes/pki/etcd/peer-key.pem \
    --peer-trusted-ca-file=/etc/kubernetes/pki/etcd/ca.crt \
    --snapshot-count=10000 \
    --trusted-ca-file=/etc/kubernetes/pki/ca.crt \
    --strict-reconfig-check


systemctl start etcd
```






### Check apiserver over etcd 
```bash
kubectl get --raw='/readyz?verbose'
```
