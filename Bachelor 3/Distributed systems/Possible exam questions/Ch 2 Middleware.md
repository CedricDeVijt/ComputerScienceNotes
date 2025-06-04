## Indicate the main differences between Local Method Invocation and Remote Method Invocations from the point of view of the used reference, the access and the number of invocations that are required by the client machine (invoker).

- **Used Reference**:

  - Local: Direct reference to the object in the same address space.
  - Remote: Reference to a remote object via a stub/proxy over a network.

- **Access**:

  - Local: Direct memory access, faster, within the same process.
  - Remote: Network-based access, slower, involves serialization/deserialization.

- **Number of Invocations**:
  - Local: Single direct call to the method.
  - Remote: Multiple steps (client to stub, network, server skeleton, object), typically one client invocation triggers multiple underlying network calls.

## Indicate what is the role of the Proxy on the Remote Method Invocation process. Indicate how the Proxy and the Skeleton are related.

The proxy (stub) acts as a local representative of the remote object, handling communication by serializing method calls, sending them over the network, and receiving responses.

**Proxy and Skeleton Relationship**:

- The proxy (client-side stub) marshals client requests and sends them to the skeleton (server-side). The skeleton unmarshals requests, invokes the actual method on the remote object, and sends results back to the proxy. They work together to enable transparent remote communication.
