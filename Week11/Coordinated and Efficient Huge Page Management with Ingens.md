# Coordinated and Efficient Huge Page Management with Ingens [OSDI '16]

### Motivation 

* Just using default page handler for THP has some overheads
* Huge page is not a free lunch.
  * Synchronous allocations incur high page fault latency
  * Greedy allocation incurs memory bloating

### Solution

* Ingens
  * Asynchronous allocation => no extra page fault latency
  * Spatial utilization based allocation => bound memory bloating
  * Ingens overhead is negligible

### Limitation and Future works

* Ingens only supports huge page for anonymous page, but not for page cache.
  * Enabling THP to page cache incurs IO traffic.
* Ingen follows NUMA heuristic, but all of experiments in this paper evaluated on single NUMA node.