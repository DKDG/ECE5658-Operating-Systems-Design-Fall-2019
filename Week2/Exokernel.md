# Exokernel: An Operating System Architecture for Application-Level Resource Management

* In this paper, instead of a traditional monolithic kernel like Unix, the authors proposed a prototype operating system called exokernel that can securely exploit machine resources.
* The exokernel was motivated to design by following simple reasons.
  * In traditional operating systems, applications were generally considered untrusted and did not have permission to change the abstraction interface.
  * It is not recommended to modify specific abstraction layers with hardcoding to accelerate application performance.
* The three techniques described below are used by the exokernel to safely export resources.
  * secure bindings
  * visible source revocation
  * abort protocol
* The application implemented in the exokernel is called libOS, which can request and utilize resources from the exokernel, such as virtual memory  and disk blocks, through low-level APIs.
  * To this end, it can achieve performance, flexibility and extensibility.

![exokernel_overview](D:\ECE5658-Operating-Systems-Design-Fall-2019\Week2\exokernel_overview.PNG)