# C4 Model: Container Diagram

The **Container Diagram** provides a deeper view of the internal structure of the system by illustrating the main containers or components and their relationships. Containers can be applications, services, databases, or other subsystems.

```mermaid
C4Container
    title Container Diagram for Internet Banking System

    System_Ext(email_system, "E-Mail System", "The internal Microsoft Exchange system", $tags="v1.0")
    Person(customer, "Customer", "A customer of the bank, with personal bank accounts")

    Container_Boundary(c1, "Internet Banking System") {
        Container(spa, "Single-Page Application", "JavaScript, Angular", "Provides all the Internet banking functionality to customers via their web browser")
        ContainerDb(database, "Database", "SQL Database", "Stores user registration information, hashed auth credentials, access logs, etc.")
    }

    System_Ext(mainframe_system, "Mainframe Banking System", "Stores core banking information about customers, accounts, transactions, etc.")

    Rel(customer, spa, "Uses", "HTTPS")
    Rel(spa, database, "Reads/Writes", "JDBC")
    Rel(spa, email_system, "Sends emails using", "SMTP")
    Rel(spa, mainframe_system, "Fetches data", "HTTPS")
```