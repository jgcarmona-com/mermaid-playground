# C4 Model: Code Diagram

The **Code Diagram** provides the lowest-level view of the system's design, focusing on the class structure and their relationships. It represents the implementation details of components.

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +Account account
        +login()
        +logout()
    }

    class Account {
        +int id
        +double balance
        +deposit(amount)
        +withdraw(amount)
    }

    class Transaction {
        +int transactionId
        +string type
        +double amount
        +execute()
    }

    User --> Account : Has
    Account --> Transaction : Executes
    Transaction --> Account : Modifies
```

At this level any diagram is allowed, and probably welcome. I'd go for UML or UML-like diagrams (i.e.: a combination of componetns and itneraction diagrams)