# The Linux Scheduler: a Decade of Wasted Cores

* People have oversimplified that the Linux CFS scheduler solved the scheduling problem.

* However, the authors evaluated a number of scientific applications, kernel make, and TPC-H (databases) on multicore machines and found that threads were not allocated even though the core was idle.

* The authors developed their own debugging tools to find and fix the underlying fundamental bugs in the current Linux scheduler.

* The author's presentation slide has a picture that explains in detail the situation where the bug occurred.

* Four scheduling bugs
  * group imbalance bug: 
    * Balanced across cores, balanced across cpu groups, but in fact, one core may be idle.
    * In other words, this fundamental bug is inherent in the way the load balancing metrics are calculated.
    * Rather than comparing the average of loads between groups, rebalancing the load among idle cores by comparing the minimum values.
    * However,  minimum value can be volatile more often than the average, it is a temporary solution.
  * the scheduling group construction bug
    * Hierarchial load balancing (4-level): When the application was stuck on a node two hops away, a bug caused the load balancing algorithm to not migrate the threads between threads.
    * Build a domain by creating one "directly connected" group for all CPUs. In other words, the domain is established in a new way instead of the existing 4-level group way.
  * the overhead on wakeup bug
    * The original scheduling rational is that when a sleeping thread wakes up from its busy core again, thus it misses the opportunity to be passed to another idle core.
    * Solution: change the code that runs when the thread wakes up
  * the missing scheduling domains
    * When we turn on/off the cpu by using hotplugin, load balancing is not performed between NUMA nodes.
    * This bug seems to have been introduced by the Linux maintainer by mistake.

* The debugging tools they developed were open source on github. 

* The solution is simpler than we think, but the analysis to find scheduling bugs seems to have been very laborious.
