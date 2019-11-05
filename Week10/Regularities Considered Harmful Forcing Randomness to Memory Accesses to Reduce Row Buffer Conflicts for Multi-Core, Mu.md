# Regularities Considered Harmful: Forcing Randomness to Memory Accesses to Reduce Row Buffer Conflicts for Multi-Core, Multi-Bank [ASPLOS '13]
### Abstract

* The authors proposed a novel kernel-level memory allocator, called M^3 (M-cube, Multi)
* This paper rethink the memory allocation issue in light of these architectural trends.
  * They investigate how to alleviate row-buffer conflict issues from an operating system perspective so that memory can be allocated more efficiently.
* This tool's extensions allow the same application that accesses the page in any way to outperform the application that accesses the page in a regular pattern, such as sequential or the same order of access.

### Motivation

* Recently, multi-core support as exemplified by many CPU 
* Is it necessary to pre-charge even if there is no change in the cache?
  * Row-buffer conflict eliminates the caching effect and incurs more delays and energy consumption

### Contributions

* They have showed non-intuitive observations that random memory access patterns provide better performance than regular patterns in multicore and multibank systems.
* By designing M3, the concept of memory containers and randomization algorithms is designed to allow operating systems to randomize page frame access efficiently.
* They developed a tool that displays the mapping between page frames and memory components such as channels, ranks, and banks.