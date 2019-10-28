# An Analysis of Linux Scalability to Many Cores [OSDI '10]
### Abstract

* The authors analyzes the scalability of seven system applications running on a 48 core AMD machine.
  * They figure out where is bottleneck on linux kernel and fix some code and make patches.
* They conclude that there is no scalability reason to give up on traditional operation system organizations just yet.

### Contribution

* Analysis of Linux scalability for 7 real apps
* Fixes: 3002 lines of code, 16 patches
  * no kernel problem up to 48 cores

### Method

* Run application
  * use in-memory file system to avoid disk bottleneck
* Find bottlenecks
* Fix bottlenecks, re-run application

### Bottleneck1: reading mount table

* Critical sections is short . Why does it cause a scalability bottleneck?
  * spin_lock and spin_unlock use many more cycles than the critical section
    * linux uses non-scalable ticket lock
      * previous lock holder notifies next lock holder after sending out N/2 replies
    * Many well known problem,
      * per-core mount caches (per-core data structure)
        * mount table is rarely modified
        * modify mount table: invalidate per-core tables

### Bottlneck2: reference counting

* Ref count indicates if kernel can free object
  * if ref count goes to zero, kernel is okay to free object
  * File name cache (dentry), physical pages
  * A single atomic instruction limits scalability
    * Reading the reference count is slow
    * Reading the reference count delays memory operations from other cores
      * contention on a reference count congests the interconnect
  * Solution: sloppy counters
    * kernel rarely needs true value of ref count

### Limitations 

* Results limited to 48 cores and small set of applications
* Looming problems
* In-memory FS instead of dis
* 48-core AMD machine, not single 48-core chip







