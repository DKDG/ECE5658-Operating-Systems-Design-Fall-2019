# TxFS: Leveraging File-System Crash Consistency to Provide ACID Transactions [ATC '18]
### Motivation

- Existing techniques for collision consistency, such as logging or atomic rename, are accompanied by complex protocols and subtle bugs.
- Applications store persistent state across multiple files and abstractions.
- Efficient crash consistency is hard
  - POSIX only provides the sync-family system calls ==> fsync is an expensive call.
- In this work, the authors use the atomicity and durability provided by journal transactions and leverages them to build ACID transactions that are available in user space transactions.

### Design

- TxFS is a novel transactional file system that builds upon a file system's atomic-update mechanism such as journaling.
  - Simple API, portability across different hardware, high performance, low complexity, full ACID transactions
  - Develop techniques to isolate transactions
  - Simple API - one syscall to begin/end/abort a transaction

