# 🎮 Optimizing Cloud Gaming Latency Using Edge Computing & Modular Edge Data Centers

<p align="center">
  <b>A Simulation-Based Study Using Cisco Packet Tracer</b>
</p>

<p align="center">
  <b>Akshat Raj</b><br>
  Department of Computer Science<br>
  CHRIST (Deemed to be University), Bangalore, India
</p>

---

## 📌 Overview

Cloud gaming allows users to play computationally intensive games without requiring powerful local hardware. The game is executed on a remote server, while video frames are streamed to the user and player inputs are transmitted back to the server.

However, this architecture is highly sensitive to **network latency**.

For users in India, accessing cloud gaming infrastructure hosted in geographically distant data centers can require traffic to traverse multiple network layers and international transit links.

This project investigates whether **Edge Computing** and **Modular Edge Data Centers (MDCs)** can reduce the network path between gamers and cloud gaming servers.

Two network architectures were designed and simulated using **Cisco Packet Tracer**:

1. A traditional **Centralized Cloud Gaming Architecture**
2. A proposed **Edge Computing + Modular Edge Data Center Architecture**

The study focuses on network topology, routing behavior, hop reduction, connectivity, and simulated latency.

---

## 🎯 Research Objective

The primary objective of this project is to investigate how placing cloud gaming infrastructure closer to users through **Modular Edge Data Centers** can improve the network architecture for latency-sensitive cloud gaming applications.

The project aims to:

- Model a centralized cloud gaming network.
- Model an edge-enabled cloud gaming network.
- Simulate users from multiple Indian metropolitan cities.
- Configure dynamic routing using **OSPF**.
- Optimize routing toward the edge infrastructure.
- Compare centralized and edge-based routing paths.
- Verify end-to-end network connectivity.
- Analyze hop count and simulated latency.
- Study the potential benefits and limitations of edge computing for cloud gaming.

---

## 🏙️ Simulated User Locations

The network represents cloud gaming users from four major Indian metropolitan cities:

| City | Local Network |
|------|---------------|
| Bangalore | `192.168.10.0/24` |
| Delhi | `192.168.20.0/24` |
| Hyderabad | `192.168.30.0/24` |
| Chennai | `192.168.40.0/24` |

Each user connects through a local/home network to a regional ISP before reaching the national network infrastructure.

---

# 🏗️ Network Architecture

## Scenario 1 — Centralized Cloud Gaming

The first scenario represents a traditional centralized cloud architecture.

The gaming server is hosted in a simulated **Singapore Data Center**.

### Network Path

```text
Gamer
  │
  ▼
Home WiFi Router
  │
  ▼
Regional / City ISP
  │
  ▼
India Core Network
  │
  ▼
International Transit
  │
  ▼
Singapore Data Center
  │
  ▼
Cloud Gaming Server
```

Traffic from Indian users must therefore traverse the national core and international transit infrastructure before reaching the gaming server.

### Conceptual Architecture

```text
 Bangalore Gamer ── Bangalore ISP ──┐
                                    │
 Delhi Gamer ────── Delhi ISP ──────┤
                                    │
 Hyderabad Gamer ── Hyderabad ISP ──┼── India Core
                                    │       │
 Chennai Gamer ───── Chennai ISP ───┘       │
                                            ▼
                                   International Transit
                                            │
                                            ▼
                                   Singapore DC Router
                                            │
                                            ▼
                                   Cloud Gaming Server
```

---

## Scenario 2 — Edge Computing + MDC

The second scenario introduces a **Modular Edge Data Center (MDC)** connected closer to the users within the Indian network infrastructure.

Instead of sending gaming traffic through the international route, eligible traffic can reach a local edge gaming server.

### Optimized Network Path

```text
Gamer
  │
  ▼
Home WiFi Router
  │
  ▼
Regional / City ISP
  │
  ▼
India Core Network
  │
  ▼
Modular Edge Data Center
  │
  ▼
Edge Gaming Server
```

### Conceptual Architecture

```text
 Bangalore Gamer ── Bangalore ISP ──┐
                                    │
 Delhi Gamer ────── Delhi ISP ──────┤
                                    │
 Hyderabad Gamer ── Hyderabad ISP ──┼── India Core
                                    │       │
 Chennai Gamer ───── Chennai ISP ───┘       │
                                            ▼
                                  Modular Edge Data Center
                                            │
                                            ▼
                                      Edge Server
```

This architecture reduces the number of network layers that gaming traffic must traverse before reaching the server.

---

# 🖥️ Simulation Environment

The network was developed using:

- **Cisco Packet Tracer**
- Cisco 2911 Routers
- Cisco 2960 Switch
- WRT300N Wireless Routers
- Simulated Gamer Laptops
- Cloud Gaming Server
- Edge Gaming Server
- Modular Edge Data Center
- OSPF Dynamic Routing

---

# 🔧 Network Components

## Gamer Devices

Four laptops represent gamers located in:

- Bangalore
- Delhi
- Hyderabad
- Chennai

These devices generate traffic toward the gaming infrastructure.

---

## Home WiFi Routers

Each gamer connects through a **WRT300N wireless router**.

These devices represent the user's home/local access network before traffic reaches the regional ISP.

---

## Regional ISP Routers

Cisco 2911 routers represent regional ISP infrastructure for each simulated city.

The four ISP routers represent:

```text
Bangalore ISP
Delhi ISP
Hyderabad ISP
Chennai ISP
```

They forward traffic from local networks toward the India Core network.

---

## India Core Router

The **India Core Router** represents the national-level backbone connecting the regional ISP networks.

It serves as the major routing point between:

```text
Regional ISPs
      │
      ▼
  India Core
   /       \
  ▼         ▼
Edge      International
Network     Transit
```

---

## International Transit Router

The International Transit Router represents the network infrastructure required to route traffic outside India toward the Singapore data center.

This path is primarily used in the centralized cloud architecture.

---

## Singapore Data Center

The Singapore Data Center contains the simulated centralized cloud gaming server.

The gaming server uses:

```text
IP Address : 172.16.1.100
Subnet     : 255.255.255.0
Gateway    : 172.16.1.1
```

---

## Modular Edge Data Center

The proposed architecture introduces a **Modular Edge Data Center (MDC)** connected to the India Core network.

The edge network uses:

```text
Network     : 192.168.200.0/24
Edge Server : 192.168.200.10
MDC Gateway : 192.168.200.1
```

The Core-to-MDC point-to-point network uses:

```text
40.0.0.0/30
```

---

# 🌐 IP Addressing Scheme

## Gamer Networks

| Location | Network | Gateway |
|----------|---------|---------|
| Bangalore | `192.168.10.0/24` | `192.168.10.1` |
| Delhi | `192.168.20.0/24` | `192.168.20.1` |
| Hyderabad | `192.168.30.0/24` | `192.168.30.1` |
| Chennai | `192.168.40.0/24` | `192.168.40.1` |

## ISP Network

| Device | IP Address |
|--------|------------|
| Bangalore ISP | `10.0.0.1/24` |
| Delhi ISP | `10.0.0.2/24` |
| Hyderabad ISP | `10.0.0.3/24` |
| Chennai ISP | `10.0.0.4/24` |

## Core / International Infrastructure

| Component | IP / Network |
|-----------|--------------|
| India Core | `20.0.0.1/24` |
| International Transit | `20.0.0.2/24` |
| Singapore DC Router | `30.0.0.1/24` |

## Edge Infrastructure

| Component | IP / Network |
|-----------|--------------|
| Edge Network | `192.168.200.0/24` |
| MDC Gateway | `192.168.200.1` |
| Edge Gaming Server | `192.168.200.10` |
| Core-MDC Link | `40.0.0.0/30` |

---

# 🔀 OSPF Routing

Dynamic routing was implemented using **Open Shortest Path First (OSPF)**.

OSPF enables routers to dynamically exchange routing information and determine appropriate paths between networks.

OSPF was configured across the simulated routing infrastructure, including:

- Regional ISP routers
- India Core Router
- International Transit Router
- Singapore Data Center Router
- MDC / Edge infrastructure

---

## Edge Routing Optimization

In the edge architecture, routing metrics were configured so that the MDC path has a **lower OSPF cost** than the international path.

Conceptually:

```text
                    ┌──── MDC ──── Edge Server
                    │
                    │ Lower OSPF Cost
                    │
Gamer ─ ISP ─ India Core
                    │
                    │ Higher OSPF Cost
                    │
                    └──── International Transit
                                │
                                ▼
                           Singapore DC
```

This encourages the routing protocol to select the local edge infrastructure when an appropriate route is available.

---

# 🧪 Model Development

The project follows a two-model comparative approach.

### Model 1

```text
Centralized Cloud Architecture
```

Users connect to a remote gaming server through the international network path.

### Model 2

```text
Edge Computing Architecture
```

Users connect to an Edge Gaming Server through a Modular Edge Data Center connected to the India Core.

The two architectures allow routing behavior and network paths to be compared under different server-placement strategies.

---

# ✅ Verification

Verification answers the question:

> **"Was the network model implemented correctly?"**

The simulation was verified by checking:

- Device configuration
- IP addressing
- Subnet configuration
- Gateway configuration
- OSPF routing
- Route propagation
- Routing tables
- End-to-end connectivity
- ICMP ping responses
- Packet forwarding
- Packet Tracer Simulation Mode

Successful packet delivery confirms logical connectivity between the simulated users and gaming infrastructure.

---

# 🔍 Validation

Validation answers the question:

> **"Does the simulation represent the intended network architecture?"**

The centralized model was validated by confirming the path:

```text
Gamer
→ Regional ISP
→ India Core
→ International Transit
→ Singapore Data Center
→ Gaming Server
```

The edge model was validated by confirming the optimized path:

```text
Gamer
→ Regional ISP
→ India Core
→ MDC
→ Edge Gaming Server
```

This confirms that the two simulations represent the intended centralized and edge-computing architectures.

---

# 📊 Results

The simulations demonstrate a clear difference in **network path structure** between the two architectures.

| Metric | Centralized Cloud | Edge + MDC |
|--------|-------------------|------------|
| Server Location | Singapore | Local Edge |
| Routing Distance | International | Localized |
| International Transit | Required | Avoided for edge traffic |
| Network Path | Longer | Shorter |
| Hop Count | Higher | Reduced |
| Simulated Latency | ~20 ms | ~10–15 ms |
| Scalability | Limited | Higher |
| Expected User Experience | Greater delay | Lower-latency path |

The edge architecture reduces routing layers and removes the need for international transit when traffic is served by the edge gaming server.

---

# ⚠️ Important Simulation Limitation

Cisco Packet Tracer is primarily a **network topology and protocol simulation tool**.

It does **not accurately simulate real-world geographical propagation delay**.

Therefore:

> **The latency values generated in Packet Tracer should not be interpreted as direct measurements of real-world India-to-Singapore network latency.**

Packet Tracer is useful in this study for evaluating:

- Network topology
- Routing behavior
- OSPF path selection
- Logical connectivity
- Packet forwarding
- Relative network complexity
- Hop reduction

However, geographical distance and real Internet conditions require additional experimentation using real-world networks or more advanced network simulation/emulation platforms.

---

# 📈 Key Findings

The simulation indicates that introducing edge infrastructure can:

- Reduce the number of routing layers between users and gaming servers.
- Avoid international transit for locally served gaming traffic.
- Provide a more direct network path.
- Allow routing protocols to prioritize nearby edge infrastructure.
- Reduce dependency on geographically distant centralized cloud infrastructure.
- Improve the architecture of latency-sensitive cloud gaming systems.

The primary demonstrated benefit of the Packet Tracer model is therefore **routing-path optimization and hop reduction**, rather than a precise prediction of real-world geographical latency.

---

# 🚀 Future Work

Future extensions of this project could include:

### Real-World Latency Measurements

Collect actual RTT measurements between Indian cities and cloud regions located in Singapore.

### Advanced Network Simulation

Reproduce the architecture using platforms such as:

```text
ns-3
Mininet
GNS3
EVE-NG
```

These tools could provide greater control over latency, bandwidth, jitter, and packet loss.

### Multiple Edge Locations

Instead of a single MDC, future simulations could introduce multiple edge locations across India.

For example:

```text
                ┌── Bangalore Edge
                │
                ├── Delhi Edge
Users ─ Core ───┼── Hyderabad Edge
                │
                └── Chennai Edge
```

### Intelligent Edge Selection

Future work could investigate dynamic edge-server selection based on:

- Latency
- Server load
- Network congestion
- Available bandwidth
- Geographic proximity
- User density

### AI-Based Routing

Machine-learning or reinforcement-learning techniques could potentially be used to dynamically select the most suitable edge infrastructure.

---

```

---

# ▶️ Running the Simulation

## Requirements

To open the simulation files, install **Cisco Packet Tracer**.

A recent version of Packet Tracer is recommended.

## Steps

1. Clone this repository:

```bash
git clone https://github.com/YOUR-USERNAME/cloud-gaming-edge-computing.git
```

2. Navigate to the repository:

```bash
cd cloud-gaming-edge-computing
```

3. Open Cisco Packet Tracer.

4. Open:

```text
packet-tracer/centralized-cloud/scenario-1-centralized-cloud.pkt
```

to examine the centralized architecture.

5. Open:

```text
packet-tracer/edge-mdc/scenario-2-edge-mdc.pkt
```

to examine the proposed Edge + MDC architecture.

6. Use **Simulation Mode** in Cisco Packet Tracer to inspect packet forwarding.

7. Examine router routing tables and OSPF routes to compare path selection between the two architectures.

---

# 🔬 Reproducing the Experiment

For each architecture:

1. Start the corresponding Packet Tracer simulation.
2. Verify all required interfaces are active.
3. Confirm OSPF routes have converged.
4. Verify the routing table.
5. Ping the appropriate gaming server from each gamer device.
6. Record connectivity and simulated RTT observations.
7. Use Simulation Mode to inspect the packet path.
8. Compare the centralized and edge architectures.

The primary comparison should focus on:

```text
Routing Path
Hop Count
Connectivity
OSPF Path Selection
Simulated RTT
```

---

# 📄 Research Paper

**Title:**  
*Optimizing Latency in Cloud Gaming Through Edge Computing and Micro Data Centers: A Simulation-Based Study*

**Author:**  
Akshat Raj

**Department:**  
Department of Computer Science  
CHRIST (Deemed to be University), Bangalore, India

> Publication information will be added once the paper is officially published.

---

# 📚 Selected References

The project builds on prior research examining network latency, Quality of Service, gaming experience, and server placement.

1. Chen, K.-T., Huang, P., and Lei, C.-L.,  
   *How Sensitive Are Online Gamers to Network Quality?*  
   ACM SIGCOMM Workshop, 2006.

2. Chen, K.-T., Huang, P., and Lei, C.-L.,  
   *On the Sensitivity of Online Game Playing Time to Network QoS.*  
   IEEE INFOCOM, 2006.

3. Degrande et al.,  
   *Managing Latency and Fairness in Networked Games.*  
   KU Leuven, 2006.

4. Zhao, Zheng, and Liu,  
   *Server Allocation for Massively Multiplayer Online Cloud Games Using Evolutionary Optimization.*  
   ACM Transactions on Multimedia Computing, Communications, and Applications, 2021.

For the complete bibliography, refer to the research paper included in this repository.

---

# 👨‍💻 Author

**Akshat Raj**

Computer Science Student  
CHRIST (Deemed to be University)  
Bangalore, India

Research interests include:

- Artificial Intelligence
- Large Language Models
- Agentic AI
- Computer Networks
- Edge Computing
- Cloud Computing

---

## ⭐ About This Repository

This repository contains the simulation artifacts associated with my research into the use of **Edge Computing and Modular Edge Data Centers for latency-sensitive cloud gaming networks**.

The repository is intended to make the network architecture, Packet Tracer simulations, routing configuration, and experimental methodology accessible for academic and educational purposes.

If you find the project useful, feel free to ⭐ the repository.

---

## 📜 License

This project is provided for **academic and educational purposes**.

The research paper and associated written material remain the intellectual work of the author.

For reuse of the simulation or code, please refer to the repository's `LICENSE` file.

---

<p align="center">
  <b>Built with Cisco Packet Tracer • OSPF • Edge Computing • Cloud Gaming</b>
</p>
