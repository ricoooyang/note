# kubernetes basic concept
- <a href="#introduction">介紹</a>
- <a href="#components">Components</a>
  - <a href="#control-plane-components">Control Plane Components</a>
    - <a href="#kube-apiserver">kube-apiserver</a>
    - <a href="#etcd">etcd</a>
    - <a href="#kube-scheduler">kube-scheduler</a>
    - <a href="#kube-controller-manager">kube-controller-manager</a>
  - <a href="#node-components">Node Components</a> 
    - <a href="#kubelet">kubelet</a>
    - <a href="#kube-proxy">kube-proxy</a>
- <a href="#components">Workloads</a>
  - <a href="#pods">Pods</a>
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

- <div id="kube-apiserver">kube-apiserver</div>

    > The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane. kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. You can run several instances of kube-apiserver and balance traffic between those instances.
  - 管理整個 Kubernetes 所需 API 的接口，例如從 Command Line 下 kubectl 指令就會把指令送到這裏
  - 負責 Node 之間的溝通橋樑，每個 Node 彼此不能直接溝通，必須要透過 apiserver 轉介
  - 負責 Kubernetes 中的請求的身份認證與授權


- <div id="etcd">etcd</div>

    > Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.
  - 用來存放 Kubernetes Cluster 的資料作為備份，當某些原因而故障時，可以透過 etcd 還原 Kubernetes 的狀態


- <div id="kube-scheduler">kube-scheduler</div>

    > Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.
  - Kubernetes 的 Pods 調度員，scheduler 會監視新建立但還沒有被指定要跑在哪個 Node 上的 Pod，並根據每個 Node 上面資源規定、硬體限制等條件去協調出一個最適合放置的 Node 讓該 Pod 啟動
  
  
- <div id="kube-controller-manager">kube-controller-manager</div>

  >  Controller Manager 則是 Kubernetes 中所有 Controllers 的核心管理者。Controller Manager 會定期去訪問 API Server，若有接收到變更的指令 Controller Manager 則會去更改這些 Controllers 的狀態。
  
  - <a href="https://kubernetes.io/docs/concepts/architecture/nodes/#node-controller"> Node controller: Responsible for noticing and responding when nodes go down. </a>
  - Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
  - Endpoints controller: Populates the Endpoints object (that is, joins Services & Pods).
  - Service Account & Token controllers: Create default accounts and API access tokens for new namespaces.

-------

![title](images/1-1.jpg)
![title](images/1-2.jpg)

-------

- lab: https://www.katacoda.com/courses/kubernetes
- reference: 
    - https://cwhu.medium.com/kubernetes-basic-concept-tutorial-e033e3504ec0
    - https://kubernetes.io/docs/concepts/overview/components/

-------









