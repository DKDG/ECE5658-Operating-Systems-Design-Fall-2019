# Traffic Management: A Holistic Approach to Memory Placement on NUMA Systems [ASPLOS '13]

### Abstract

- Modern NUMA hardware has much smaller remote wire delays, and so remote access costs are not the main concerns.
- Rather, congestion on memory controllers and interconnects, caused by memory traffic from data-intensive applications, hurts performance a lot more.

### Motivation

- Previous works mainly focused on NUMA-aware memory placement, that is, placing memory pages such that data accesses are satisfied from a local node whenever possible
  - These methods was done to avoid high costs of remote memory accesses.
- In this work, They addressed that congestion on interconnect link and in memory controllers, which results from high volume of data flood across the system, can dramatically hurt performance.
  - Thus, they proposed the design of new NUMA-aware memory placement policies.

### Solution

- Carrefour: a memory traffic management algorithm
  - Balance memory pressure on interconnect and MC and improve locality
  - Mechanisms
    - Page co-location: co-locations works well.
    - Page interleaving: evenly distributing physical pages across nodes.
    - Page replication: placing a copy of a page on several memory nodes.

