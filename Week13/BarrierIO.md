# Barrier-Enabled IO Stack for Flash Storage [FAST '18]

### Motivation

* In the modern IO stack, the order in which application request IO requests is not guaranteed to be stored in storage.
* To guarantee storage order, there are many ways 
  * Database logging, file system journaling, soft-updates, COW-based file system
  * write() + fdatasync() incurs a huge overhead to host.
  * we cannot benefit from the fast storage device

### Design

* In this paper, they have developed barrier-enabled IO stack.
  * In the era of SSD, the host may control persist order and we can control the storage order without Transfer-and-Flush
* Barrier-enabled IO stack
  * BarrierFS
    * Dual-mode journaling
    * fbarrier(), fdatabarrier()
  * Order-preserving block device layer
    * Order-preserving dispatch
    * Epoch-based IO scheduling
  * Barrier-enabled Storage

### **critique**

* This paper targets only the storage device which has a single queue.
* It may be difficult to control order of each command in multi-queue storage device
* Barrier-enabled IO scheduler has conservative policy. 
  * It just opens and closes its queue on some time window.

