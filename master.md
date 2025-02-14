Name:               master-002  
NAMESPACE↑     NAME                                       PF READY STATUS   RESTARTS CPU  MEM %CPU/R %CPU/L %MEM/R %MEM/L IP             NODE       │
│ calico-system  calico-node-pgl6x                          ●  1/1   Running         3  39  264     15    n/a    n/a    n/a 10.56.137.72   master-002 │
│ calico-system  calico-typha-68b796d655-swx4z              ●  1/1   Running         1   6  106    n/a    n/a    n/a    n/a 10.56.137.72   master-002 │
│ calico-system  csi-node-driver-sldmt                      ●  2/2   Running        12   0    9    n/a    n/a    n/a    n/a 172.20.230.8   master-002 │
│ dynatrace      dynatrace-oneagent-csi-driver-2zxd5        ●  4/4   Running        20   0   44      0    n/a     17    n/a 172.20.230.9   master-002 │
│ elastic-beats  filebeat-masters-zfld4                     ●  1/1   Running         0  19   57     19    n/a     57     11 172.20.230.13  master-002 │
│ kube-system    coredns-7b6dc7894d-vmlfp                   ●  1/1   Running         1 355   52    355    n/a     74     30 172.20.230.5   master-002 │
│ kube-system    kube-apiserver-master-002                  ●  1/1   Running        10 334 5028    133    n/a    n/a    n/a 10.56.137.72   master-002 │
│ kube-system    kube-proxy-bvbmw                           ●  1/1   Running         9 176   76    n/a    n/a    n/a    n/a 10.56.137.72   master-002 │
│ kube-system    kube-scheduler-master-002                  ●  1/1   Running        12   9  242      9    n/a    n/a    n/a 10.56.137.72   master-002 │
│ kured          kured-r9svr                                ●  1/1   Running         1   0   17      0    n/a      8      8 172.20.230.4   master-002 │
│ miscellaneous  kgb-agent-ql4wt                            ●  1/1   Running        19   0    9    n/a    n/a    n/a    n/a 10.56.137.72   master-002 │
│ monitoring     prometheus-prometheus-node-exporter-tqvxz  ●  1/1   Running        18  13   21    n/a    n/a    n/a    n/a 10.56.137.72   master-002 │

│ Name:               master-002                                                                                                                      │
│ Roles:              control-plane                                                                                                                   │
│ Labels:             beta.kubernetes.io/arch=amd64                                                                                                   │
│                     beta.kubernetes.io/os=linux                                                                                                     │
│                     high_workload=disabled                                                                                                          │
│                     ingress=false                                                                                                                   │
│                     kubernetes.io/arch=amd64                                                                                                        │
│                     kubernetes.io/hostname=master-002                                                                                               │
│                     kubernetes.io/os=linux                                                                                                          │
│                     node-role.kubernetes.io/control-plane=                                                                                          │
│                     node.kubernetes.io/exclude-from-external-load-balancers=                                                                        │
│                     topology.kubernetes.io/region=intranet                                                                                          │
│                     topology.kubernetes.io/zone=diderot-az                                                                                          │
│ Annotations:        csi.volume.kubernetes.io/nodeid: {"csi.oneagent.dynatrace.com":"master-002","csi.tigera.io":"master-002"}                       │
│                     kubeadm.alpha.kubernetes.io/cri-socket: unix:///var/run/containerd/containerd.sock                                              │
│                     node.alpha.kubernetes.io/ttl: 0                                                                                                 │
│                     projectcalico.org/IPv4Address: 10.56.137.72/24                                                                                  │
│                     projectcalico.org/IPv4VXLANTunnelAddr: 172.20.230.0                                                                             │
│                     volumes.kubernetes.io/controller-managed-attach-detach: true                                                                    │
│                     weave.works/kured-most-recent-reboot-needed: 2025-02-12T05:08:45Z                                                               │
│ CreationTimestamp:  Mon, 25 Oct 2021 11:39:09 +0200                                                                                                 │
│ Taints:             node-role.kubernetes.io/control-plane:NoSchedule
Kube-Proxy Version:         v1.28.14                                                                                                              │
│ PodCIDR:                      172.20.34.0/24                                                                                                        │
│ PodCIDRs:                     172.20.34.0/24                                                                                                        │
│ Non-terminated Pods:          (12 in total)                                                                                                         │
│   Namespace                   Name                                         CPU Requests  CPU Limits  Memory Requests  Memory Limits  Age            │
│   ---------                   ----                                         ------------  ----------  ---------------  -------------  ---            │
│   calico-system               calico-node-pgl6x                            250m (3%)     0 (0%)      0 (0%)           0 (0%)         42h            │
│   calico-system               calico-typha-68b796d655-swx4z                0 (0%)        0 (0%)      0 (0%)           0 (0%)         40h            │
│   calico-system               csi-node-driver-sldmt                        0 (0%)        0 (0%)      0 (0%)           0 (0%)         82d            │
│   dynatrace                   dynatrace-oneagent-csi-driver-2zxd5          390m (4%)     200m (2%)   260Mi (1%)       300Mi (1%)     35d            │
│   elastic-beats               filebeat-masters-zfld4                       100m (1%)     0 (0%)      100Mi (0%)       500Mi (3%)     37h            │
│   kube-system                 coredns-7b6dc7894d-vmlfp                     100m (1%)     0 (0%)      70Mi (0%)        170Mi (1%)     40h            │
│   kube-system                 kube-apiserver-master-002                    250m (3%)     0 (0%)      0 (0%)           0 (0%)         127d           │
│   kube-system                 kube-proxy-bvbmw                             0 (0%)        0 (0%)      0 (0%)           0 (0%)         127d           │
│   kube-system                 kube-scheduler-master-002                    100m (1%)     0 (0%)      0 (0%)           0 (0%)         127d           │
│   kured                       kured-r9svr                                  200m (2%)     0 (0%)      200Mi (1%)       200Mi (1%)     41h            │
│   miscellaneous               kgb-agent-ql4wt                              50m (0%)      100m (1%)   80Mi (0%)        80Mi (0%)      127d           │
    monitoring                  prometheus-prometheus-node-exporter-tqvxz    50m (0%)      100m (1%)   80Mi (0%)        80Mi (0%)      127d           │
│ Allocated resources:                                                                                                                                │
│   (Total limits may be over 100 percent, i.e., overcommitted.)                                                                                      │
│   Resource           Requests     Limits                                                                                                            │
│   --------           --------     ------                                                                                                            │
│   cpu                1490m (18%)  400m (5%)                                                                                                         │
│   memory             790Mi (4%)   1330Mi (8%)                                                                                                       │
│   ephemeral-storage  0 (0%)       0 (0%)                                                                                                            │
│   hugepages-1Gi      0 (0%)       0 (0%)                                                                                                            │
│   hugepages-2Mi      0 (0%)       0 (0%)                             

│   monitoring                  prometheus-prometheus-node-exporter-tqvxz    50m (0%)      100m (1%)   80Mi (0%)        80Mi (0%)      127d           │
│ Allocated resources:                                                                                                                                │
│   (Total limits may be over 100 percent, i.e., overcommitted.)                                                                                      │
│   Resource           Requests     Limits                                                                                                            │
│   --------           --------     ------                                                                                                            │
│   cpu                1490m (18%)  400m (5%) 
