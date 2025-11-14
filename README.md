
Project Overview:
-----------------
This project demonstrates a high-density virtualized environment
capable of hosting 1000 lightweight Ubuntu VMs. The cluster uses
three HPE ProLiant DL380 Gen11 servers, connected to HPE Alletra
storage arrays via HPE Aruba CX 8325 switches. This build was
designed as a portfolio project to showcase enterprise-level
resource planning, virtualization expertise, and high-density
VM management.

Objectives:
-----------
- Deploy 1000 Ubuntu VMs for lightweight workloads
- Maintain high availability and redundancy
- Efficient allocation of CPU, RAM, and storage resources
- Secure, segmented networks for VM, storage, and management traffic
- Demonstrate automation and monitoring in a high-density environment

Hardware Configuration:

Compute (3 Servers):

 Server     | HPE ProLiant DL380 Gen11 (3 units)  
 CPU        | 2 x Intel Xeon Gold 6430 (32 cores)
 RAM        | 2.1 TB DDR5 per server             
 vCPUs      | ~333–334 (1 vCPU per VM)          
 VM Specs   | 1 vCPU / 4 GB RAM / 50 GB disk    
 NIC        | 2 x Broadcom BCM571 25Gb SFP28    
 Storage    | HPE P48183-B21 NVMe (boot device) 


Storage:

 Array      | HPE Alletra 6000 Series             
 Capacity   | 70–100 TB (50 TB for VMs)          
 Connectivity| DAC to Aruba switches              
 Redundancy | RAID / mirroring                    


Networking:

 Switch     | 2 x HPE Aruba CX 8325 (448 SFP28)  
 Connectivity | 25 Gb DAC from server NICs       
 VLANs      | Separate VLANs: VM, storage, mgmt
 Features   | Multi-chassis LAG, failover, seg. 


Virtualization Layer:

- Hypervisor: VMware ESXi 8.x
- Management: vCenter Server for HA, DRS, resource monitoring
- Automation: PowerCLI or Ansible scripts for bulk deployment
- High Availability: vSphere HA for automatic VM restart
- Load Balancing: vSphere DRS distributes workloads

Security & Segmentation:

- VLAN separation for management, storage, and VM networks
- Optional firewall segmentation for lab/testing
- Snapshots and backup policies

Monitoring & Automation:

- Tools: vCenter performance charts, Prometheus + Grafana dashboards
- Scripts: Bulk provisioning, snapshot management, alerts
- Alerting: Automated notifications for CPU/RAM/storage spikes



Future Improvements:
--------------------
- Optional extra CPU on Server 3 for heavier workloads
- Expand storage or implement NVMe caching for higher I/O
- Add a fourth server if VM count exceeds 1000
- Advanced automation for provisioning, monitoring, alerts

Notes:
------
- Designed for lightweight VMs for lab or portfolio purposes
- Demonstrates resource planning, networking, storage, and compute redundancy
- Shows automation, monitoring, and security best practices
