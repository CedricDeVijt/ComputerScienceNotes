## 4.1 Foundations of Web Services

### Definition and Core Concepts

**Web Services** enable machine-to-machine interaction over networks using standardized formats (HTTP/XML/JSON). Key elements include interoperability, machine-processable interfaces (e.g., WSDL), and communication protocols like SOAP or REST.

#### Key Technologies

- **SOAP**: XML-based protocol for structured messaging.
- **REST**: Architectural style using HTTP methods (GET, POST, etc.) and URIs.
- **WSDL**: XML-based language for describing service endpoints.

### Service-Oriented Architectures (SOA)

SOA focuses on **loosely coupled, reusable services** (e.g., order processing, profile management). Applications consume services through a **service bus**, enabling integration across domains like retail or call centers.

## 4.2 RESTful Web Services

### Core Principles of REST

- **Resource-Centric Design**: Resources (e.g., products, users) are identified by URIs.
- **Stateless Communication**: Each request contains all necessary context.
- **Uniform Interface**: Standard HTTP methods (GET, POST, PUT, DELETE) for CRUD operations.

#### URI Design Best Practices

- Use **nouns** (e.g., `/employees/21` instead of `/getEmployee`).
- Ensure URIs are **predictable** and **hackable** (e.g., `/uantwerp/courses/` → `/computer-science`).
- Avoid verbs in URIs; reserve query parameters for filtering.

### HTTP Methods and CRUD

| HTTP Method | CRUD Action | Example Usage           |
| ----------- | ----------- | ----------------------- |
| GET         | Read        | Retrieve employee data  |
| POST        | Create      | Add new employee        |
| PUT         | Update      | Modify employee details |
| DELETE      | Delete      | Remove employee record  |

#### Case Study: Facebook Graph API

- Uses RESTful principles to query social media data via endpoints like `/me/friends`.
- Returns JSON format for easy parsing. ↗ See "JSON in REST" below.

### Architectural Constraints

1. **Client-Server Separation**: Decouples frontend and backend development.
2. **Statelessness**: No server-side session storage.
3. **Caching**: Improves performance via cacheable responses.
4. **Layered System**: Proxies/intermediaries enhance scalability.

## 4.3 SOAP Web Services

### Structure of SOAP Messages

- **Envelope**: Root element containing header and body.
- **Header**: Optional metadata (e.g., security credentials).
- **Body**: Core message content (e.g., method call parameters).

#### Example: Stock Price Request

```xml
<soap:Envelope>
  <soap:Body>
    <m:GetStockPrice>
      <m:StockName>IBM</m:StockName>
    </m:GetStockPrice>
  </soap:Body>
</soap:Envelope>
```

### WSDL (Web Services Description Language)

- Defines service endpoints, message formats, and protocols.
- Enables automatic code generation for clients/servers.

### SOAP Processing Model

- Messages traverse **intermediary nodes** (e.g., proxies, firewalls).
- Supports **WS-\* extensions** for security (WS-Security), transactions (WS-Transactions), and discovery (WS-Discovery).

## 4.4 REST vs. SOAP: Key Comparisons

### Advantages of REST

- **Lower Overhead**: No XML wrapping; uses lightweight JSON.
- **Scalability**: Statelessness and caching improve performance.
- **Flexibility**: Works with any data format (JSON, XML, etc.).

### When to Use SOAP

- **Enterprise Needs**: Requires WS-\* standards (e.g., encryption, transactions).
- **Formal Contracts**: WSDL provides strict service definitions.
- **Stateful Operations**: Complex workflows needing session persistence.

#### Case Study: Google Directions API

- RESTful service returning routing data in JSON/XML.
- Contrast with SOAP’s structured approach for B2B integrations.

---

## Key Points to Remember

- **Loose Coupling → Independence**: ★★★★☆
  Web services allow components to be modified without affecting others.
- **REST → HTTP Methods**: ★★★★☆
  CRUD operations map directly to GET, POST, PUT, DELETE.
- **SOAP → XML & WSDL**: ★★★☆☆
  Best for formal enterprise integrations needing extensibility.
- **Statelessness → Scalability**: ★★★★☆
  REST’s stateless design simplifies server-side management.
- **WS-\* Extensions → SOAP Strength**: ★★★☆☆
  Use SOAP for advanced security or transactional needs.
- **URI Design → REST Usability**: ★★★★☆
  Predictable URIs enhance API discoverability.
- **JSON vs. XML → Flexibility**: ★★★★☆
  JSON’s lightweight structure dominates modern REST APIs.
