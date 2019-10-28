# Read Log Update [SOSP '15] 

## Motivation

* Multicore revolution => Need concurrent data-structures => new programming frameworks for concurrency
* The key to performance in concurrent data-structures
  * Unsynchronized traversals
    * 90% of the time is spent traversing data
  * Multi-location atomic updates
    * Hide race conditions from programmers
* RCU supports unsynchronized traversals but not multi-location atomic updates
  * - To modify objects: duplicate them and modify copies
      - provides unsynchronized traversals
    - To commit: use a a single pointer update to make new copies reachable and old copies unreachable
      - must happen all at once

## Design

* Read-Log-Update (RLU)
  * Simplifies RCU programming
  * Presevers RCU efficiency
* Idea
  * adds support for multi-pointer atomic updates
  * use a global clock and per thread logs
* RLU commit
  * P updates write clocks (more than global clock)
  * P executes RCU-epoch
    * Waits for Q to finish
  * P writes back log
  * P resets write clock
  * P swap logs (current log is safe for re-use after next commit)
* new API: rlu_try_lock()
  * To modify object => Lock it
  * Provide multi-location atomic updates
* List delete without a Mutext
  * Need custom post-lock validations
    * Ex) C.next == E, C is reachable from the head