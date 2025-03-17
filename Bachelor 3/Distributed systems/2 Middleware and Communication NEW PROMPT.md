## 2.1 Middleware Fundamentals in Distributed Systems

### Core Characteristics of Middleware

**Middleware** acts as the "plumbing" connecting distributed components. Key features:

- Provides standardized communication patterns
- Abstracts network complexity (e.g., socket management)
- Enables focus on application logic rather than infrastructure

#### Four Defining Properties

1. **Invisibility**: Operates transparently beneath application layer
2. **Standardization**: Offers uniform APIs for common tasks
3. **Integration**: Binds heterogeneous system components
4. **Productivity Boost**: Handles cross-cutting concerns like marshalling

### Communication Building Blocks: Sockets

**Sockets** are OS-provided endpoints for inter-process communication.

#### Socket Programming Essentials

- **4-Tuple Identifier**: $\{ip_{src}, port_{src}, ip_{dst}, port_{dst}\}$
- Key Operations (Berkeley Sockets API):
  ```
  socket() → bind() → listen()/connect() → send()/receive() → close()
  ```
- Java Implementation:
  - Client: `Socket()` + I/O streams
  - Server: `ServerSocket()` with `accept()` blocking

### Remote vs Local Invocations

#### Local Method Execution

```java
// Within same JVM
object.add(5,3); → Direct memory access
```

#### Remote Method Challenges

```java
// Cross-machine execution
b.add(5,3); → Requires:
1. Argument marshalling
2. Network transport via middleware
3. Result unmarshalling
```

## 2.2 Remote Procedure Calls (RPC) Architecture

### RPC Components

#### Proxy (Client-Side)

- Mimics local object interface
- **Marshals** requests into network messages
- Example Flow:
  `Client call → Proxy → Request message → Network`

#### Skeleton (Server-Side)

- Unmarshals requests into method calls
- **Returns** results via reply messages
- Example Flow:
  `Network → Skeleton → Method invocation → Result marshalling`

### Marshalling/Unmarshalling

**Process**: Serialization/deserialization of objects to byte streams.

- **Standards**:
  - Java Serialization
  - Protocol Buffers (Google)
  - CORBA CDR

#### Data Representation Challenges

- Endianness (byte order)
- Platform-specific data types
- Versioning compatibility

## 2.3 Fault Tolerance & Invocation Semantics

### Failure Modes in RPC

- Client crashes before reply
- Duplicate requests from retries
- Network packet loss

### Invocation Guarantees

| Semantic          | Retry? | Duplicate Filter? | Execution Count     |
| ----------------- | ------ | ----------------- | ------------------- |
| **Maybe**         | No     | No                | 0 or 1 (unreliable) |
| **At-least-once** | Yes    | No                | ≥1                  |
| **At-most-once**  | Yes    | Yes               | ≤1                  |

#### Implementation Tactics

- **History Tables**: Store previous replies for retransmission
- **Unique Request IDs**: Detect duplicates

**Mnemonic (MAR)**:

- **M**aybe (No guarantees)
- **A**t-least-once (Assured execution)
- **R**obust At-most-once (Reliable)

## 2.4 Middleware Architecture Layers

### Core Components

1. **Communication Module**: Manages request-reply protocols
2. **Dispatcher**: Routes requests to correct skeletons
3. **Remote Reference Module**: Maintains object reference tables

#### Binding Service

- **DNS-like Resolution**: Maps logical names (e.g., "Adder") to remote references
- Registration Process:
  ```plaintext
  Server: register("Adder", objRef)
  Client: lookup("Adder") → Proxy creation
  ```

### Transparency vs Awareness

- **Hidden Aspects**:
  - Network location
  - Marshalling details
- **Exposed Aspects**:
  - Latency (async vs sync calls)
  - Potential failures (requires exception handling)

---

## Key Points to Remember

- **Middleware Role→Abstraction** ★★★★★

  - _Critical distinction_: Middleware hides network complexity but doesn't eliminate physical constraints like latency.

- **RPC Semantics→Fault Handling** ★★★★☆

  - _Pitfall_: At-least-once may execute duplicates; At-most-once requires state tracking.

- **Marshalling→Data Consistency** ★★★★☆

  - Use standardized formats (e.g., Protobuf) to avoid endianness/versioning issues.

- **Proxy/Skeleton Pattern→Location Transparency** ★★★★☆

  - Proxies mimic local objects; skeletons reverse the process on servers.

- **Socket Basics→4-Tuple Uniqueness** ★★★☆☆

  - Unique connection identifier: `\{ip_{src}, port_{src}, ip_{dst}, port_{dst}\}` [❓ Verify Context]

- **Binding Service→Naming Resolution** ★★★☆☆

  - Analogous to DNS but for distributed object references.

- **MAR Mnemonic→Invocation Semantics** ★★★★★
  - Remember Maybe/At-least/At-most guarantees using "MAR".
