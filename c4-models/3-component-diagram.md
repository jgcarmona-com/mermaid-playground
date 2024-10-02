# C4 Model: Component Diagram

The **Component Diagram** provides an in-depth view of a single container, breaking it down into individual components and their interactions. Components typically include classes, services, and other logical units within a container.

```mermaid
C4Component
    title Component Diagram for Internet Banking System - API Application

    Container_Boundary(api, "API Application") {
        Component(signin, "Sign In Controller", "Spring MVC Rest Controller", "Allows users to sign in to the Internet Banking System")
        Component(accounts, "Accounts Summary Controller", "Spring MVC Rest Controller", "Provides customers with a summary of their bank accounts")
        Component(security, "Security Component", "Spring Bean", "Handles authentication and authorization")
    }

    SystemDb(database, "Database", "Relational Database", "Stores user registration information and transaction logs")

    Rel(signin, security, "Uses")
    Rel(accounts, database, "Reads/Writes data", "JDBC")
    Rel(security, database, "Reads/Writes auth data", "JDBC")
```