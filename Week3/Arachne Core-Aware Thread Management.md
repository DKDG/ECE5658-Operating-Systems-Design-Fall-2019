# Arachne: Core-Aware Thread Management

* Motivation:
  * Recently, data centers are using  modern high-performance hardware, and services that provide low latency are being introduced.
  *  Theoretically, applications that require low-latency and high-throughput can run simultaneously in one machine.
  * However, since the application uses a physical resource as a virtual resource called a thread, if the two kinds of applications run at the same time, the performance of the low latency application is hampered because internal resource parallelism cannot be maintained.
* Solution: Arachne
  * Application can have visibility to be aware physical core.
  * Appropriate algorithms to estimate how much core per-application requires.
  * Per-application core management policy
  * Minimize cache miss
* Future work
  * Authors believe that Arachne can be expolited on VM. 
    * Hypervisor would know guest machines requirements so it can allocate host machine's physical core.
  * Their mechanism would be also implemented on cluster scheduling algorithm.
    * For exmaple, Yarn scheduler would aggressively run background application not being fear of impacting foreground's latency.
