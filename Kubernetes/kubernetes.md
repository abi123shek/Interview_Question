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
Persistent Volumes (PV) & Persistent Volume Claims (PVC) 
Persistent Volume (PV): A storage resource provisioned in Kubernetes (e.g., NFS, cloud storage). It exists independently of pods.
Persistent Volume Claim (PVC): A request by a pod for storage. It binds to an available PV based on size, access mode, and storage class.
🔹 PV = Actual storage
🔹 PVC = Request for storage

## ✅ What is the difference between StatefulSet and Deployment?
A StatefulSet is used for managing stateful applications that require stable network identities, persistent storage, and ordered deployment. Each pod in a StatefulSet has a unique, stable name (e.g., my-app-0, my-app-1), ensuring that storage (PVCs) remains attached to the same pod even if it restarts. Pods are scaled sequentially, and they retain their identity across rescheduling. This makes StatefulSets ideal for databases like MySQL, PostgreSQL, and distributed systems like Kafka or Zookeeper.

A Deployment, on the other hand, is used for stateless applications, where all pods are identical and interchangeable. It manages rolling updates, scaling, and self-healing efficiently by treating all pods as equal, allowing them to be created or destroyed dynamically. Deployments scale in parallel and do not maintain sticky identities or persistent storage. They are best suited for web applications, APIs, and microservices that do not rely on per-instance persistence.

In summary, use Deployments for stateless workloads where any pod can serve requests, and use StatefulSets for stateful applications that require persistent identity, ordered scaling, and stable storage.

## ✅ Tell me about different services in Kubernetes.
ubernetes provides four types of services to manage network communication between pods and external users. ClusterIP (default) allows internal communication within the cluster. NodePort exposes the service on a static port across all nodes, enabling external access via <NodeIP>:<NodePort>. LoadBalancer provisions an external load balancer (mainly in cloud environments) to distribute traffic across pods. ExternalName maps a service to an external DNS name, allowing Kubernetes to route traffic to external resources. Each service type is designed for different use cases, ensuring efficient networking within and outside the cluster.

## ✅ What is the difference between ClusterIP and NodePort?
ClusterIP is the default Kubernetes service type that allows communication only within the cluster. It assigns an internal IP, making the service accessible only to other pods. It is used for internal microservices and databases.

NodePort, on the other hand, exposes the service on a static port (30000-32767) on each node’s IP, making it accessible externally via <NodeIP>:<NodePort>. It is useful for debugging or when external access is needed without a load balancer.
In short, ClusterIP is for internal traffic, while NodePort allows external access via the node’s IP and a designated port.

## ✅ How can you achieve auto-scaling in Kubernetes?
Auto-scaling in Kubernetes can be achieved using three main mechanisms. Horizontal Pod Autoscaler (HPA) scales pods in or out based on CPU, memory, or custom metrics, ensuring efficient resource utilization. Vertical Pod Autoscaler (VPA) adjusts a pod’s CPU and memory up or down dynamically to match workload demands. Cluster Autoscaler (CA) scales the number of worker nodes up or down based on pending pod requirements, ensuring sufficient infrastructure capacity. Together, these autoscaling methods help optimize performance, resource efficiency, and cost management in Kubernetes

## ✅ What is a Namespace in Kubernetes?
A Namespace in Kubernetes is a way to divide resources within a cluster into logical groups. It allows for better organization, isolation, and resource management for different environments or teams. For example, you can have separate namespaces for development, staging, and production, each with its own set of resources. Namespaces help manage resource quotas, access control, and avoid naming conflicts between different environments or teams within the same cluster. 
## ✅ What is a DaemonSet?
A DaemonSet in Kubernetes ensures that a specific pod runs on every node (or a subset of nodes) in the cluster. It is typically used for running system-level or cluster-wide services, such as log collectors, monitoring agents, or network proxies. As nodes are added to the cluster, the DaemonSet automatically schedules the pod on them, and as nodes are removed, the pods are deleted. This ensures that the specified service is always available on all nodes in the cluster.

## ✅ What is an Ingress in Kubernetes?
An Ingress in Kubernetes is an API object that manages external access to services within a cluster, typically over HTTP or HTTPS. It provides routing rules to direct traffic from outside the cluster to specific services based on the URL path or domain name. Ingress allows for features like SSL termination, URL rewriting, and load balancing. It requires an Ingress Controller to function and is commonly used to expose web applications or APIs to the internet in a more efficient and flexible way compared to using NodePort or LoadBalancer.

## ✅ What is ConfigMap in Kubernetes?
A ConfigMap in Kubernetes is an API object used to store configuration data as key-value pairs. It allows you to separate configuration from application code, making it easier to manage and update settings without modifying the application itself. ConfigMaps can be used to store environment variables, command-line arguments, or configuration files, and they can be mounted as volumes or injected into pods as environment variables. This helps maintain flexibility and makes applications more portable and easier to manage. 

## ✅ What is a Secret in Kubernetes?
A Secret in Kubernetes is an API object used to store sensitive information, such as passwords, tokens, or SSH keys, in a more secure way than plain text. Secrets are encoded in base64 and can be mounted into pods as environment variables or volumes, ensuring that sensitive data is not exposed directly in configuration files. Kubernetes also provides access control to restrict who can view or modify secrets, adding an extra layer of security for managing confidential data in the cluster.

## ✅ How do you securely store credentials in Kubernetes?
To securely store credentials in Kubernetes, use Secrets. Secrets store sensitive information such as passwords, API keys, and tokens, encoded in base64 to prevent exposure in plaintext. They can be mounted as environment variables or volumes into pods, ensuring that sensitive data is not hard-coded in configurations. Additionally, Kubernetes offers role-based access control (RBAC) to limit access to Secrets, and integrating tools like HashiCorp Vault or AWS Secrets Manager can provide further security for managing and rotating credentials.

## ✅ What is a Horizontal Pod Autoscaler (HPA) and what metrics does it use?
A Horizontal Pod Autoscaler (HPA) in Kubernetes automatically adjusts the number of pod replicas in a deployment based on observed metrics such as CPU usage, memory usage, or custom metrics like request rate or latency. HPA helps ensure that applications scale in response to changes in traffic or resource demand, optimizing performance and resource utilization. By default, it uses CPU and memory as scaling metrics, but it can be configured to use custom metrics from monitoring tools like Prometheus.

## ✅ How does Vertical Pod Autoscaler (VPA) work?
The Vertical Pod Autoscaler (VPA) in Kubernetes automatically adjusts the CPU and memory resources of running pods based on their usage. It monitors the resource consumption of each pod and, when necessary, recommends or directly modifies the requested resources (CPU/Memory) to ensure optimal performance. VPA helps to avoid resource over-provisioning or under-provisioning, allowing pods to run efficiently. Unlike HPA, which scales the number of pods, VPA scales the resource allocation for individual pods.

## ✅ What is the difference between HPA and VPA?
The Horizontal Pod Autoscaler (HPA) and Vertical Pod Autoscaler (VPA) both help with scaling in Kubernetes, but they operate differently. HPA adjusts the number of pod replicas based on metrics like CPU, memory, or custom metrics, ensuring the application can handle varying traffic levels. VPA, on the other hand, adjusts the resource requests (CPU and memory) of individual pods to ensure they have the right resources for optimal performance, without changing the number of pods. HPA scales pods horizontally, while VPA scales resources vertically. 

## ✅ What is Role-Based Access Control (RBAC) in Kubernetes?
Role-Based Access Control (RBAC) in Kubernetes is a security mechanism that controls who can access and perform actions on resources within a cluster. It defines roles with specific permissions and then assigns those roles to users or service accounts. RBAC uses Roles and RoleBindings for namespace-level access, and ClusterRoles and ClusterRoleBindings for cluster-wide access. This helps ensure that users and applications only have the necessary permissions, improving security and resource isolation within the cluster.

## ✅ How do you debug a failing Pod?
To debug a failing pod in Kubernetes, start by checking the pod's logs using kubectl logs <pod-name> to identify any error messages or issues. If the pod has multiple containers, specify the container name with kubectl logs <pod-name> -c <container-name>. Next, inspect the pod's events using kubectl describe pod <pod-name> to look for warning or error events that could explain the failure. You can also check the status of the pod with kubectl get pod <pod-name> and look for crash loops or resource issues. If needed, run kubectl exec -it <pod-name> -- /bin/bash to access the pod's shell for further troubleshooting. 

## ✅ What is a Custom Resource Definition (CRD)?
 Custom Resource Definition (CRD) in Kubernetes allows you to extend the Kubernetes API by defining your own custom resources (CRs). CRDs enable you to create and manage resources that are not part of the default Kubernetes API, tailoring Kubernetes to your specific use cases. Once a CRD is created, you can use kubectl to interact with the custom resources just like any other built-in resource (e.g., Pods, Services). CRDs are typically used to integrate custom applications, workflows, or operators into the Kubernetes ecosystem. 
 
## ✅ What are Helm charts, and how do they simplify Kubernetes deployments?
Helm charts are pre-packaged Kubernetes configurations that simplify the deployment and management of applications on Kubernetes. They consist of templates, default configurations, and dependencies, allowing you to easily deploy complex applications with a single command. Helm charts provide reusable, versioned, and configurable deployments, making it easier to manage application releases, upgrades, and rollbacks. They help reduce the complexity of Kubernetes manifests, automate repetitive tasks, and ensure consistency across environments.

## ✅ What are the main components of Helm?
The main components of Helm are:

Helm Client – The command-line tool that interacts with the Helm server, helps manage charts, and communicates with the Kubernetes API server.
Helm Repository – A storage location for charts, which can be public or private, and allows you to download and share Helm charts.
Helm Chart – A package containing Kubernetes manifests, templates, values, and metadata used to deploy applications on Kubernetes.
Tiller (Helm v2 only) – The server-side component that manages Helm releases and interacts with Kubernetes; it has been replaced by direct interactions in Helm v3.
Together, these components enable easy deployment, upgrade, and management of applications on Kubernetes. 

## ✅ What is a Helm Chart, and what does it contain?
A Helm Chart is a packaged collection of Kubernetes resources that define and configure an application or service to be deployed on Kubernetes. It contains a set of YAML files including templates, default configuration values, and metadata. A typical chart includes:

Chart.yaml: Metadata about the chart (name, version, description).
values.yaml: Default configuration values for the application.
templates/: Kubernetes manifests (deployments, services, etc.) with placeholders for dynamic values.
charts/: Optional sub-charts, used for dependencies.
Helm charts simplify deploying and managing complex applications by providing reusable, versioned, and configurable templates.

## ✅ What is a Chart.yaml file, and what is its purpose?
The Chart.yaml file is a metadata file in a Helm chart that defines essential details about the chart. It includes information such as the chart name, version, description, maintainers, and dependencies. This file is crucial for Helm to identify and manage the chart, ensuring version control and compatibility. It also helps organize Helm repositories by providing structured metadata, making it easier to share and deploy Helm charts consistently across different environments. 

## ✅ What is a values.yaml file, and how does it work?
The values.yaml file in a Helm chart defines the default configuration values for the chart. It allows users to customize application settings without modifying the chart’s templates directly. Helm templates reference these values using placeholders (e.g., {{ .Values.image.repository }}), and users can override defaults by providing a custom values.yaml or using the --set flag in the Helm CLI. This approach makes Helm charts flexible, reusable, and easily configurable across different environments. 
