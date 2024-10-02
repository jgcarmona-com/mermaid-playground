# C4 Model: Context Diagram

Context diagrams provide an overview of the entire system and its interaction with external actors. They help in understanding the relationship between a system and its environment.

## Example of a Context Diagram
```mermaid
C4Context
    title System Context Diagram for Internet Banking System

    Enterprise_Boundary(b0, "BankBoundary0") {
        Person(customerA, "Banking Customer A", "A customer of the bank, with personal bank accounts.")
        Person(customerB, "Banking Customer B")
        System(SystemAA, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

        Enterprise_Boundary(b1, "BankBoundary") {
            SystemDb_Ext(SystemE, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")
            System_Ext(SystemC, "E-mail system", "The internal Microsoft Exchange e-mail system.")
        }
    }

    BiRel(customerA, SystemAA, "Uses")
    Rel(SystemAA, SystemC, "Sends emails to customers", "SMTP")
    Rel(SystemAA, SystemE, "Fetches core banking data", "HTTPS")

    UpdateElementStyle(customerA, $fontColor="white", $bgColor="#08427b")
    UpdateElementStyle(SystemAA, $bgColor="#1168bd")
    UpdateElementStyle(SystemE, $bgColor="#999999")
    UpdateRelStyle(SystemAA, SystemE, $textColor="blue", $lineColor="blue", $offsetX="5")
```