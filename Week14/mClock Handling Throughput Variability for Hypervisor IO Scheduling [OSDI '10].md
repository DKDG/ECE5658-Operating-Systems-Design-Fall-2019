# mClock: Handling Throughput Variability for Hypervisor IO Scheduling [OSDI '10]
### Motivation

* Storage IO allocation is hard
  * Storage workload characteristics are variable
  * Available throughput changes with time
  * Must adjust allocation dynamically
  * Distributed shared access

### Design

* mClock supports proportional-shared fairness subject to minimum reservation and maximum limits on the IO allocations for VMs.
  * Rich QoS controls are quite effective in isolating VM performance and providing better application latency.
* Real-time tags
  * Needed for tracking reservations & limits
  * Virtual time loses track of actual allocation vs. time
* Separate tags for reservation, shares & limit
* Dynamic tag selection and synchronization
  * Need to decide which tag to use
  * Need to synchronize tags after idleness

### Critique

* It is still static mechanism to set R,L,S and other controls.
* There is not priority control along with RLS.