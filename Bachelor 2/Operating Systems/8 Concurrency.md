
## Chapter 1: Introduction to Concurrency
### Summary
- **Definition**: Concurrency ensures the coordinated functioning of multiple processes.
- **Problem**: Shared resources can result in incorrect program flow.
- **Key Challenges**:
  - **Starvation**: Processes are perpetually delayed.
  - **Deadlocks**: Two or more processes wait indefinitely for each other.

### Key Concepts
- **Critical Section (CS)**: A segment of code where shared resources are accessed.
- **Mutual Exclusion**: Ensures only one process enters the CS at a time.

---

## Chapter 2: Software-Based Solutions
### Summary
#### Bit per Critical Section
- Maintain a variable for each CS.
- Issues: Not atomic, busy waiting.

#### Dekker’s Algorithm
1. **1st Attempt**: Uses a turn variable to alternate access to the CS.
   - **Issue**: Faster processes get delayed.
2. **2nd Attempt**: Introduces flag variables for each process.
   - **Issue**: Both processes may enter the CS simultaneously.
3. **3rd Attempt**: Improves mutual exclusion but risks deadlock.
4. **4th Attempt**: Adds delays to prevent simultaneous entry.
   - **Issue**: Unbounded waiting time.
5. **Final Solution**: Combines flags and turn variable for courteous access.

#### Peterson’s Algorithm
- Announces desire to enter CS and assigns turns.
- Can be generalized for **n processes**.

---

## Chapter 3: Hardware-Based Solutions
### Summary
#### Characteristics
- **Prohibits interrupts** during CS execution.
  - Inefficient for large CS.
- **Machine Instruction Support** (e.g., Test-and-Set).
  - Issues: Busy waiting, potential starvation.

#### Semaphores
- **Definition**: A counter controlling access to resources.
- **Types**:
  1. **Counting Semaphores**: Tracks available resources.
  2. **Binary Semaphores**: Only 0 or 1 as values.

#### Semaphore Operations
1. **wait(s)**: Decrease count. Block if count is negative.
2. **signal(s)**: Increase count. Unblock if count becomes positive.

#### Mutual Exclusion Using Semaphores
- Semaphore initialized to 1 for each CS.
- Entering CS: `wait(s)`
- Exiting CS: `signal(s)`

---

## Chapter 4: Classical Problems
### Summary
#### Producers/Consumers Problem
- **Producer**: Generates data and writes to a buffer.
- **Consumer**: Reads data from the buffer.
- **Challenges**:
  - Ensure proper order of access.
  - Prevent simultaneous buffer access.
  - Prevent buffer underflow or overflow.

#### Readers/Writers Problem
- **Readers**: Multiple readers can access data simultaneously.
- **Writers**: Only one writer can access data, no readers allowed.

#### Solutions Using Semaphores
1. **Producers/Consumers**:
   - **Binary Semaphores**: Ensures exclusive access to buffer variables.
   - **Counting Semaphores**: Balances producers and consumers.
2. **Readers/Writers**:
   - Use counters and semaphores to manage access priorities.
   - Writers get exclusive access by blocking readers.

---

## Key Points to Remember
- **Concurrency Problems**:
  - Starvation and deadlocks can arise without proper coordination.
- **Software Solutions**:
  - Dekker's and Peterson’s algorithms provide mutual exclusion.
  - Peterson’s algorithm can handle multiple processes.
- **Hardware Solutions**:
  - Semaphores effectively manage resource access.
  - Binary semaphores are simple and powerful.
- **Classical Problems**:
  - Producers/Consumers and Readers/Writers demonstrate common concurrency challenges.
  - Semaphores provide structured solutions.

**Highlighted Terms**: Critical Section, Mutual Exclusion, Semaphore, Starvation, Deadlock, Test-and-Set, Binary Semaphore, Producers/Consumers Problem, Readers/Writers Problem.

