## Indicate the difference between the different types of multi-tenancy.

**Data Multi-Tenancy:**

- **Description:** In data multi-tenancy, multiple tenants share the same database schema but have separate data partitions. Each tenant's data is isolated, ensuring security and privacy.
- **Example:** A SaaS application where each tenant's data is stored in the same database but in different tables or with tenant identifiers.
- **Use Case:** Common in applications where data isolation is crucial, such as CRM systems.

**Application Multi-Tenancy:**

- **Description:** In application multi-tenancy, multiple tenants share the same application instance and codebase. Each tenant's configuration and data are isolated, but they run on the same software environment.
- **Example:** A web application where multiple organizations use the same codebase but have different configurations and user interfaces.
- **Use Case:** Common in SaaS applications where cost efficiency and resource sharing are prioritized, such as email services.

## List and describe the three service models commonly used in cloud computing. Provide an example of a service following each of the three models.

**B) Three Service Models in Cloud Computing:**

1. **Infrastructure as a Service (IaaS):**
   - **Description:** Provides virtualized computing resources (servers, storage, networking) over the internet. Users manage OS, applications, and data.
   - **Example:** Amazon Web Services (AWS) EC2.
2. **Platform as a Service (PaaS):**
   - **Description:** Offers a platform allowing users to develop, run, and manage applications without managing underlying infrastructure.
   - **Example:** Google App Engine.
3. **Software as a Service (SaaS):**
   - **Description:** Delivers software applications over the internet, fully managed by the provider. Users access via subscription.
   - **Example:** Microsoft Office 365.
