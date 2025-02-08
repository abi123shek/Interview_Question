# Kubernetes
## ✅ What are the different components of Kubernetes?
Kubernetes Components 
1. Control Plane (Manages the cluster)
API Server (kube-apiserver) – Handles API requests, authentication, and communication.
Controller Manager (kube-controller-manager) – Runs controllers to maintain cluster state (node, pod, service, etc.).
Scheduler (kube-scheduler) – Assigns workloads (pods) to nodes based on resource availability.
etcd – Distributed key-value store for cluster data storage.
2. Worker Node Components (Run workloads)
Kubelet – Ensures pods run on the node and reports to the control plane.
Kube Proxy – Manages network communication between pods and external traffic.
Container Runtime (Docker, containerd, CRI-O, etc.) – Runs containerized applications.
3. Add-ons (Enhance functionality)
CoreDNS – Handles internal DNS for service discovery.
Ingress Controller – Manages external access via HTTP/HTTPS routes.
Metrics Server – Collects resource usage data for autoscaling.

## ✅ What are Persistent Volumes (PV) and Persistent Volume Claims (PVC)?
✅ What is the difference between StatefulSet and Deployment?
✅ Tell me about different services in Kubernetes.
✅ What is the difference between ClusterIP and NodePort?
✅ How can you achieve auto-scaling in Kubernetes?
✅ What is a Namespace in Kubernetes?
✅ What is a DaemonSet?
✅ What is an Ingress in Kubernetes?
✅ What is ConfigMap in Kubernetes?
✅ What is a Secret in Kubernetes?
✅ How do you securely store credentials in Kubernetes?
✅ What is a Horizontal Pod Autoscaler (HPA) and what metrics does it use?
✅ How does Vertical Pod Autoscaler (VPA) work?
✅ What is the difference between HPA and VPA?
✅ What is Role-Based Access Control (RBAC) in Kubernetes?
✅ How do you debug a failing Pod?
✅ What is a Custom Resource Definition (CRD)?
✅ What are Helm charts, and how do they simplify Kubernetes deployments?
✅ What are the main components of Helm?
✅ What is a Helm Chart, and what does it contain?
✅ What is a Chart.yaml file, and what is its purpose?
✅ What is a values.yaml file, and how does it work?
