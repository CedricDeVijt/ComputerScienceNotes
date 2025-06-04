## REST architectures are characterized by several architectural constraints. Explain each of the following constraints and indicate why each of them is desirable. a) Client-server model, b) Caching and c) Layering

- **Client-Server Model**: Separates client (UI/requests) from server (data/processing). **Desirable**: Enhances scalability, simplifies server logic, and allows independent evolution of client and server.
- **Caching**: Stores responses to reduce server load and latency. **Desirable**: Improves performance, reduces network traffic, and enhances user experience.
- **Layering**: Organizes system into hierarchical layers with distinct roles. **Desirable**: Promotes separation of concerns, scalability, and flexibility while hiding complexity.

## Describe five ways in which REST resources are described from the point of view of REST URI design.

1. **Hierarchical Structure**: URIs reflect resource hierarchy (e.g., `/users/123/orders`).
2. **Resource-Based**: URIs identify resources, not actions (e.g., `/books` instead of `/getBooks`).
3. **Clear Naming**: Use meaningful, intuitive nouns (e.g., `/products` instead of `/items`).
4. **Consistency**: Uniform URI patterns across the API (e.g., `/users/{id}/profile`).
5. **Query Parameters**: Use for filtering/sorting (e.g., `/books?author=Smith`).
