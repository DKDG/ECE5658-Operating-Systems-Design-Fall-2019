# Everything you always wanted to know about synchronization but were afraid to ask [SOSP '13]

Scalability of synchronization is key to application scalability

## Motivation

* What is the main source of scalability problem in synchronization?
  * Scalability of synchronization is mainly a property of the hardware

## Findings 

Opteron: incomplete directorty, Xeon: broadcast requests

* Crossing sockets is a killer
  * up to 8x more expensive communication
* Sharing within a socket is necessary but not sufficient
  * up to 3x more expensive communication
* Intra-socket uniformity matters
* Loads & store can be as expensive as atomic operations
  * 8-35% more expensive on non-locally cached data
* Simple locks are powerful 
  * better in 25 out of 32 data-points on a hash table
* Good synchronization in software might not scale as expected due to hardware

