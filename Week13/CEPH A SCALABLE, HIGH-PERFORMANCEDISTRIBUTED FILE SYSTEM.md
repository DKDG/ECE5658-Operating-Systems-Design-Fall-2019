# **CEPH: A SCALABLE, HIGH-PERFORMANCEDISTRIBUTED FILE SYSTEM [OSDI '06]**
### Motivation

* System designers have long sought to improve the performance of file systems, which have proved critical to the overall performance of an exceedingly broad class of applications.
* Although widely used, the centralization inherent in the client/server model has proven a significant obstacle to scalable performance.
* NFS is widely used, but the centralization inherent in the client / server model has proven to be a significant obstacle to scalable performance.

### Design

* Ceph maximizes the separation between data and metadata management by replacing allocation tables with a pseudo-random data distribution function (CRUSH) designed for heterogeneous and dynamic clusters of unreliable object storage devices (OSDs).
  * open source software defined storage
  * unified storage platform (block, object and file storage)
  * no single point of failure

###  Critique

* Ten years of building on local file systems
* Need to consider and support modern hardware (e.g., 40G, NVMe SSDs)