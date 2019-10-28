# The scalable commutativity rule: designing scalable software for multicore processors [SOSP '13]

### Abstract 

* People usually evaluate their software scalability to choose workload, plot performance at varying umbers of cores, and use tools to identify scalability bottlenecks.
  * However, the different workloads or higher core counts often exhibits new bottlenecks.
* There can be latent opportunity in interfaces, such as system call APIs
  * The real bottlenecks may be in the interface design
* Authors proposed the following rule: Whenever interface operations commute, they can be implemented in a way that scales.
* They argue that a set of operations scales if their implementations have conflict-free memory access, where no core writes a cache line that was read or written by another core.
* When operations commute, their results are independent of order
  * Therefore, communication between commutative operations is unnecessary.

### Contributions

* The scalable commutatively rule (SIM)
  * Formalization of the rule and proof of its correctness
  * State-dependent, interface-based commutativity
* Commuter: An automated scalability testing tool
* sv6: A scalable POSIX-like kernel

