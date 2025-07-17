# Day-31

## 🏗️ **Kubernetes Architecture: 

Kubernetes (K8s) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It follows a **master-worker architecture** (now called **control plane and nodes**) and consists of several components that communicate with each other via REST APIs and gRPC.

### 1. **Control Plane (Master Node)**

Manages the cluster, makes decisions, and maintains the cluster state.

* API Server (`kube-apiserver`)
* Scheduler (`kube-scheduler`)
* Controller Manager (`kube-controller-manager`)
* Cloud Controller Manager (`cloud-controller-manager`)
* etcd (key-value store)

### 2. **Node (Worker Nodes)**

Runs the actual application workloads in Pods.

* Kubelet
* Kube Proxy
* Container Runtime (e.g., containerd, Docker)
* Pods (with application containers)

---

## 🧠 CONTROL PLANE COMPONENTS (Master)

### 1. **kube-apiserver** 🧩

* **Role:** The front-end of the Kubernetes control plane.
* **Responsibilities:**

  * Exposes Kubernetes API (RESTful interface).
  * Validates and processes requests.
  * Authenticates and authorizes users.
  * Communicates with etcd, controllers, and nodes.
* **Communication:**

  * All components (UI, CLI `kubectl`, nodes) talk to the API Server.
  * `kubectl get pods` → API Server → etcd → returns response.

---

### 2. **etcd** 🗃️

* **Role:** A distributed **key-value** store.
* **Responsibilities:**

  * Stores the **entire cluster state** (configuration, nodes, pods, secrets).
  * Used for leader election and consensus.
* **Communication:**

  * API Server reads/writes cluster data from/to etcd.
  * Highly consistent and durable.

---

### 3. **kube-scheduler** 📅

* **Role:** Assigns pods to nodes.
* **Responsibilities:**

  * Watches for **unscheduled pods**.
  * Picks a node based on:

    * Node availability
    * Resource usage (CPU, memory)
    * Affinity rules
    * Taints and tolerations
* **Communication:**

  * Talks to the API Server to fetch unassigned pods and updates scheduling info.

---

### 4. **kube-controller-manager** 🎮

* **Role:** Runs **controller loops** that monitor cluster state and fix deviations.
* **Controllers inside it:**

  * **Node Controller:** Detects failed nodes.
  * **Replication Controller:** Ensures the right number of pod replicas.
  * **Deployment Controller:** Manages deployments.
  * **Namespace Controller:** Manages namespaces.
* **Communication:**

  * Talks to the API Server to get current state and issue corrections.

---

### 5. **cloud-controller-manager** ☁️ (optional)

* **Role:** Manages cloud-specific control logic.
* **Responsibilities:**

  * Manages cloud provider APIs (e.g., AWS, GCP).
  * Handles:

    * Node provisioning
    * Load balancers
    * Storage volumes
* **Communication:**

  * Talks to the cloud provider APIs and the API server.

---

## 🧱 NODE COMPONENTS (Workers)

Each worker node runs several components to execute workloads (containers).

### 1. **kubelet** 🧭

* **Role:** The agent running on each node.
* **Responsibilities:**

  * Registers node with the API server.
  * Ensures containers described in PodSpecs are running and healthy.
  * Syncs pod specs from the API server.
* **Communication:**

  * Talks to the API server (watches PodSpec).
  * Communicates with container runtime to manage containers.

---

### 2. **kube-proxy** 🔀

* **Role:** Manages network rules.
* **Responsibilities:**

  * Provides network communication to Pods inside and outside the cluster.
  * Uses IPTables/IPVS to forward traffic.
  * Enables **Service Discovery** and **Load Balancing**.
* **Communication:**

  * Works on each node to handle service traffic (based on API Server updates).

---

### 3. **Container Runtime** 🐳

* **Role:** Runs and manages containers.
* **Examples:** `containerd`, `CRI-O`, `Docker` (deprecated from v1.20+)
* **Responsibilities:**

  * Pulls container images.
  * Starts/stops containers.
  * Reports status to kubelet.
* **Communication:**

  * kubelet uses **Container Runtime Interface (CRI)** to communicate.

---

### 4. **Pods and Containers** 📦

* **Pods**: Smallest deployable unit. Encapsulates one or more containers.
* **Containers**: Run application logic.

---

## 🔗 HOW COMPONENTS COMMUNICATE

### Summary Table:

| Component          | Communicates With      | Protocol/Method           |
| ------------------ | ---------------------- | ------------------------- |
| `kubectl` (client) | API Server             | HTTPS (REST)              |
| API Server         | etcd                   | gRPC                      |
| Controller Manager | API Server             | HTTPS (REST)              |
| Scheduler          | API Server             | HTTPS (REST)              |
| Kubelet            | API Server, Runtime    | HTTPS, CRI                |
| Kube Proxy         | API Server             | Watches Service/Endpoints |
| Cloud Controller   | API Server, Cloud APIs | HTTPS, Provider SDKs      |
| Nodes              | API Server             | Register/Heartbeat        |

---

## 📈 Communication Flow Example

Say you deploy a pod:

1. `kubectl apply -f pod.yaml`
2. `kubectl` sends request to `kube-apiserver`.
3. `kube-apiserver` stores config in `etcd`.
4. `scheduler` sees unscheduled pod, assigns a node.
5. `controller-manager` updates deployment/controller status.
6. `kubelet` on assigned node pulls image and starts pod.
7. `kube-proxy` updates networking rules.

---

## 🔐 Security and Authentication

* **Authentication**: Certificates, tokens, OIDC
* **Authorization**: RBAC (Role-Based Access Control)
* **Admission Controllers**: Validate or mutate requests before persistence

---
![Kubernetes Architecture](https://phoenixnap.com/kb/wp-content/uploads/2021/04/full-kubernetes-model-architecture.png)

