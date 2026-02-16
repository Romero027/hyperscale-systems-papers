# Production Systems Reading List 

A curated list of recent papers from top systems and networking conferences (e.g., NSDI, OSDI, SOSP, SIGCOMM) describing the design and implementation of production systems at major tech companies (e.g., Google, Meta, Microsoft, Amazon), starting from 2020.


## Index

* [**Cluster Management & Scheduling**](#cluster-management--scheduling)
* [**Distributed Storage & Databases**](#distributed-storage--databases)
* [**Networking**](#networking)
* [**Machine Learning Infrastructure**](#machine-learning-infrastructure)
* [**Serverless & Microservices**](#serverless--microservices)
* [**Reliability & Debugging**](#reliability--debugging)

---

## Reading List

### Cluster Management & Scheduling
- [**Autopilot: Workload Autoscaling at Google**](https://dl.acm.org/doi/10.1145/3342195.3387524), _EuroSys '20_ `[Google]`
  - Explains how Google automatically adjusts resources for jobs in Borg to improve utilization without manual tuning.
- [**Twine: A Unified Cluster Management System for Shared Infrastructure**](https://www.usenix.org/conference/osdi20/presentation/tang), _OSDI '20_ `[Meta]`
  - Meta's cluster management system that unifies the lifecycle of maximizing hardware utilization, moving beyond simple task packing to managing the entire machine lifecycle.
- [**Protean: VM Allocation Service at Scale**](https://www.usenix.org/conference/osdi20/presentation/hadary), _OSDI '20_ `[Microsoft]`
  - Microsoft Azure's centralized allocation service that manages millions of VMs across global regions, focusing on meeting varied placement constraints and packing efficiency.
- [**Global Capacity Management With Flux**](https://www.usenix.org/conference/osdi23/presentation/eriksen), _OSDI '23_ `[Meta]`
  - Describes how Meta places services across regions to handle massive scale constraints, power availability, and disaster recovery.

### Distributed Storage & Databases
- [**Millions of Tiny Databasess**](https://www.usenix.org/conference/nsdi20/presentation/brooker), _NSDI '20_ `[AWS]`
  - AWS describes the architecture behind EBS, arguing for "blast radius reduction" by using millions of tiny Paxos groups rather than one massive monolithic consensus system.
- [**Virtual Consensus in Delos**](https://www.usenix.org/conference/osdi20/presentation/balakrishnan), _OSDI '20_ `[Meta]`
  - Meta's control plane storage system that allows hot-swapping the underlying consensus protocol (e.g., swapping ZooKeeper for a new protocol) without downtime.
- [**Shard Manager: A Generic Shard Management Framework for Geo-distributed Applications**](https://dl.acm.org/doi/10.1145/3477132.3483546), _SOSP '21_ `[Meta]`
  - A framework that manages the placement and migration of shards for hundreds of different stateful services at Meta, decoupling this complex logic from application code.

### Networking 
- [**Accessing Cloud with Disaggregated Software-Defined Router**](https://www.usenix.org/conference/nsdi21/presentation/shao), _NSDI '21_ `[Tencent]`
  - Tencent's cloud gateway architecture that disaggregates router functionality into four independently scalable modules (access, forwarding, routing, SDN control), enabling rapid feature delivery while handling tens of Tbps of traffic.
- [**Orion: Google's Software-Defined Networking Control Plane**](https://www.usenix.org/conference/nsdi21/presentation/ferguson), _NSDI '21_ `[Google]`
  - Google's second-generation SDN control plane built on a microservice architecture with a pub-sub database, achieving 40x faster convergence and 1.16M network updates/sec across Jupiter datacenter and B4 WAN networks.
- [**When Cloud Storage Meets RDMA**](https://www.usenix.org/conference/nsdi21/presentation/gao), _NSDI '21_ `[Alibaba]`
  - Experience report on integrating RDMA into Alibaba's Pangu storage system, using podset-scoped RDMA with TCP fallback to halve client latency while maintaining high availability across exabyte-scale deployments.

### Machine Learning Infrastructure
- [**MAST: Global Scheduling of ML Training across Geo-Distributed Datacenters at Hyperscale**](https://www.usenix.org/conference/osdi24/presentation/choudhury), _OSDI '24_ `[Meta]`
  - Addresses the GPU shortage by enabling Meta to train large models across *distributed* global datacenters, overcoming massive bandwidth constraints.

### Serverless & Microservices
- [**Firecracker: Lightweight Virtualization for Serverless Applications**](https://www.usenix.org/conference/nsdi20/presentation/agache), _NSDI '20_ `[Amazon]`
  - AWS describes the VMM behind Lambda, which stripped down QEMU to create "MicroVMs" that boot in <125ms for true multi-tenant isolation.
- [**ServiceRouter: Hyperscale and Minimal Cost Service Mesh at Meta**](https://www.usenix.org/conference/osdi23/presentation/saokar), _OSDI '23_ `[Meta]`
  - Meta's take on a service mesh optimized for hyperscale, focusing on minimizing the "sidecar tax" (CPU/RAM overhead) that standard meshes incur.

### Reliability & Debugging

