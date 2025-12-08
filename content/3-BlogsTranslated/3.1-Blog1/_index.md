---
title: "Blog 1"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# How a Customer Reduced Total Cost of Ownership (TCO) by 28% for Storage with Amazon FSx for NetApp ONTAP
by **Sachin Bawse** and **Vishnu Vashist** | on **September 08, 2025** | in Advanced (300), Amazon FSx for NetApp ONTAP, Best Practices, Healthcare, Technical How-to | Permalink

Organizations with multiple branch offices often face significant challenges in managing distributed file systems, especially when relying on traditional on-premises infrastructure. Maintaining smooth file sharing across geographically dispersed locations—while ensuring security, efficient data management, and reliable user authentication—is becoming increasingly complex in today’s digital landscape.

Amazon FSx for NetApp ONTAP addresses these challenges by providing a **fully managed cloud-native file storage solution**, offering high-performance storage with **built-in replication, automated synchronization, and intelligent caching**.

In this article, the authors share how a customer deployed **FSx for ONTAP** with a **Multi-AZ configuration**, using **NetApp FlexCache** for local caching and conducting data migration using **SnapMirror**. During this process, they completed performance tests, analyzed architectural trade-offs, and performed a cost comparison—showing a **28% reduction in total cost of ownership (TCO)** compared to a traditional on-premises solution.

---

## Solution Overview
The core architecture centers around deploying an **Amazon FSx for NetApp ONTAP Multi-AZ cluster** spanning two Availability Zones to ensure high availability and fault tolerance.

Branch locations connect to FSxN through **secure VPN connections**, accessing data via **ONTAP FlexCache volumes** deployed on-premises or within VMware environments. These caches help **reduce bandwidth usage and improve responsiveness** by serving frequently accessed data locally.

Data migration is performed using **NetApp SnapMirror**, ensuring consistent data replication from the on-prem environment to AWS.

> *Figure 1: Distributed file system with **Amazon FSx** or **NetApp ONTAP** architecture.*

![Image](/images/2-Proposal/distributed.png)

Communication and caching layers include:
* Local branch → FlexCache volumes (serving hot data)
* FlexCache → FSx ONTAP origin cluster across AZs
* SnapMirror → replicating data to FSx, ensuring storage efficiency

The customer also conducted performance comparisons: when transferring a 50 MB file, **ONTAP Select cache connected to FSx** achieved 26.09 seconds, compared to **24.20 seconds on a local file server**, demonstrating near on-prem performance.

---

## Latency and FlexCache Write-Back Considerations
The **write-back** feature of FlexCache is particularly helpful when latency between the branch cache and the origin cluster exceeds **8 ms**. Under these conditions, caching significantly improves write performance.

Key architectural requirements include:
* **CPU & RAM**: Each node in the origin cluster requires at least **128 GB RAM** and approximately **20 vCPUs** to support write-back workloads.
* **ONTAP Version**: Both the origin cluster and the cache must run **ONTAP 9.15.1 or later** to enable write-back.
* **Licensing**: FlexCache (including write-back) is **built-in**; no additional license is needed.
* **Cluster Peering**: The origin and cache clusters must be **peered**, and their storage virtual machines (**SVMs**) must also be **vserver-peered** with FlexCache enabled.

These principles ensure cache stability in distributed branch deployments.

---

## Monitoring and Visibility
To gain deeper insight into FSx & ONTAP performance beyond default **Amazon CloudWatch** metrics, the solution uses **NetApp Harvest** with **Grafana**.

Harvest collects metrics such as:
* performance
* cache hit ratio
* storage efficiency
* volume-level statistics

This provides administrators with detailed observability and proactive optimization capabilities.

---

## TCO Estimate Compared to On-Premises
To quantify the cost benefits, the customer modeled a hybrid scenario comparing **FSx for ONTAP** (Multi-AZ, SSD + capacity tier at ~30/70 ratio, throughput ~256 MB/s) to an **equivalent on-prem system**.

Results showed that **FSx for ONTAP reduces TCO by an estimated 28%**, driven by lower operational overhead, improved storage efficiency, and simplified infrastructure management.

---

## Conclusion
**Amazon FSx for NetApp ONTAP** is a powerful solution for distributed file systems, especially suited for multi-branch architectures.

Through **Multi-AZ deployment, FlexCache for local acceleration, SnapMirror for migration**, and detailed **monitoring**, this architecture delivers **near-local performance, high availability**, and **a 28% reduction in TCO compared to on-premises solutions**.

This deployment demonstrates how modern cloud-integrated storage addresses traditional limitations of bandwidth, consistency, and operational complexity across multi-site environments.

---

## Authors

|
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sachin Bawse ![Image](/images/2-Proposal/Sachin-Bawse.png) | Sachin is a **GTM Specialist Storage Solution Architect at Amazon Web Services (AWS)**, where he focuses on **storage optimization, data migration**, and **performance improvement** for customer workloads. Outside work, Sachin is passionate about **traveling**, exploring **new destinations**, discovering **different cultures**, and enjoying **diverse cuisine**. |
| Vishnu Vashist ![Image](/images/2-Proposal/Vishnu-Vashist.png) | Vishnu Vashist is a **Partner Success Solutions Architect** in the **AWS Partner Organization**, supporting customers across **Healthcare & Life Sciences (HCLS)** as well as **Travel, Transportation, and Logistics**. He specializes in **migration and modernization**, supporting large-scale AWS migration projects and guiding customers and partners on architecture and infrastructure design. |
