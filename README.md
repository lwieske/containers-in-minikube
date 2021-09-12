# Some Demonstrations with Minikube and Containers

## Cleaning Up

First, the traces of former executions of  *minikube* are eliminated, the cluster itself (stop, delete) and further initialization steps in the cache directory to establish a clean base.


```python
!minikube stop ; minikube delete ; rm -rf ~/.minikube/cache
```

    ✋  Stopping node "minikube"  ...
    🛑  Powering off "minikube" via SSH ...
    🛑  1 nodes stopped.
    🔥  Deleting "minikube" in docker ...
    🔥  Deleting container "minikube" ...
    🔥  Removing /Users/lothar/.minikube/machines/minikube ...
    💀  Removed all traces of the "minikube" cluster.


## Start The First Cluster


```python
!KUBERNETES_VERSION=1.22.1 minikube start --kubernetes-version=${KUBERNETES_VERSION}
```

    😄  minikube v1.23.0 on Darwin 11.5.2
    ✨  Automatically selected the docker driver. Other choices: hyperkit, virtualbox, ssh, podman (experimental)
    👍  Starting control plane node minikube in cluster minikube
    🚜  Pulling base image ...
    💾  Downloading Kubernetes v1.22.1 preload ...
        > preloaded-images-k8s-v12-v1...: 515.04 MiB / 515.04 MiB  100.00% 6.08 MiB
    🔥  Creating docker container (CPUs=2, Memory=1987MB) ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
    🐳  Preparing Kubernetes v1.22.1 on Docker 20.10.8 ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Generating certificates and keys ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Booting up control plane ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Configuring RBAC rules ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
    🔎  Verifying Kubernetes components...
        ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
    🌟  Enabled addons: storage-provisioner, default-storageclass
    🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default


## Checking Readiness


```python
!kubectl get nodes
```

    NAME       STATUS     ROLES                  AGE   VERSION
    minikube   NotReady   control-plane,master   10s   v1.22.1



```python
!sleep 10 ; kubectl get nodes
```

    NAME       STATUS   ROLES                  AGE   VERSION
    minikube   Ready    control-plane,master   20s   v1.22.1


## Start Cluster With Preloaded Cache


```python
!minikube stop ; minikube delete
```

    ✋  Stopping node "minikube"  ...
    🛑  Powering off "minikube" via SSH ...
    🛑  1 nodes stopped.
    🔥  Deleting "minikube" in docker ...
    🔥  Deleting container "minikube" ...
    🔥  Removing /Users/lothar/.minikube/machines/minikube ...
    💀  Removed all traces of the "minikube" cluster.



```python
!KUBERNETES_VERSION=1.22.1 minikube start --kubernetes-version=${KUBERNETES_VERSION}
```

    😄  minikube v1.23.0 on Darwin 11.5.2
    ✨  Automatically selected the docker driver. Other choices: hyperkit, virtualbox, ssh, podman (experimental)
    👍  Starting control plane node minikube in cluster minikube
    🚜  Pulling base image ...
    🔥  Creating docker container (CPUs=2, Memory=1987MB) ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
    🐳  Preparing Kubernetes v1.22.1 on Docker 20.10.8 ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Generating certificates and keys ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Booting up control plane ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
        ▪ Configuring RBAC rules ...[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
    🔎  Verifying Kubernetes components...
        ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
    🌟  Enabled addons: storage-provisioner, default-storageclass
    🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default


Having deleted the cluster the startuo time for a new cluster with prefilled caches reduces to well under a minute.


```python
!sleep 10
```

## Creating First Namespace And Pod


```bash
%%bash

cat <<EOF| kubectl apply -f -
kind: Namespace
apiVersion: v1
metadata:
  name: demo
  labels:
    name: demo
---
kind: Pod
apiVersion: v1
metadata:
  name: demo-pod
  namespace: demo
spec:
  containers:
  - name: demo-ctr
    image: nginx:stable-alpine
    resources:
      limits:
        memory: "200Mi"
        cpu: "700m"
      requests:
        memory: "200Mi"
        cpu: "700m"
EOF
```

    namespace/demo created
    pod/demo-pod created


A namespace demo with a pod demo-pod in it according to above yaml.


```bash
%%bash

cat <<EOF| kubectl apply -f -
kind: Namespace
apiVersion: v1
metadata:
  name: demo
  labels:
    name: demo
---
kind: Pod
apiVersion: v1
metadata:
  name: demo-pod
  namespace: demo
spec:
  containers:
  - name: demo-ctr
    image: nginx:stable-alpine
    resources:
      limits:
        memory: "200Mi"
        cpu: "700m"
      requests:
        memory: "200Mi"
        cpu: "700m"
EOF
```

    namespace/demo unchanged
    pod/demo-pod unchanged


As nemspace *demo* and the pod *demo-pod* in it have already been created by executing the exact same command before, *kubectl apply* remains idempotent.


```python
!kubectl get pods --namespace demo
```

    NAME       READY   STATUS              RESTARTS   AGE
    demo-pod   0/1     ContainerCreating   0          0s


The newly created and started pod *demo-pod* is just one pod among others constituting the base kubernetes cluster. Those containers are isolated in the *kube-system* namespace.


```python
!kubectl get namespaces
```

    NAME              STATUS   AGE
    default           Active   17s
    demo              Active   1s
    kube-node-lease   Active   20s
    kube-public       Active   20s
    kube-system       Active   20s



```python
!kubectl get pods --namespace kube-system
```

    NAME                               READY   STATUS              RESTARTS   AGE
    coredns-78fcd69978-wjgrf           0/1     ContainerCreating   0          2s
    etcd-minikube                      1/1     Running             0          13s
    kube-apiserver-minikube            1/1     Running             0          18s
    kube-controller-manager-minikube   1/1     Running             0          18s
    kube-proxy-kcbwc                   1/1     Running             0          2s
    kube-scheduler-minikube            1/1     Running             0          17s
    storage-provisioner                1/1     Running             0          12s



```bash
%%bash

echo "systemd-cgls --no-pager ; exit" | minikube ssh
```

    systemd-cgls --no-pager ; exit
    ]0;docker@minikube: ~docker@minikube:~$ systemd-cgls --no-pager ; exit
    Control group /docker/b656577b3185794fb56b6d931c9bec7b99afad6399467b2f88b0af1fbf2b158a:
    -.slice
    ├─init.scope 
    │ └─[0;38;5;245m1 /sbin/init[0m
    └─system.slice 
      ├─containerd.service 
      │ ├─[0;38;5;245m 200 /usr/bin/containerd[0m
      │ ├─[0;38;5;245m1602 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 9d95898cb83042c…[0m
      │ ├─[0;38;5;245m1603 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 69f972944518e3b…[0m
      │ ├─[0;38;5;245m1625 /usr/bin/containerd-shim-runc-v2 -namespace moby -id b2e90906de38417…[0m
      │ ├─[0;38;5;245m1663 /pause[0m
      │ ├─[0;38;5;245m1671 /pause[0m
      │ ├─[0;38;5;245m1681 /pause[0m
      │ ├─[0;38;5;245m1701 /usr/bin/containerd-shim-runc-v2 -namespace moby -id a5dd1bdf5a503a5…[0m
      │ ├─[0;38;5;245m1741 /pause[0m
      │ ├─[0;38;5;245m1786 /usr/bin/containerd-shim-runc-v2 -namespace moby -id b932b548a4ca4c4…[0m
      │ ├─[0;38;5;245m1812 /usr/bin/containerd-shim-runc-v2 -namespace moby -id aabddff2aca4184…[0m
      │ ├─[0;38;5;245m1831 /usr/bin/containerd-shim-runc-v2 -namespace moby -id e901992a1a8e5b6…[0m
      │ ├─[0;38;5;245m1874 /usr/bin/containerd-shim-runc-v2 -namespace moby -id af73ecaf6a156e8…[0m
      │ ├─[0;38;5;245m1885 etcd --advertise-client-urls=https://192.168.49.2:2379 --cert-file=/…[0m
      │ ├─[0;38;5;245m1888 kube-apiserver --advertise-address=192.168.49.2 --allow-privileged=t…[0m
      │ ├─[0;38;5;245m1930 kube-controller-manager --allocate-node-cidrs=true --authentication-…[0m
      │ ├─[0;38;5;245m1957 kube-scheduler --authentication-kubeconfig=/etc/kubernetes/scheduler…[0m
      │ ├─[0;38;5;245m2778 /usr/bin/containerd-shim-runc-v2 -namespace moby -id fe9e4ba52b62d5e…[0m
      │ ├─[0;38;5;245m2798 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 9bea84f546369a1…[0m
      │ ├─[0;38;5;245m2829 /pause[0m
      │ ├─[0;38;5;245m2830 /pause[0m
      │ ├─[0;38;5;245m2876 /usr/bin/containerd-shim-runc-v2 -namespace moby -id cccfdcac443a418…[0m
      │ ├─[0;38;5;245m2897 /pause[0m
      │ ├─[0;38;5;245m2912 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 3721ab803335713…[0m
      │ ├─[0;38;5;245m2931 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 381b126a8149820…[0m
      │ ├─[0;38;5;245m2964 /usr/local/bin/kube-proxy --config=/var/lib/kube-proxy/config.conf -…[0m
      │ ├─[0;38;5;245m2965 /storage-provisioner[0m
      │ ├─[0;38;5;245m3047 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 399d06382bf9f06…[0m
      │ ├─[0;38;5;245m3066 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 92dbb4e62babfb1…[0m
      │ ├─[0;38;5;245m3095 /pause[0m
      │ ├─[0;38;5;245m3097 /coredns -conf /etc/coredns/Corefile[0m
      │ ├─[0;38;5;245m3223 iptables-restore -w 5 -W 100000 --noflush --counters[0m
      │ └─[0;38;5;245m3246 n/a[0m
      ├─docker.service 
      │ └─[0;38;5;245m472 /usr/bin/dockerd -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock…[0m
      ├─kubelet.service 
      │ └─[0;38;5;245m2344 /var/lib/minikube/binaries/v1.22.1/kubelet --bootstrap-kubeconfig=/e…[0m
      ├─systemd-journald.service 
      │ └─[0;38;5;245m185 /lib/systemd/systemd-journald[0m
      ├─ssh.service 
      │ ├─[0;38;5;245m 210 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups[0m
      │ ├─[0;38;5;245m3229 sshd: docker [priv][0m
      │ ├─[0;38;5;245m3234 sshd: docker@pts/1[0m
      │ ├─[0;38;5;245m3242 -bash[0m
      │ └─[0;38;5;245m3247 systemd-cgls --no-pager[0m
      └─dbus.service 
        └─[0;38;5;245m197 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile…[0m
    logout
    [3J[H[2J


```python
!rm -rf alpine
```


```python
!skopeo --override-os linux copy docker://alpine:3.14.2 oci:alpine:3.14.2
```

    Getting image source signatures
    Copying blob a0d0a0d46f8b [======>---------------------------] 574.4KiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b [=============>----------------------] 1.1MiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b [=====================>--------------] 1.7MiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b [=============================>------] 2.2MiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b [==================================>-] 2.6MiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b [====================================] 2.7MiB / 2.7MiB
    [1A[JCopying blob a0d0a0d46f8b done  
    [1A[JCopying blob a0d0a0d46f8b done  
    Copying config 696d33ca15 [====================================] 585.0b / 585.0b
    [1A[JCopying config 696d33ca15 done  
    [1A[JCopying config 696d33ca15 done  
    [1A[JCopying config 696d33ca15 done  
    Writing manifest to image destination
    Storing signatures



```python
!tree alpine
```

    [01;34malpine[00m
    ├── [01;34mblobs[00m
    │   └── [01;34msha256[00m
    │       ├── 03014f0323753134bf6399ffbe26dcd75e89c6a7429adfab392d64706649f07b
    │       ├── 696d33ca1510966c426bdcc0daf05f75990d68c4eb820f615edccf7b971935e7
    │       └── a0d0a0d46f8b52473982a3c466318f479767577551a53ffc9074c9fa7035982e
    ├── index.json
    └── oci-layout
    
    2 directories, 5 files



```python
!file alpine/blobs/sha256/*
```

    alpine/blobs/sha256/03014f0323753134bf6399ffbe26dcd75e89c6a7429adfab392d64706649f07b: JSON data
    alpine/blobs/sha256/696d33ca1510966c426bdcc0daf05f75990d68c4eb820f615edccf7b971935e7: JSON data
    alpine/blobs/sha256/a0d0a0d46f8b52473982a3c466318f479767577551a53ffc9074c9fa7035982e: gzip compressed data, original size modulo 2^32 5865472



```python
!cat alpine/blobs/sha256/03014f0323753134bf6399ffbe26dcd75e89c6a7429adfab392d64706649f07b | jq
```

    [1;39m{
      [0m[34;1m"schemaVersion"[0m[1;39m: [0m[0;39m2[0m[1;39m,
      [0m[34;1m"config"[0m[1;39m: [0m[1;39m{
        [0m[34;1m"mediaType"[0m[1;39m: [0m[0;32m"application/vnd.oci.image.config.v1+json"[0m[1;39m,
        [0m[34;1m"digest"[0m[1;39m: [0m[0;32m"sha256:696d33ca1510966c426bdcc0daf05f75990d68c4eb820f615edccf7b971935e7"[0m[1;39m,
        [0m[34;1m"size"[0m[1;39m: [0m[0;39m585[0m[1;39m
      [1;39m}[0m[1;39m,
      [0m[34;1m"layers"[0m[1;39m: [0m[1;39m[
        [1;39m{
          [0m[34;1m"mediaType"[0m[1;39m: [0m[0;32m"application/vnd.oci.image.layer.v1.tar+gzip"[0m[1;39m,
          [0m[34;1m"digest"[0m[1;39m: [0m[0;32m"sha256:a0d0a0d46f8b52473982a3c466318f479767577551a53ffc9074c9fa7035982e"[0m[1;39m,
          [0m[34;1m"size"[0m[1;39m: [0m[0;39m2814446[0m[1;39m
        [1;39m}[0m[1;39m
      [1;39m][0m[1;39m
    [1;39m}[0m



```python
!cat alpine/blobs/sha256/696d33ca1510966c426bdcc0daf05f75990d68c4eb820f615edccf7b971935e7 | jq
```

    [1;39m{
      [0m[34;1m"created"[0m[1;39m: [0m[0;32m"2021-08-27T17:19:45.758611523Z"[0m[1;39m,
      [0m[34;1m"architecture"[0m[1;39m: [0m[0;32m"amd64"[0m[1;39m,
      [0m[34;1m"os"[0m[1;39m: [0m[0;32m"linux"[0m[1;39m,
      [0m[34;1m"config"[0m[1;39m: [0m[1;39m{
        [0m[34;1m"Env"[0m[1;39m: [0m[1;39m[
          [0;32m"PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"[0m[1;39m
        [1;39m][0m[1;39m,
        [0m[34;1m"Cmd"[0m[1;39m: [0m[1;39m[
          [0;32m"/bin/sh"[0m[1;39m
        [1;39m][0m[1;39m
      [1;39m}[0m[1;39m,
      [0m[34;1m"rootfs"[0m[1;39m: [0m[1;39m{
        [0m[34;1m"type"[0m[1;39m: [0m[0;32m"layers"[0m[1;39m,
        [0m[34;1m"diff_ids"[0m[1;39m: [0m[1;39m[
          [0;32m"sha256:e2eb06d8af8218cfec8210147357a68b7e13f7c485b991c288c2d01dc228bb68"[0m[1;39m
        [1;39m][0m[1;39m
      [1;39m}[0m[1;39m,
      [0m[34;1m"history"[0m[1;39m: [0m[1;39m[
        [1;39m{
          [0m[34;1m"created"[0m[1;39m: [0m[0;32m"2021-08-27T17:19:45.553092363Z"[0m[1;39m,
          [0m[34;1m"created_by"[0m[1;39m: [0m[0;32m"/bin/sh -c #(nop) ADD file:aad4290d27580cc1a094ffaf98c3ca2fc5d699fe695dfb8e6e9fac20f1129450 in / "[0m[1;39m
        [1;39m}[0m[1;39m,
        [1;39m{
          [0m[34;1m"created"[0m[1;39m: [0m[0;32m"2021-08-27T17:19:45.758611523Z"[0m[1;39m,
          [0m[34;1m"created_by"[0m[1;39m: [0m[0;32m"/bin/sh -c #(nop)  CMD [\"/bin/sh\"]"[0m[1;39m,
          [0m[34;1m"empty_layer"[0m[1;39m: [0m[0;39mtrue[0m[1;39m
        [1;39m}[0m[1;39m
      [1;39m][0m[1;39m
    [1;39m}[0m



```python
!rustup self uninstall -y
```

    [1minfo: [mremoving rustup home
    [1minfo: [mremoving cargo home
    [1minfo: [mremoving rustup binaries
    [1minfo: [mrustup is uninstalled



```python
!rm -rf helloworld
```


```python
!curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
```

    [1minfo:[0m downloading installer
    [1minfo: [mprofile set to 'default'
    [1minfo: [mdefault host triple is x86_64-apple-darwin
    [1minfo: [msyncing channel updates for 'stable-x86_64-apple-darwin'
    [1minfo: [mlatest update on 2021-09-09, rust version 1.55.0 (c8dfcfe04 2021-09-06)
    [1minfo: [mdownloading component 'cargo'
    [1minfo: [mdownloading component 'clippy'
    [1minfo: [mdownloading component 'rust-docs'
     17.1 MiB /  17.1 MiB (100 %)   6.4 MiB/s in  2s ETA:  0s
    [1minfo: [mdownloading component 'rust-std'
     21.0 MiB /  21.0 MiB (100 %)   6.2 MiB/s in  3s ETA:  0s
    [1minfo: [mdownloading component 'rustc'
     75.9 MiB /  75.9 MiB (100 %)   6.2 MiB/s in 12s ETA:  0s
    [1minfo: [mdownloading component 'rustfmt'
    [1minfo: [minstalling component 'cargo'
    [1minfo: [minstalling component 'clippy'
    [1minfo: [minstalling component 'rust-docs'
     17.1 MiB /  17.1 MiB (100 %)   4.6 MiB/s in  2s ETA:  0s
    [1minfo: [minstalling component 'rust-std'
     21.0 MiB /  21.0 MiB (100 %)   9.7 MiB/s in  2s ETA:  0s
    [1minfo: [minstalling component 'rustc'
     75.9 MiB /  75.9 MiB (100 %)   9.6 MiB/s in  7s ETA:  0s
    [1minfo: [minstalling component 'rustfmt'
    [1minfo: [mdefault toolchain set to 'stable-x86_64-apple-darwin'
    
      [1m[32mstable-x86_64-apple-darwin installed[m - rustc 1.55.0 (c8dfcfe04 2021-09-06)
    
    [1m
    Rust is installed now. Great!
    [m
    To get started you may need to restart your current shell.
    This would reload your [1mPATH[m environment variable to include
    Cargo's bin directory ($HOME/.cargo/bin).
    
    To configure your current shell, run:
    source $HOME/.cargo/env



```python
!rustup default stable
```

    [1minfo: [musing existing install for 'stable-x86_64-apple-darwin'
    [1minfo: [mdefault toolchain set to 'stable-x86_64-apple-darwin'
    
      [1mstable-x86_64-apple-darwin unchanged[m - rustc 1.55.0 (c8dfcfe04 2021-09-06)
    



```python
!rustup update
```

    [1minfo: [msyncing channel updates for 'stable-x86_64-apple-darwin'
    [1minfo: [mchecking for self-updates
    
      [1mstable-x86_64-apple-darwin unchanged[m - rustc 1.55.0 (c8dfcfe04 2021-09-06)
    
    [1minfo: [mcleaning up downloads & tmp directories



```python
!cargo new helloworld
```

    [0m[0m[1m[32m     Created[0m binary (application) `helloworld` package



```bash
%%bash

cd helloworld

cat >Dockerfile <<EOF
FROM docker.io/library/rust:1.55.0

WORKDIR /usr/src/helloworld

COPY . .

RUN cargo build --release

RUN cargo install --path .

CMD ["/usr/local/cargo/bin/helloworld"]
EOF
```


```bash
%%bash

cd helloworld

cat >Dockerfile.slim <<EOF
FROM docker.io/library/rust:1.55.0-alpine3.14

WORKDIR /usr/src/helloworld

COPY . .

RUN cargo build --release

RUN cargo install --path .

CMD ["/usr/local/cargo/bin/helloworld"]
EOF
```


```bash
%%bash

cd helloworld

cat >Dockerfile.slim-staged <<EOF
FROM docker.io/library/rust:1.55.0-alpine3.14

WORKDIR /usr/src/helloworld

COPY . .

RUN cargo build --release

RUN cargo install --path .

CMD ["/usr/local/cargo/bin/helloworld"]
EOF
```


```python
!podman info
```

    host:
      arch: amd64
      buildahVersion: 1.22.3
      cgroupControllers: []
      cgroupManager: systemd
      cgroupVersion: v2
      conmon:
        package: conmon-2.0.29-2.fc34.x86_64
        path: /usr/bin/conmon
        version: 'conmon version 2.0.29, commit: '
      cpus: 1
      distribution:
        distribution: fedora
        version: "34"
      eventLogger: journald
      hostname: localhost
      idMappings:
        gidmap:
        - container_id: 0
          host_id: 1000
          size: 1
        - container_id: 1
          host_id: 100000
          size: 65536
        uidmap:
        - container_id: 0
          host_id: 1000
          size: 1
        - container_id: 1
          host_id: 100000
          size: 65536
      kernel: 5.13.13-200.fc34.x86_64
      linkmode: dynamic
      memFree: 1698824192
      memTotal: 2061852672
      ociRuntime:
        name: crun
        package: crun-1.0-1.fc34.x86_64
        path: /usr/bin/crun
        version: |-
          crun version 1.0
          commit: 139dc6971e2f1d931af520188763e984d6cdfbf8
          spec: 1.0.0
          +SYSTEMD +SELINUX +APPARMOR +CAP +SECCOMP +EBPF +CRIU +YAJL
      os: linux
      remoteSocket:
        exists: true
        path: /run/user/1000/podman/podman.sock
      security:
        apparmorEnabled: false
        capabilities: CAP_CHOWN,CAP_DAC_OVERRIDE,CAP_FOWNER,CAP_FSETID,CAP_KILL,CAP_NET_BIND_SERVICE,CAP_SETFCAP,CAP_SETGID,CAP_SETPCAP,CAP_SETUID,CAP_SYS_CHROOT
        rootless: true
        seccompEnabled: true
        seccompProfilePath: /usr/share/containers/seccomp.json
        selinuxEnabled: true
      serviceIsRemote: true
      slirp4netns:
        executable: /usr/bin/slirp4netns
        package: slirp4netns-1.1.12-2.fc34.x86_64
        version: |-
          slirp4netns version 1.1.12
          commit: 7a104a101aa3278a2152351a082a6df71f57c9a3
          libslirp: 4.4.0
          SLIRP_CONFIG_VERSION_MAX: 3
          libseccomp: 2.5.0
      swapFree: 0
      swapTotal: 0
      uptime: 17h 6m 53.41s (Approximately 0.71 days)
    registries:
      search:
      - registry.fedoraproject.org
      - registry.access.redhat.com
      - docker.io
      - quay.io
    store:
      configFile: /var/home/core/.config/containers/storage.conf
      containerStore:
        number: 0
        paused: 0
        running: 0
        stopped: 0
      graphDriverName: overlay
      graphOptions: {}
      graphRoot: /var/home/core/.local/share/containers/storage
      graphStatus:
        Backing Filesystem: xfs
        Native Overlay Diff: "true"
        Supports d_type: "true"
        Using metacopy: "false"
      imageStore:
        number: 0
      runRoot: /run/user/1000/containers
      volumePath: /var/home/core/.local/share/containers/storage/volumes
    version:
      APIVersion: 3.3.1
      Built: 1630356396
      BuiltTime: Mon Aug 30 20:46:36 2021
      GitCommit: ""
      GoVersion: go1.16.6
      OsArch: linux/amd64
      Version: 3.3.1
    



```python
!cd helloworld ; podman build --tag helloworld:v0.1.0 --file Dockerfile .
```

    STEP 1/6: FROM docker.io/library/rust:1.55.0
    Trying to pull docker.io/library/rust:1.55.0...
    Getting image source signatures
    Copying blob sha256:74ca45178655a5c9b4a372bb131e0e6a563074c81321f9178fd06bc9847f6559
    Copying blob sha256:955615a668ce169f8a1443fc6b6e6215f43fe0babfb4790712a2d3171f34d366
    Copying blob sha256:2756ef5f69a5190f4308619e0f446d95f5515eef4a814dbad0bcebbbbc7b25a8
    Copying blob sha256:911ea9f2bd51e53a455297e0631e18a72a86d7e2c8e1807176e80f991bde5d64
    Copying blob sha256:27b0a22ee906271a6ce9ddd1754fdd7d3b59078e0b57b6cc054c7ed7ac301587
    Copying blob sha256:8584d51a9262f9a3a436dea09ba40fa50f85802018f9bd299eee1bf538481077
    Copying blob sha256:2756ef5f69a5190f4308619e0f446d95f5515eef4a814dbad0bcebbbbc7b25a8
    Copying blob sha256:74ca45178655a5c9b4a372bb131e0e6a563074c81321f9178fd06bc9847f6559
    Copying blob sha256:955615a668ce169f8a1443fc6b6e6215f43fe0babfb4790712a2d3171f34d366
    Copying blob sha256:911ea9f2bd51e53a455297e0631e18a72a86d7e2c8e1807176e80f991bde5d64
    Copying blob sha256:27b0a22ee906271a6ce9ddd1754fdd7d3b59078e0b57b6cc054c7ed7ac301587
    Copying blob sha256:8584d51a9262f9a3a436dea09ba40fa50f85802018f9bd299eee1bf538481077
    Copying config sha256:378164a392dd65d97fda64be77d39c767f3e6579f7347d311467b40a3e246a10
    Writing manifest to image destination
    Storing signatures
    STEP 2/6: WORKDIR /usr/src/helloworld
    --> 4ad35b40853
    STEP 3/6: COPY . .
    --> 83e80b75e92
    STEP 4/6: RUN cargo build --release
       Compiling helloworld v0.1.0 (/usr/src/helloworld)
        Finished release [optimized] target(s) in 1.00s
    --> f5d122d3a3c
    STEP 5/6: RUN cargo install --path .
      Installing helloworld v0.1.0 (/usr/src/helloworld)
       Compiling helloworld v0.1.0 (/usr/src/helloworld)
        Finished release [optimized] target(s) in 0.78s
      Installing /usr/local/cargo/bin/helloworld
       Installed package `helloworld v0.1.0 (/usr/src/helloworld)` (executable `helloworld`)
    --> 3ecdbe7032b
    STEP 6/6: CMD ["/usr/local/cargo/bin/helloworld"]
    COMMIT helloworld:v0.1.0
    --> 1207419edd4
    Successfully tagged localhost/helloworld:v0.1.0
    1207419edd4b05d410812632c587f6351b141ebff118c029065f21af6f134b7e



```python
!podman images
```

    REPOSITORY              TAG         IMAGE ID      CREATED       SIZE
    localhost/helloworld    v0.1.0      1207419edd4b  12 hours ago  1.28 GB
    docker.io/library/rust  1.55.0      378164a392dd  2 days ago    1.27 GB



```python
!podman run --name helloworld --rm helloworld:v0.1.0
```

    Hello, world!



```python
!cd helloworld ; podman build --tag helloworld:v0.2.0 --file Dockerfile.slim .
```

    STEP 1/6: FROM docker.io/library/rust:1.55.0-alpine3.14
    Trying to pull docker.io/library/rust:1.55.0-alpine3.14...
    Getting image source signatures
    Copying blob sha256:922454686f1ed186a1f1ecf76b947b3b16125d09227ba5d5736ce77c72941ce0
    Copying blob sha256:a0d0a0d46f8b52473982a3c466318f479767577551a53ffc9074c9fa7035982e
    Copying blob sha256:d4ea2bb3df1724da0bb9bbf8d43f7a5b7192610627c590c2fd4b8e0770230cbf
    Copying blob sha256:d4ea2bb3df1724da0bb9bbf8d43f7a5b7192610627c590c2fd4b8e0770230cbf
    Copying blob sha256:a0d0a0d46f8b52473982a3c466318f479767577551a53ffc9074c9fa7035982e
    Copying blob sha256:922454686f1ed186a1f1ecf76b947b3b16125d09227ba5d5736ce77c72941ce0
    Copying config sha256:ac41586fb44e3aa14cee23647a0d7257d86f4a549634453ab95497bd24eff193
    Writing manifest to image destination
    Storing signatures
    STEP 2/6: WORKDIR /usr/src/helloworld
    --> 480f2a6ea05
    STEP 3/6: COPY . .
    --> 1860244e360
    STEP 4/6: RUN cargo build --release
       Compiling helloworld v0.1.0 (/usr/src/helloworld)
        Finished release [optimized] target(s) in 1.11s
    --> 0ee3a153b7b
    STEP 5/6: RUN cargo install --path .
      Installing helloworld v0.1.0 (/usr/src/helloworld)
       Compiling helloworld v0.1.0 (/usr/src/helloworld)
        Finished release [optimized] target(s) in 0.53s
      Installing /usr/local/cargo/bin/helloworld
       Installed package `helloworld v0.1.0 (/usr/src/helloworld)` (executable `helloworld`)
    --> 941a12397d6
    STEP 6/6: CMD ["/usr/local/cargo/bin/helloworld"]
    COMMIT helloworld:v0.2.0
    --> 62355461603
    Successfully tagged localhost/helloworld:v0.2.0
    62355461603acf01ed62df7828f3b59076290f5703795d74f49bef57a1744f52



```python
!cd helloworld ; podman build --tag helloworld:v0.3.0 --file Dockerfile.slim-staged .
```

    STEP 1/6: FROM docker.io/library/rust:1.55.0-alpine3.14
    STEP 2/6: WORKDIR /usr/src/helloworld
    --> Using cache 480f2a6ea0555ca38f34d6a2949447caf1dd0adf62e6d681dce715ed793ea85f
    --> 480f2a6ea05
    STEP 3/6: COPY . .
    --> Using cache 1860244e3609276ed56e2775f4717c23581b6b075774fb96d5c4494302ec2c8d
    --> 1860244e360
    STEP 4/6: RUN cargo build --release
    --> Using cache 0ee3a153b7bfd68cde9043ed801a7fb16503c1866bb7a62407d0adba99ee7545
    --> 0ee3a153b7b
    STEP 5/6: RUN cargo install --path .
    --> Using cache 941a12397d6c41507025230baf7aaaa233c99c84e6aaece58f88def0040be06b
    --> 941a12397d6
    STEP 6/6: CMD ["/usr/local/cargo/bin/helloworld"]
    --> Using cache 62355461603acf01ed62df7828f3b59076290f5703795d74f49bef57a1744f52
    COMMIT helloworld:v0.3.0
    --> 62355461603
    Successfully tagged localhost/helloworld:v0.3.0
    Successfully tagged localhost/helloworld:v0.2.0
    62355461603acf01ed62df7828f3b59076290f5703795d74f49bef57a1744f52



```python
!podman images
```

    REPOSITORY              TAG                IMAGE ID      CREATED       SIZE
    localhost/helloworld    v0.3.0             62355461603a  12 hours ago  880 MB
    localhost/helloworld    v0.2.0             62355461603a  12 hours ago  880 MB
    localhost/helloworld    v0.1.0             1207419edd4b  12 hours ago  1.28 GB
    docker.io/library/rust  1.55.0-alpine3.14  ac41586fb44e  2 days ago    868 MB
    docker.io/library/rust  1.55.0             378164a392dd  2 days ago    1.27 GB



```python
!podman run --name helloworld --rm helloworld:v0.3.0
```

    Hello, world!

