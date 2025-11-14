# Large-Scale Virtual Environment: 1000 Ubuntu VMs

## Overview
This project focuses on designing and architecting a large-scale virtual environment capable of hosting **1000 Ubuntu VMs** with dedicated CPU, RAM, storage, network segmentation, and redundancy.  

**Focus Areas:**
 - High-density VM deployment
- Compute and storage redundancy
- Network segmentation and performance
 - Resource optimization and scalability

---

## Project Goals
- Deploy **1000 Ubuntu VMs**:
  - **1 vCPU per VM**
  - **4 GB RAM per VM**
  - **50 GB storage per VM**
- Achieve **high availability** through compute, storage, and network redundancy
- Implement **VLAN separation** for VM and storage traffic
- Document architecture, rationale, and resource allocation decisions

---

## Hardware Specifications

### Servers
| Component | Specification | Notes |
|-----------|---------------|-------|
| Model | HPE ProLiant DL380 Gen11 (3 units) | Server 3 optionally supports 3 CPUs |
| CPU | 2 × Intel Xeon Gold 6430 (32 cores each, 2.1 GHz) | Dual CPUs per server provide ~512 vCPUs |
| RAM | 2.176 TB per server (34 × 64GB RDIMM) | Sufficient for ~333–334 VMs per server |
| Storage | 1 × 480GB NVMe boot drive (HPE P48183-B21) | Local RAID configuration for boot |
| Network | 2 × Broadcom BCM571 25Gb 2-port SFP28 | High-speed connectivity |
| PSU | 4 × 850W | Redundant power |

### Networking
- 2 × HPE Aruba CX 8325 switches (448 SFP28 ports)
- Multi-chassis link aggregation (VSF/VSE)
- VLAN separation for VM and storage traffic
- DAC cables for high-speed server-storage connectivity

### Storage
- HPE Alletra 6000 Series
- 70–100 TB total capacity (50 TB reserved for VM storage)
- RAID, snapshots, and replication for high availability

### Power
| Component | Power Consumption |
|-----------|-----------------|
| Servers (3) | 3 × 1600W = 4800W |
| Switches (2) | 2 × 725W = 1450W |
| Storage (4) | 4 × 800W = 3200W |
| PDUs | 4 × HPE G2 Metered Vertical PDU, 280V input |

---

## Virtualization Architecture
- **Hypervisor:** VMware ESXi 8.x
- **VM Template:** Ubuntu Server 22.04 LTS
- **VM Specs:** 1 vCPU, 4 GB RAM, 50 GB storage
- **Cluster:** ~333–334 VMs per host
- **Networking:** VLAN separation for management, VM, and storage traffic; multi-chassis aggregation for redundancy
- **Storage:** Shared datastore with snapshots and replication

---

## Implementation Steps (IF I had the hardware)
1. **Server Preparation:** Install ESXi and configure local RAID.
2. **Networking Setup:** Configure VLANs and aggregate switches using VSF.
3. **Storage Integration:** Connect HPE Alletra, configure datastores and replication.
4. **VM Deployment:** Create Ubuntu template, clone 1000 VMs using automation, distribute across three hosts.
5. **Validation:** Test resource allocation, connectivity, and failover; AI-assisted hardware compatibility checks.

---

## Tools & Automation
- **Provisioning:** PowerCLI / Ansible for bulk VM creation
- **Monitoring:** vCenter / Prometheus
- **Documentation & Diagrams:** Draw.io / Lucidchart
- **Runbooks:** Configuration guides and automation scripts

---

## Learning Outcomes
- High-density VM infrastructure design
- Compute, memory, and storage allocation strategies
- Networking segmentation and link aggregation techniques
- Automation for large-scale VM provisioning
- Redundancy and failover planning

---

## Future Enhancements
- Expand automation scripts for patching, backup, and monitoring
- Implement virtual firewall for VM isolation

---

