# Efficient Virtual Memory for Big Memory Servers [ISCA '13]

### Motivation

* This paper showed that many big-memory server workloads (databses, in-memory caches and graph analytics) pay a high cost for page-based virtual memory.
  * They consume as mush as 10% of execution cycles on TLB misses.
* Since the late 1960s, paging formulation remains largely unchanged. However, virtual memory usage has changed dramatically.
  * Memory price has declined and 64-bit addressing can provide sufficient address space to applications.
* Big-memory workloads incur high virtual memory overheads due to TLB misses.
* In addition, these workloads seldom use the rich features of  page-based virtual memory (swapping, CoW and per-page protection).

### Solution

* Direct-segment software support for x86-64 in Linux and emulate direct-segment hardware.
  * It maps a large range of contiguous virtual memory address to contiguous physical memory addresses using small, fixed hardware: base, limit, and offset registers for each core.
  * paged VM as usual where needed, segmentation where possible
  * eliminate almost all TLB misses to large anonymous region.





