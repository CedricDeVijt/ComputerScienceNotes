## 2.1 Introduction to Middleware

### Definition and Role

- Middleware acts as the "plumbing" of distributed systems, providing a standard way to connect components.
- Key roles:
  - Invisible infrastructure for communication.
  - Simplifies complex system integration.
  - Allows developers to focus on core tasks.

### Core Characteristics

1. Standardizes communication.
2. Abstracts network complexity.
3. Supports interoperability across heterogeneous systems.

## 2.2 Basic Communication with Sockets

### Socket Fundamentals

- **Socket pairs**: Defined by a 4-tuple: `{ip_src, port_src, ip_dst, port_dst}`.
- **Socket API**:
  - `socket()`, `bind()`, `listen()`, `accept()`, `connect()`, `send()`, `receive()`, `close()`.
- Enables inter-process communication (IPC) over a network.

### Java Socket Example

- **Client**: Connects to a server, sends requests, and reads responses.
- **Server**: Listens for connections, processes requests, and returns responses.

## 2.3 Remote Invocation and RPC

### Remote Procedure Calls (RPC)

- Enables calling methods on remote machines as if they were local.
- **Components**:
  - **Client stub**: Marshals requests.
  - **Server skeleton**: Unmarshals requests and invokes methods.
- **Steps**:
  1. Convert arguments to a bitstream (marshalling).
  2. Transmit over the network.
  3. Unmarshal and execute remotely.
  4. Return results to the client.

### Challenges

- Argument serialization.
- Network latency and fault handling.

## 2.4 Middleware Architecture Components

### Proxy and Skeleton

- **Proxy**: Acts as a local object for the client, forwards requests to the remote object.
- **Skeleton**: Receives requests, invokes methods on the server, and returns results.

### Marshalling

- Converts objects to bitstreams for transmission.
- Standards: CORBA CDR, Java Serialization, Protocol Buffers.

### Communication Module

- Implements request-reply protocols.
- Manages sockets and ensures invocation semantics.

### Dispatcher and Remote Reference Module

- **Dispatcher**: Routes requests to the correct skeleton.
- **Remote Reference Module**: Maps local proxies to remote objects and vice versa.

## 2.5 Fault Tolerance and Invocation Semantics

### Failure Modes in RPC

- Client/server crashes, message loss, duplicates.

### Invocation Semantics

| Semantics         | Fault Tolerance Measures          | Execution Guarantee     |
| ----------------- | --------------------------------- | ----------------------- |
| **Maybe**         | None                              | No guarantees           |
| **At-least-once** | Retransmit requests, no filtering | Method executed ≥1 time |
| **At-most-once**  | Retransmit + duplicate filtering  | Method executed ≤1 time |

### Techniques

- Retry requests, duplicate filtering, re-execute or retransmit results.

## 2.6 Remote Objects and References

### Remote Object Characteristics

- **Remote Interface**: Defines methods accessible remotely (e.g., via IDL).
- **Remote Object Reference**: Globally unique identifier containing:
  - IP address, port, creation time, object number, interface type.

### Local vs. Remote Invocation

- **Local**: Direct method calls within the same address space.
- **Remote**: Limited to remote interface methods; requires middleware.

## 2.7 Binding Services and IDL

### Binding Service

- Resolves remote object references (e.g., DNS for RPC).
- **Options**:
  1. Direct server contact.
  2. Centralized binding service (e.g., dictionary).

### Interface Definition Language (IDL)

- Generates proxies, skeletons, and dispatchers automatically.
- Examples: Java RMI, Apache Thrift.

## 2.8 Example Workflow: Remote Addition

### Steps

1. Define remote interface (IDL).
2. Implement methods on the server.
3. Middleware generates proxies and skeletons.
4. Client invokes `remote.add(2,5)`.
5. Proxy marshals request, sends via sockets.
6. Server skeleton unmarshals, executes method, returns result.

## Key Points to Remember

- **Middleware** abstracts network complexity, enabling transparent communication.
- **Sockets** are the foundation for basic IPC (APIs: `bind`, `listen`, `accept`).
- **RPC/RMI** rely on proxies (client) and skeletons (server) for remote method execution.
- **Marshalling** converts data for transmission; standards include Protocol Buffers.
- **Invocation Semantics**:
  - _At-least-once_: Retries without duplication checks.
  - _At-most-once_: Ensures no duplicate executions.
- **Remote References** uniquely identify objects globally (IP, port, creation time).
- **Binding Services** resolve object references (e.g., centralized directory).
- **IDL** generates middleware components automatically, reducing boilerplate code.
