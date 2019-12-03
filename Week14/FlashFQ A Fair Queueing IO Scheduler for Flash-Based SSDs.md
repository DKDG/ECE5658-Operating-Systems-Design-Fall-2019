# FlashFQ: A Fair Queueing I/O Scheduler for Flash-Based SSDs [ATC '13]

### Motivation

* NAND flash ssd can be benefit from no-op scheduling because SSD can achieve fast I/O without mechanical seek/rotation delay. 
* However, the fairness is important in multi-task and multi-tenant systems.
  * In this system, heavy I/O operations can unfairly block light operations
* Existing fair I/O schedulers are mostly timeslice-based, so it may exhibit poor responsiveness, particularly when there are large number of co-running tasks.
  * Timeslice schedulers can't easily exploit device parallelism.

### Design

* Fair queueing resource scheduler
  * originated in network packet scheduling
  * Virtual time-based fairness
  * Management of under-utilizing tasks
* Restricted parallelism on Flash ==> start-time fair queuing with throttled dispatch
  * block a task if its resource usage is excessively ahead of the slowest task.

### Critique

* They did not consider JBD2 I/O context.