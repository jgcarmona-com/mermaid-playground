# Component Diagrams: Basic Concepts

Component diagrams are used to show the structure of a software system, including how components are connected and interact with each other.

## Component Diagram: E-commerce Application

```mermaid
%% Defining a basic component diagram for an e-commerce system.
%% Components include User Service, Order Service, and Payment Service.

graph TD
    subgraph Frontend[Frontend]
    F1[Web Application]
    F2[Mobile Application]
    end

    subgraph Backend[Backend]
    US[User Service]
    OS[Order Service]
    PS[Payment Service]
    DB[(Database)]
    end

    F1 -- "Requests" --> US
    F2 -- "Requests" --> US
    US -- "Manages Users" --> DB
    OS -- "Processes Orders" --> DB
    PS -- "Handles Payments" --> DB
    US -- "Calls" --> OS
    OS -- "Calls" --> PS
```

## Explanation

- **Web Application and Mobile Application:** Represent the frontend systems where users interact.
- **User Service:** Manages user-related data.
- **Order Service:** Processes user orders.
- **Payment Service:** Manages payment processing.
- **Database:** Central storage for all services.

Use component diagrams to better understand the internal structure and dependencies of your system.