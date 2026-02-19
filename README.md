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
- [**HALP: Heuristic Aided Learned Preference Eviction Policy for YouTube Content Delivery Network**](https://www.usenix.org/conference/nsdi23/presentation/song-zhenyu), _NSDI '23_ `[Google]`
  - An ML-augmented cache eviction policy for YouTube's CDN DRAM cache that combines heuristics with learned preferences, reducing byte miss ratio by 9.1% at peak traffic with only 1.8% CPU overhead in production.

### Networking 
- [**Accessing Cloud with Disaggregated Software-Defined Router**](https://www.usenix.org/conference/nsdi21/presentation/shao), _NSDI '21_ `[Tencent]`
  - Tencent's cloud gateway architecture that disaggregates router functionality into four independently scalable modules (access, forwarding, routing, SDN control), enabling rapid feature delivery while handling tens of Tbps of traffic.
- [**Orion: Google's Software-Defined Networking Control Plane**](https://www.usenix.org/conference/nsdi21/presentation/ferguson), _NSDI '21_ `[Google]`
  - Google's second-generation SDN control plane built on a microservice architecture with a pub-sub database, achieving 40x faster convergence and 1.16M network updates/sec across Jupiter datacenter and B4 WAN networks.
- [**When Cloud Storage Meets RDMA**](https://www.usenix.org/conference/nsdi21/presentation/gao), _NSDI '21_ `[Alibaba]`
  - Experience report on integrating RDMA into Alibaba's Pangu storage system, using podset-scoped RDMA with TCP fallback to halve client latency while maintaining high availability across exabyte-scale deployments.
- [**Evolvable Network Telemetry at Facebook**](https://www.usenix.org/conference/nsdi22/presentation/zhou), _NSDI '22_ `[Meta]`
  - Presents PCAT, a change-aware telemetry system that tracks and confines changes across Meta's rapidly evolving network (30+ code commits/week), preventing cascading failures in monitoring hundreds of thousands of switches and billions of counters.
- [**Bluebird: High-performance SDN for Bare-metal Cloud Services**](https://www.usenix.org/conference/nsdi22/presentation/arumugam), _NSDI '22_ `[Microsoft]`
  - Azure's network virtualization system for bare-metal cloud using programmable switch ASICs with custom P4 programs, delivering full line-rate up to 100Gb/s with sub-microsecond latency per SDN switch hop.
- [**Cetus: Releasing P4 Programmers from the Chore of Trial and Error Compiling**](https://www.usenix.org/conference/nsdi22/presentation/li-yifan), _NSDI '22_ `[Alibaba]`
  - A compiler that automatically transforms uncompilable P4 programs into functionally equivalent compilable ones by shortening dependency chains, reducing Alibaba's P4 development cycle from days to minutes.
- [**Norma: Towards Practical Network Load Testing**](https://www.usenix.org/conference/nsdi23/presentation/chen-yanqing), _NSDI '23_ `[Alibaba]`
  - A programmable-switch-based network load tester capable of generating up to 3 Tbps of stateful TCP traffic, deployed at Alibaba for over two years to detect performance issues in production network devices.
- [**Empowering Azure Storage with RDMA**](https://www.usenix.org/conference/nsdi23/presentation/bai), _NSDI '23_ `[Microsoft]`
  - Documents Microsoft's regional-scale RDMA deployment for Azure Storage, now carrying 70% of Azure traffic across all public regions, moving exabytes of data daily from TCP to RDMA with significant latency and CPU savings.
- [**Harnessing WebRTC for Large-Scale Live Streaming**](https://dl.acm.org/doi/10.1145/3718958.3750535), _SIGCOMM '25_ `[ByteDance]`
  - ByteDance's production system for adapting WebRTC to large-scale live streaming, optimizing first-frame delay, startup rebuffering, audio-to-video drift, and per-session CPU usage.
- [**Intent-Driven Network Management with Multi-Agent LLMs: The Confucius Framework**](https://dl.acm.org/doi/10.1145/3718958.3750537), _SIGCOMM '25_ `[ByteDance]`
  - A multi-agent LLM framework for network management that models workflows as DAGs, integrates LLMs with existing tools via RAG, and has been operational for two years with 60+ applications, reducing developer time by 17 engineer-hours/week.
- [**Alibaba Stellar: A New Generation RDMA Network for Cloud AI**](https://dl.acm.org/doi/10.1145/3718958.3750539), _SIGCOMM '25_ `[Alibaba]`
  - Alibaba's RDMA virtualization stack for cloud AI, introducing para-virtualized DMA for on-demand memory pinning, an extended memory translation table for GPUDirect RDMA, and RDMA packet spray for efficient multi-path utilization.

### Machine Learning Infrastructure
- [**Check-N-Run: a Checkpointing System for Training Deep Learning Recommendation Models**](https://www.usenix.org/conference/nsdi22/presentation/eisenman), _NSDI '22_ `[Meta]`
  - A scalable checkpointing system for Meta's terabyte-scale recommendation models that uses incremental checkpointing and quantization to achieve 6-17x reduction in write bandwidth and 2.5-8x reduction in storage capacity.
- [**MLaaS in the Wild: Workload Analysis and Scheduling in Large-Scale Heterogeneous GPU Clusters**](https://www.usenix.org/conference/nsdi22/presentation/weng), _NSDI '22_ `[Alibaba]`
  - A characterization study of Alibaba's PAI GPU cluster (6,742+ GPUs, 1,300+ users), revealing low utilization and long queueing delays, and proposing GPU sharing and reserving-and-packing scheduling policies to improve efficiency.
- [**MAST: Global Scheduling of ML Training across Geo-Distributed Datacenters at Hyperscale**](https://www.usenix.org/conference/osdi24/presentation/choudhury), _OSDI '24_ `[Meta]`
  - Addresses the GPU shortage by enabling Meta to train large models across *distributed* global datacenters, overcoming massive bandwidth constraints.

### Serverless & Microservices
- [**Firecracker: Lightweight Virtualization for Serverless Applications**](https://www.usenix.org/conference/nsdi20/presentation/agache), _NSDI '20_ `[Amazon]`
  - AWS describes the VMM behind Lambda, which stripped down QEMU to create "MicroVMs" that boot in <125ms for true multi-tenant isolation.
- [**ServiceRouter: Hyperscale and Minimal Cost Service Mesh at Meta**](https://www.usenix.org/conference/osdi23/presentation/saokar), _OSDI '23_ `[Meta]`
  - Meta's take on a service mesh optimized for hyperscale, focusing on minimizing the "sidecar tax" (CPU/RAM overhead) that standard meshes incur.
- [**Hermes: Enhancing Layer-7 Cloud Load Balancers with Userspace-Directed I/O Event Notification**](https://dl.acm.org/doi/10.1145/3718958.3750469), _SIGCOMM '25_ `[Alibaba]`
  - An eBPF-based framework that enables closed-loop scheduling between userspace workers and the kernel for L7 load balancers, processing 10M+ requests/sec on 100K CPU cores with 19% infrastructure cost reduction, deployed for over two years.

### Reliability & Debugging
- [**Towards LLM-Based Failure Localization in Production-Scale Networks**](https://dl.acm.org/doi/10.1145/3718958.3750505), _SIGCOMM '25_ `[Alibaba]`
  - BiAn, an LLM-based framework that processes monitoring data to rank error devices with explanations during network incidents, reducing root-cause time by 20.5% overall (55.2% for high-risk incidents) across 10 months of production deployment.
- [**SkeletonHunter: Diagnosing and Localizing Network Failures in Containerized Large Model Training**](https://dl.acm.org/doi/10.1145/3718958.3750513), _SIGCOMM '25_ `[Alibaba]`
  - A network diagnosis system that exploits the intrinsic traffic sparsity in large model training to detect and localize failures, achieving 98.2% precision and 95.7% localization accuracy across 40K+ GPUs at Alibaba Cloud.
