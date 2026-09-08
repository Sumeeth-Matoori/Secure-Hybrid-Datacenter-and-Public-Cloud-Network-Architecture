# 🔐 Secure Hybrid Datacenter and Public Cloud Network Architecture

## 📌 Project Overview

This project demonstrates the design and implementation of a **Secure Hybrid Datacenter and Public Cloud Network Architecture**.

The project combines a private datacenter network with a simulated cloud environment and implements multiple security mechanisms to protect network resources.

The practical implementation was developed using **Cisco Packet Tracer** and includes:

* VLAN Segmentation
* Inter-VLAN Routing
* Router-on-a-Stick
* Extended Access Control Lists (ACLs)
* Static Routing
* Private Datacenter-to-Cloud Connectivity
* AWS IAM Design
* AWS Security Group Design
* VPC and Application Segmentation

---

## 🎯 Aim

To design and implement a secure hybrid datacenter and public cloud network using Cisco Packet Tracer with:

* VLAN segmentation
* Inter-VLAN routing
* ACL-based access control
* Controlled private-to-cloud connectivity
* IAM and Security Group design

---

## 🏗️ Network Architecture

The network architecture follows the structure:

Faculty / Admin / Guest / Servers
↓
SW1-Core
↓
R1-DataCenter
↓
R1–R2 WAN
↓
R2-Cloud
↓
CLOUD-APP

The architecture separates the private datacenter and cloud environment using a dedicated routed connection.

---

## 🌐 VLAN Design

| VLAN ID | VLAN Name | Network         | Purpose                          |
| ------- | --------- | --------------- | -------------------------------- |
| 10      | FACULTY   | 192.168.10.0/24 | Faculty Users                    |
| 20      | ADMIN     | 192.168.20.0/24 | Administrative Users             |
| 30      | SERVERS   | 192.168.30.0/24 | Application and Database Servers |
| 40      | GUEST     | 192.168.40.0/24 | Restricted Guest Users           |

---

## 📡 IP Addressing

| Device / Interface | IP Address    |
| ------------------ | ------------- |
| R1 G0/0.10         | 192.168.10.1  |
| R1 G0/0.20         | 192.168.20.1  |
| R1 G0/0.30         | 192.168.30.1  |
| R1 G0/0.40         | 192.168.40.1  |
| R1 G0/1            | 192.168.50.1  |
| R2 G0/0            | 192.168.50.2  |
| R2 G0/1            | 203.0.113.1   |
| R2 G0/2            | 172.16.10.1   |
| APP-Server         | 192.168.30.10 |
| DB-Server          | 192.168.30.20 |
| CLOUD-APP          | 172.16.10.10  |

---

# 🔒 Security Implementation

## VLAN Segmentation

The network is divided into separate VLANs for:

* Faculty
* Admin
* Servers
* Guest Users

This improves network security by separating users and resources into different network segments.

---

## 🔄 Inter-VLAN Routing

Router-on-a-Stick configuration is used on **R1-DataCenter**.

Each VLAN has a separate router subinterface that acts as its default gateway.

---

## 🛡️ ACL-Based Security

Extended Access Control Lists (ACLs) are used to control access to sensitive resources.

### Faculty Users

Allowed:

* Application Server
* Cloud Application

Blocked:

* Direct Database Access

### Admin Users

Allowed:

* Application Server
* Database Server
* Cloud Application

### Guest Users

Blocked from:

* Application Server
* Database Server
* Cloud Application

---

# ☁️ Private Datacenter to Cloud Connectivity

A dedicated point-to-point network connects:

R1-DataCenter ↔ R2-Cloud

WAN Network:

192.168.50.0/30

Static routing is configured to allow controlled communication between:

* Private Datacenter
* Cloud Application Network

Cloud Application Network:

172.16.10.0/24

---

# 🔐 AWS IAM Design

The project includes a conceptual AWS IAM design based on the principle of **Least Privilege**.

### Proposed Roles

| Role                      | Responsibility                         |
| ------------------------- | -------------------------------------- |
| Cloud Administrator       | Manage overall cloud resources         |
| Network Administrator     | Manage VPC, Routes and Security Groups |
| Application Administrator | Manage application resources           |
| Database Administrator    | Manage database resources              |
| Faculty User              | Access approved services               |
| Guest User                | Limited external services              |

---

# 🛡️ AWS Security Group Design

| Security Group | Purpose                                                                             |
| -------------- | ----------------------------------------------------------------------------------- |
| SG-Web         | Allows required HTTP/HTTPS traffic                                                  |
| SG-App         | Allows application traffic from approved sources                                    |
| SG-Database    | Allows database access only from the application tier and authorized administrators |

The database is not directly exposed to general users or the Internet.

---

# 🧪 Testing Results

| Test Case            | Expected Result | Status       |
| -------------------- | --------------- | ------------ |
| Faculty → Gateway    | Allowed         | PASS         |
| Faculty → APP Server | Allowed         | PASS         |
| Faculty → Database   | Blocked         | PASS         |
| Faculty → CLOUD-APP  | Allowed         | PASS         |
| Admin → APP Server   | Allowed         | PASS         |
| Admin → Database     | Allowed         | PASS         |
| Admin → CLOUD-APP    | Allowed         | PASS         |
| Guest → APP Server   | Blocked         | PASS         |
| Guest → Database     | Blocked         | PASS         |
| Guest → CLOUD-APP    | Blocked         | PASS         |
| R1 → R2              | Allowed         | 100% Success |
| R1 → CLOUD-APP       | Allowed         | 100% Success |

---

# 🛠️ Technologies Used

* Cisco Packet Tracer
* VLANs
* Router-on-a-Stick
* Extended ACLs
* Static Routing
* Network Segmentation
* AWS IAM Concepts
* AWS Security Groups
* AWS VPC Concepts

---

# 🚀 Key Features

* Secure VLAN Segmentation
* Inter-VLAN Routing
* Router-on-a-Stick Configuration
* Extended ACL Security Policies
* Faculty Database Access Restriction
* Guest Network Isolation
* Private Datacenter to Cloud Connectivity
* Static Routing
* Cloud Application Isolation
* IAM Role-Based Access Design
* AWS Security Group Design
* Attack Containment Through Network Segmentation

---

# 🧠 Security Principles Applied

This project follows important cybersecurity principles:

* Least Privilege
* Network Segmentation
* Defense in Depth
* Access Control
* Workload Isolation
* Attack Containment

---

# 📂 Project Structure

Secure-Hybrid-Datacenter-Cloud/

├── README.md
├── Project_Report.pdf
├── Network_Topology/
│   └── Hybrid_Network_Topology.png
├── Screenshots/
│   ├── VLAN_Configuration.png
│   ├── ACL_Configuration.png
│   ├── Routing_Test.png
│   └── Connectivity_Test.png
└── PacketTracer/
└── Hybrid_Datacenter_Cloud.pkt

---

# 🎓 Learning Outcomes

Through this project, I gained practical knowledge of:

* VLAN Configuration
* Network Segmentation
* Router-on-a-Stick
* Extended ACL Configuration
* Static Routing
* Network Troubleshooting
* Hybrid Cloud Networking
* AWS IAM Concepts
* AWS Security Groups
* VPC Segmentation
* Cybersecurity Architecture

---

# 🔮 Future Improvements

Future enhancements for this project include:

* Deploying the architecture on an actual AWS VPC
* Implementing Public and Private Subnets
* Using AWS IAM Roles and Policies
* Configuring AWS Network ACLs
* Implementing Site-to-Site VPN connectivity
* Adding centralized logging and monitoring
* Performing vulnerability assessments
* Implementing Kubernetes network policies
* Adding redundancy and disaster recovery mechanisms

---

# 🌍 SDG Contribution

## SDG 9 – Industry, Innovation and Infrastructure

Secure networking is an important part of reliable digital infrastructure. This project demonstrates how network segmentation, access control, and secure hybrid connectivity can contribute to building a more secure and dependable digital environment.

---

# 👨‍💻 Author

**Sumeeth Goud Matoori**

Cyber Security Student
Marwadi University
Cisco–AICTE Virtual Internship Program 2026

---

# 📜 License

This project is developed for **educational and academic purposes** as part of the **Cisco–AICTE Virtual Internship Program 2026**.

---

⭐ If you found this project useful, consider giving the repository a star!
