# kubernetes basic concept
- <a href="#introduction">介紹</a>
- <a href="#components">Components</a>
  - <a href="#control-plane-components">Control Plane Components</a>
    - <a href="#kube-apiserver">kube-apiserver</a>
    - <a href="#etcd">etcd</a>
    - <a href="#kube-scheduler">kube-scheduler</a>
    - <a href="#kube-controller-manager">kube-controller-manager</a>
    - <a href="#cloud-controller-manager">cloud-controller-manager</a>
  - <a href="#node-components">Node Components</a> 
    - <a href="#kubelet">kubelet</a>
    - <a href="#kube-proxy">kube-proxy</a>
    - <a href="#container-runtime">Container runtime</a>
- <a href="#workloads">Workloads</a>
  - <a href="#pod">Pod</a>
  - <a href="#workload-resources">Workload Resources</a>
  
-------------

### <div id="introduction">介紹</div>

- Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.
    - 同時部署多個容器到多台機器上（Deployment）
    - 服務的乘載量有變化時，可以對容器做自動擴展（Scaling）
    - 管理多個容器的狀態，自動偵測並重啟故障的容器（Management）

-------

### <div id="components">Components</div>

#### <div id="control-plane-components">1. Control Plane Components</div>

> Control Plane Components 負責對cluster做出全局決策（例如: 調度），以及偵測和回應cluster事件。

- <div id="kube-apiserver"><a href="https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/">kube-apiserver</a></div>

    > The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane. kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. You can run several instances of kube-apiserver and balance traffic between those instances.
  - 管理整個 Kubernetes 所需 API 的接口，例如從 Command Line 下 kubectl 指令就會把指令送到這裏
  - 負責 Node 之間的溝通橋樑，每個 Node 彼此不能直接溝通，必須要透過 apiserver 轉介
  - 負責 Kubernetes 中的請求的身份認證與授權
  
<br>

- <div id="etcd">etcd</div>

    > Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.
  - 用來存放 Kubernetes Cluster 的資料作為備份，當某些原因而故障時，可以透過 etcd 還原 Kubernetes 的狀態

<br>

- <div id="kube-scheduler"><a href="https://kubernetes.io/docs/reference/command-line-tools-reference/kube-scheduler/">kube-scheduler</a></div>

    > Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.
  - Kubernetes 的 Pods 調度員，scheduler 會監視新建立但還沒有被指定要跑在哪個 Node 上的 Pod，並根據每個 Node 上面資源規定、硬體限制等條件去協調出一個最適合放置的 Node 讓該 Pod 啟動
  
<br>

- <div id="kube-controller-manager"><a href="https://kubernetes.io/docs/reference/command-line-tools-reference/kube-controller-manager/">kube-controller-manager</a></div>

  > The Kubernetes controller manager is a daemon that embeds the core control loops shipped with Kubernetes. In applications of robotics and automation, a control loop is a non-terminating loop that regulates the state of the system. In Kubernetes, a controller is a control loop that watches the shared state of the cluster through the apiserver and makes changes attempting to move the current state towards the desired state. Examples of controllers that ship with Kubernetes today are the replication controller, endpoints controller, namespace controller, and serviceaccounts controller.

  > Kubernetes controller manager 是由多個 controller 集合而成，不中斷的透過 kube-apiserver 監控cluster的各個狀態，自動化的達到理想的狀態。

  - <a href="https://kubernetes.io/docs/concepts/architecture/nodes/#node-controller"> Node controller: Responsible for noticing and responding when nodes go down. </a>
  - Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
  - Endpoints controller: Populates the Endpoints object (that is, joins Services & Pods).
  - Service Account & Token controllers: Create default accounts and API access tokens for new namespaces.
  
<br>

- <div id="cloud-controller-manager"><a href="https://kubernetes.io/docs/concepts/architecture/cloud-controller/">cloud-controller-manager</a></div>

  > The cloud-controller-manager is a Kubernetes control plane component that embeds cloud-specific control logic. The cloud controller manager lets you link your cluster into your cloud provider's API, and separates out the components that interact with that cloud platform from components that only interact with your cluster.


#### <div id="node-components">2. Node Components</div>

    > Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

    > 一個 Worker Node（簡稱 Node）對應到一台機器，可以是實體機、虛擬機如 AWS 上的一台 EC2 或 GCP 上的一台 Computer Engine。每個 Node 中都有三個組件：kubelet、kube-proxy、Container Runtime。

<br>

- <div id="kubelet">kubelet</div>

    > An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod. 
      The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. 
      The kubelet doesn't manage containers which were not created by Kubernetes.

    > Node 的管理員，負責管理該 Node 上的所有 Pods 的狀態並負責與 Control Plane (舊名:Master node) 溝通

<br>

- <div id="kube-proxy">kube-proxy</div>

    > kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept.
      kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.
      kube-proxy uses the operating system packet filtering layer if there is one and it's available. Otherwise, kube-proxy forwards the traffic itself.

    > 處理每個節點上的虛擬網路。 Proxy 會路由網路流量，以及管理服務和 Pod 的 IP 定址。

<br>

- <div id="container-runtime">Container Runtime</div>
 
    > The container runtime is the software that is responsible for running containers.
      Kubernetes supports several container runtimes: Docker, containerd, CRI-O, and any implementation of the Kubernetes CRI (Container Runtime Interface).

    > 該 Node 真正負責容器執行的程式，以 Docker 容器為例其對應的 Container Runtime 就是 Docker Engine

<br>

-------

### <div id="workloads"><a href="https://kubernetes.io/docs/concepts/workloads">Workloads</a></div>

> A workload is an application running on Kubernetes. Whether your workload is a single component or several that work together, on Kubernetes you run it inside a set of pods. In Kubernetes, a Pod represents a set of running containers on your cluster.
  Kubernetes pods have a defined lifecycle. For example, once a pod is running in your cluster then a critical fault on the node where that pod is running means that all the pods on that node fail. Kubernetes treats that level of failure as final: you would need to create a new Pod to recover, even if the node later becomes healthy.
  However, to make life considerably easier, you don't need to manage each Pod directly. Instead, you can use workload resources that manage a set of pods on your behalf. These resources configure controllers that make sure the right number of the right kind of pod are running, to match the state you specified.

> 在一組 Pod 中運行 workload，用來「管理或是運行 Container」 在 Cluster 上。

<br>

- <a href="https://kubernetes.io/docs/concepts/workloads/pods/"><div id="pod">Pod</div></a>


<br>

- <div id="workload-resources">Kubernetes provides several built-in workload resources:</div>

    > <a href="https://www.baeldung.com/ops/kubernetes-deployment-vs-statefulsets"> before you get started, you should know concepts of stateless and stateful.</a>
    
    > stateless applications don’t “store” data. On the other hand, stateful applications require backing storage
    
    - Deployment 
        - Deployment 為 Pod 和 Replica Set（舊名: Replication Controller）提供聲明式更新。
        - 根據 Deployment 的設定，確保該 Pod 有一定的數量運行在 node 上
    - StatefulSet 
        - 透過 PVC (Persistent Volume Claim) 提供穩定的 Storage Identity
        - Headless Service 提供穩定的 Network Identity
    - DaemonSet
    - Job and CronJob 


-------

![title](images/1-1.jpg)
![title](images/1-2.jpg)

-------

- lab: https://www.katacoda.com/courses/kubernetes
- reference: 
    - https://cwhu.medium.com/kubernetes-basic-concept-tutorial-e033e3504ec0
    - https://kubernetes.io/docs/concepts/overview/components/
    - https://www.baeldung.com/ops/kubernetes-deployment-vs-statefulsets
    - https://jimmysong.io/kubernetes-handbook/concepts/deployment.html

-------









