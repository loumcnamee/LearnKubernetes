# LearnKubernetes
A collection of notes and scripts to learn Kubernetes

# Kubernetes Training notes
---

For this training I am using kubectl install in a Ubuntu WSL instance on Windows 11

Note The followng LinkeIn courses are recommended 
  * GitOps foundations
  * Docker


## kubectl installation

Ref: https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download

1. download kubectrl binaries

    `$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`

2. install kubectl

    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

## Run minikube

1. To verify minkube is correctly installed

    minikube

1. To start minikube run

    minikube start

1. Display the kubectl version

    kubectl version --client

1. To retrieve infomation about minkube clusters

    kubectl cluster-info

1. List deployed nodes

    kubectl get nodes

1. List the k8s namespaces

    kubectl get namespaces

1. List the pods in all nemespaces

    kubectl get pods -A

1. List the services in the cluster

    kubectl get services -A
fitzroyharboursoccerclub@gmail.com

## Load a pod

1. Deploy the pods  `kubectl apply -f deployment.yaml`

> deployment.apps/pod-info-deployment configured

1. Verify the deployment by listing the pods `kubectl get pods -n example-namespace`

> NAME                                   READY   STATUS    RESTARTS   AGE
> pod-info-deployment-5b84b47d9b-t5tmm   1/1     Running   0          16m

`kubectl apply -f deployment.yaml`

`kubectl get pods -n example-namespace`

> NAME                                   READY   STATUS    RESTARTS   AGE

> pod-info-deployment-5b84b47d9b-2lwqx   1/1     Running   0          4s

> pod-info-deployment-5b84b47d9b-n7t8m   1/1     Running   0          4s

> pod-info-deployment-5b84b47d9b-t5tmm   1/1     Running   0          18m`

$ kubectl get pods -n example-namespace
NAME                                   READY   STATUS    RESTARTS   AGE
pod-info-deployment-5b84b47d9b-hdchb   1/1     Running   0          31s
pod-info-deployment-5b84b47d9b-n7t8m   1/1     Running   0          119s
pod-info-deployment-5b84b47d9b-t5tmm   1/1     Running   0          20m

$ docker images

$ kubectl get pods -n example-namespace
NAME                                   READY   STATUS    RESTARTS   AGE
pod-info-deployment-5b84b47d9b-hdchb   1/1     Running   0          101m
pod-info-deployment-5b84b47d9b-n7t8m   1/1     Running   0          103m
pod-info-deployment-5b84b47d9b-t5tmm   1/1     Running   0          121m
loumcnamee@kodo8:~/k8sTrg$ kubectl describe pod pod-info-deployment-5b84b47d9b-hdchb
Error from server (NotFound): pods "pod-info-deployment-5b84b47d9b-hdchb" not found
loumcnamee@kodo8:~/k8sTrg$ kubectl describe pod pod-info-deployment-5b84b47d9b-hdchb -n example-namespace
Name:             pod-info-deployment-5b84b47d9b-hdchb
Namespace:        example-namespace
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Mon, 06 Apr 2026 12:29:16 -0400
Labels:           app=pod-info
                  pod-template-hash=5b84b47d9b
Annotations:      <none>
Status:           Running
IP:               10.244.0.7
IPs:
  IP:           10.244.0.7
Controlled By:  ReplicaSet/pod-info-deployment-5b84b47d9b
Containers:
  pod-info-container:
    Container ID:   docker://a2c2d369acaffb3f8fb77ccf51e83d615699a79107c78593e520843d313e14c3
    Image:          kimschles/pod-info-app:latest
    Image ID:       docker-pullable://kimschles/pod-info-app@sha256:fa4f33bc2301bb242bdd078ac206d0e379dfed2e225d46a6952ff444ae6f4a7a
    Port:           3000/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Mon, 06 Apr 2026 12:29:17 -0400
    Ready:          True
    Restart Count:  0
    Environment:
      POD_NAME:       pod-info-deployment-5b84b47d9b-hdchb (v1:metadata.name)
      POD_NAMESPACE:  example-namespace (v1:metadata.namespace)
      POD_IP:          (v1:status.podIP)
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-dj2hk (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-dj2hk:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    Optional:                false
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  102m  default-scheduler  Successfully assigned example-namespace/pod-info-deployment-5b84b47d9b-hdchb to minikube
  Normal  Pulling    102m  kubelet            Pulling image "kimschles/pod-info-app:latest"
  Normal  Pulled     102m  kubelet            Successfully pulled image "kimschles/pod-info-app:latest" in 502ms (502ms including waiting). Image size: 213980203 bytes.
  Normal  Created    102m  kubelet            Created container: pod-info-container
  Normal  Started    102m  kubelet            Started container pod-info-container
loumcnamee@kodo8:~/k8sTrg$ histry


### Side Note

The course uses a docker image provided by the instructor. 

1. call `docker images` to list images contained in the local docker instance

1. call `docker pull kimschles/pod-info-app:latest` to download the image into the local docker image

1. call `docker inspect hello-world:latest` to display details about the docker image. In this example the image is hello-world:latest






groups user
groups $USER
docker ps



top
exit
lsb_release -a
sudo apt update
sudo apt-get install ca-certificates curl gnupg lsb-release
uname - a
uname -a
lsb_release -a
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl status docker
sudo docker run hello-world
docker
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube
docker
minkube start
minikube start
sudo minikube start
minikube start
stsremctl status docker
systemctl status docker
docker ps
sudo groupadd docker
sudo usermod -aG docker $USER
docker ps
sudo systemctl start docker
docker ps
minikube start --driver=docker
sudo usermod -aG docker $USER
newgrp docker
exit
pwd
