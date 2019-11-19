# All File Systems Are Not Created Equal: On the Complexity of Crafting Crash-Consistent Applications [OSDI '14]
### Motivation

* Most file systems provide a crash consistency mechanism that is underspecified and unclear.
* It is not easy to define a crash-consistent updated protocol for high performance applications.
* In this paper, the authors deeply analyze file system operations in terms of atomic behavior and ordering and application's crash consistency protocols.

### Design

* BOB (Block Order Breaker)
  * BOB collects block-level traces under the file system and reverses them to look for possible disk crash conditions.
  * BOB can find failures but can’t prove their absence.
* ALICE: Application-level crash consistency protocol checker
  * Alice's insight is that no matter how complex the application source code, the update protocol boils down to a sequence of file-system related system calls.
  * It produces protocol diagrams
  * If application has specific file system persistence property, we can call that application has crash vulnerability.



