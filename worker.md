Name:               worker-czqxby                                                                                                                   │
│ Roles:              <none>                                                                                                                          │
│ Labels:             beta.kubernetes.io/arch=amd64                                                                                                   │
│                     beta.kubernetes.io/os=linux                                                                                                     │
│                     heat=cos1-k8s-workers-lcl_hors_prod-v1.28                                                                                       │
│                     ingress=false                                                                                                                   │
│                     kubernetes.io/arch=amd64                                                                                                        │
│                     kubernetes.io/hostname=worker-czqxby                                                                                            │
│                     kubernetes.io/os=linux                                                                                                          │
│                     topology.kubernetes.io/region=intranet                                                                                          │
│                     topology.kubernetes.io/zone=dalembert-az                                                                                        │
│ Annotations:        csi.volume.kubernetes.io/nodeid: {"csi.oneagent.dynatrace.com":"worker-czqxby","csi.tigera.io":"worker-czqxby"}                 │
│                     kubeadm.alpha.kubernetes.io/cri-socket: unix:///var/run/containerd/containerd.sock                                              │
│                     node.alpha.kubernetes.io/ttl: 0                                                                                                 │
│                     projectcalico.org/IPv4Address: 10.28.64.61/25                                                                                   │
│                     projectcalico.org/IPv4VXLANTunnelAddr: 172.20.246.0                                                                             │
│                     volumes.kubernetes.io/controller-managed-attach-detach: true                                                                    │
│                     weave.works/kured-most-recent-reboot-needed: 2025-02-10T05:11:27Z                                                               │
│ CreationTimestamp:  Thu, 10 Oct 2024 18:02:33 +0200                                                                                                 │
│ Taints:             <none>                                                                                                                          │
│ Unschedulable:      false                                                                                                                           │
│ Lease:                                 
 AcquireTime:     <unset>                                                                                                                          │
│   RenewTime:       Fri, 14 Feb 2025 14:56:50 +0100                                                                                                  │
│ Conditions:                                                                                                                                         │
│   Type                 Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message             │
│   ----                 ------  -----------------                 ------------------                ------                       -------             │
│   NetworkUnavailable   False   Wed, 12 Feb 2025 21:53:38 +0100   Wed, 12 Feb 2025 21:53:38 +0100   CalicoIsUp                   Calico is running o │
│ n this node                                                                                                                                         │
│   MemoryPressure       False   Fri, 14 Feb 2025 14:52:08 +0100   Wed, 12 Feb 2025 21:52:36 +0100   KubeletHasSufficientMemory   kubelet has suffici │
│ ent memory available                                                                                                                                │
│   DiskPressure         False   Fri, 14 Feb 2025 14:52:08 +0100   Wed, 12 Feb 2025 21:52:36 +0100   KubeletHasNoDiskPressure     kubelet has no disk │
│  pressure                                                                                                                                           │
│   PIDPressure          False   Fri, 14 Feb 2025 14:52:08 +0100   Wed, 12 Feb 2025 21:52:36 +0100   KubeletHasSufficientPID      kubelet has suffici │
│ ent PID available                                                                                                                                   │
│   Ready                True    Fri, 14 Feb 2025 14:52:08 +0100   Wed, 12 Feb 2025 21:52:36 +0100   KubeletReady                 kubelet is posting  │
│ ready status. AppArmor enabled                                                                                                                      │
│ Addresses:                                                                                                                                          │
│   InternalIP:  10.28.64.61                                                                                                                          │
│   Hostname:    worker-czqxby                                                                                                                        │
│ Capacity:                                                                                                                                           │
│   cpu:                16                                                                                                                            │
│   ephemeral-storage:  81106868Ki                                                                                                                    │
│   hugepages-1Gi:      0                    │

│   HolderIdentity:  worker-czqxby 
 PodCIDR:                                      172.20.113.0/24                                                                                       │
│ PodCIDRs:                                     172.20.113.0/24                                                                                       │
│ Non-terminated Pods:                          (70 in total)                                                                                         │
│   Namespace                                   Name                                                               CPU Requests  CPU Limits  Memory R │
│ equests  Memory Limits  Age                                                                                                                         │
│   ---------                                   ----                                                               ------------  ----------  -------- │
│ -------  -------------  ---                                                                                                                         │
│   abkip2-05154-metier-development             dvl-abkip-frontend-5b44cfbbb7-vk74h                                50m (0%)      200m (1%)   191Mi (0 │
│ %)       191Mi (0%)     41h                                                                                                                         │
│   abkip2-05154-metier-development             dvl-oidc-test-6c94959c97-6722b                                     50m (0%)      1 (6%)      512Mi (0 │
│ %)       512Mi (0%)     40h                                                                                                                         │
│   abkip2-05154-metier-development             dvl-sso-oidc-97ccbc66f-kgcgh                                       50m (0%)      1 (6%)      512Mi (0 │
│ %)       512Mi (0%)     41h                                                                                                                         │
│   adminbad-03899-metier-integration           int-wshabil-74b4696697-4xbw8                                       50m (0%)      500m (3%)   256Mi (0 │
│ %)       256Mi (0%)     41h                                                                                                                         │
│   adminbad-03899-metier-uat                   rct-wsauth-5988bb67d9-cmzgl                                        50m (0%)      500m (3%)   256Mi (0 
 calico-system                               calico-node-7fpwp                                                  250m (1%)     0 (0%)      0 (0%)   │
│          0 (0%)         42h                                                                                                                         │
│   calico-system                               csi-node-driver-glqpj                                              0 (0%)        0 (0%)      0 (0%)   │
│          0 (0%)         83d                                                  
dynatrace                                   dynakube-oneagent-gzftm                                            100m (0%)     1 (6%)      512Mi (0 │
│ %)       1Gi (1%)       15d                                                                                                                         │
│   dynatrace                                   dynatrace-oneagent-csi-driver-tl4jg                                390m (2%)     200m (1%)   260Mi (0 │
│ %)       300Mi (0%)     35d                                                                                                                         │
│   elastic-beats                               filebeat-workers-6wzb5                                             100m (0%)     0 (0%)      500Mi (0 │
│ %)       1000Mi (1%)    37h                                                                                                                         │
│   elastic-beats                               metricbeat-n6ntr                                                   100m (0%)     0 (0%)      1000Mi ( │
│ 1%)      1000Mi (1%)    37h                                                              
