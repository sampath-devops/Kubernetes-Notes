# Kubernetes-Notes
# Limitations of Docker (Without Orchestration) – Problem Use Cases

1. Single-Host Limitation (No High Availability) :
        Docker containers usually run on a single host unless you manually configure multiple hosts. Docker is dependent on the underlying host. If the host crashes, all containers go            down and it cannot distribute containers across multiple nodes.

        Example: You are running 99 containers on one server. When you try to start the 100th container, it fails because:
        Container 1 or 2 is consuming more CPU/RAM. The host has reached its resource limits.
        Docker cannot: 
          --> Automatically rebalance workloads
          --> Move containers to another host 
          --> Detect resource pressure and adjust workloads
  
2. No Auto-Healing
        Docker cannot automatically restart or recreate containers if they crash or someone deletes them, The application inside the container stops responding and you must manually              check container states.
        Example : If a team member accidentally deletes a container Docker will not Recreate the container and You must manually start the container again

3. No Auto-Scaling / No Built-in Load Management
        Docker does not automatically scale containers based on CPU, Memory usage, number of users and application load
        Example: Your application is running in 2 containers and can handle ~500 users.If traffic suddenly jumps to 1000 or 10,000 users, Docker cannot create additional containers               automatically, balance traffic between them and manage scaling up or down

4. Not Suitable Alone for Enterprise/Production Standards
        For enterprise-grade deployments, organizations need:
                        High availability
                        Auto-scaling
                        Self-healing
                        Multi-node clustering
                        Fault tolerance
                        Observability and alerts
        Docker alone cannot provide these features.
   
    **Docker vs Kubernetes**(COMPARISON DIAGRAM)

                 ┌───────────────────────────┐
                 │         APPLICATION        │
                 └───────────────────────────┘
                               │
                               ▼
                    ┌───────────────────┐
                    │       DOCKER      │
                    └───────────────────┘
                          (Single Host)
                    ┌──────────────────────┐
                    │   Docker Engine       │
                    │  ────────────────     │
   Build Image ---->│  Images & Containers  │
                    │                        │
   Run Container -->│  Manual Scaling        │
                    │  Manual Healing        │
                    │  No Multi-Node         │
                    └──────────────────────┘
                               │
                         Limitations
                               ▼
        ============================================================== 
                               ▼
                    ┌───────────────────┐
                    │    KUBERNETES     │
                    └───────────────────┘
                     (Multi-Node Cluster)
        ┌──────────────────────┬─────────────────────────┬───────────────────────┐
        │ Control Plane        │ Worker Nodes            │ External Integrations │
        │                       │                         │ (Ingress, LB, etc.)  │
        ├──────────────────────┼─────────────────────────┼───────────────────────┤
        │ API Server           │ Kubelet                 │ Auto-Scaling          │
        │ Scheduler            │ Container Runtime       │ Load Balancing        │
        │ Controller Manager   │ Pods & Deployments      │ Service Mesh          │
        │ ETCD (Cluster Store) │ Node-Level Resources    │ Cloud Integrations    │
        └──────────────────────┴─────────────────────────┴───────────────────────┘
                               │
                       Kubernetes Features
                               ▼
          ┌──────────────────────────────────────────────────┐
          │ • Auto-Healing (restarts pods automatically)      │
          │ • Auto-Scaling (HPA, VPA)                         │
          │ • Multi-Node High Availability                    │
          │ • Rolling Updates & Rollbacks                     │
          │ • Self-Monitoring with Probes                     │
          │ • Load Balancing & Service Discovery              │
          │ • Enterprise Production-Ready                     │
          └──────────────────────────────────────────────────┘
          ┌───────────────┐          ┌─────────────────────────┐
          │   DOCKER       │   vs.    │        KUBERNETES       │
          └───────────────┘          └─────────────────────────┘
          │ Single Host               │ Multi-Node Cluster
          │ Manual Scaling            │ Auto-Scaling
          │ Manual Healing            │ Auto-Healing
          │ No Orchestration          │ Full Orchestration
          │ Not HA Ready              │ Highly Available
          └───────────────┘          └─────────────────────────┘


# Kubernetes Architecture
<img width="1054" height="661" alt="image" src="https://github.com/user-attachments/assets/1d267932-7ef9-4560-8759-02157c33379c" />


