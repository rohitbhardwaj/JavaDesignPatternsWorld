Structural Design Patterns: Proxy Pattern
Objective
The Proxy Design Pattern acts as a surrogate or placeholder for another object, controlling access to it. This pattern is particularly useful for lazy loading, access control, caching, and logging/monitoring tasks. It provides a layer of control before the client interacts with the actual object.

Key Components
Subject:

An interface or abstract class shared by the RealSubject and Proxy.
Declares methods that the client can call.
RealSubject:

The actual object that contains the core logic or business operation.
Implements the Subject interface.
Proxy:

A placeholder or surrogate for the RealSubject.
Implements the Subject interface.
Adds additional logic (e.g., access control, lazy loading, logging) before delegating the request to the RealSubject.
When to Use Proxy Pattern
Lazy Loading:

Delay the creation of resource-intensive objects until they’re actually needed.
Access Control:

Enforce permissions or policies before allowing access to the RealSubject.
Caching:

Cache results or data to optimize repeated operations on the RealSubject.
Logging/Monitoring:

Track or log method calls without modifying the RealSubject.
Remote Access:

Represent objects located on different systems (Remote Proxy).
Implementation
Use Case:
A Database Proxy is used to control access to a database connection. The proxy provides logging, lazy loading, and access control.

1. Subject Interface
Define the common interface for the RealSubject and Proxy:

2. RealSubject
Implement the Database interface with the actual connection logic:

3. Proxy
Implement the Database interface with additional logic for lazy loading, logging, and access control:
4. Client
The client interacts with the Proxy instead of the RealSubject:


Output
plaintext
Copy code
Proxy: Logging connection request.
Connecting to the database...
Proxy: Logging query execution.
Executing query: SELECT * FROM users

Access denied: You do not have permission to connect.
Access denied: You do not have permission to execute queries.

