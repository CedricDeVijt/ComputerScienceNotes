## The Reactive Manifesto is characterized by four architectural traits. Describe each of these traits and indicate their importance.

1. **Responsive**: Ensures timely responses to users, critical for user satisfaction and system reliability.
2. **Resilient**: Systems stay operational during failures through replication and isolation, vital for fault tolerance.
3. **Elastic**: Scales dynamically with demand, essential for handling variable workloads efficiently.
4. **Message-Driven**: Uses asynchronous messaging for loose coupling, improving scalability and resilience.

## Indicate why containers are considered a preferable solution over virtual machines (VM) for the implementations of microservices. Indicate at least one advantages and one disadvantage of using containers.

- **Why Preferable**: Containers are lightweight, share the host OS, and start faster, enabling efficient scaling and deployment.
- **Advantage**: Reduced resource overhead compared to VMs, allowing more services on the same hardware.
- **Disadvantage**: Weaker isolation than VMs, potentially increasing security risks.
