
#### Content for `sequence-diagram-basics.md`


# Sequence Diagram: Basic Concepts

Sequence diagrams illustrate how different objects interact in a given scenario of a system over time. They show the sequence of messages exchanged between various objects.

## Sequence Diagram: User Registration Flow
```mermaid
sequenceDiagram
    participant User
    participant RegistrationController
    participant RegistrationService
    participant Database

    User ->> RegistrationController: Submit Registration Form
    RegistrationController ->> RegistrationService: Validate and Register
    RegistrationService ->> Database: Save User Data
    Database -->> RegistrationService: Acknowledge
    RegistrationService -->> RegistrationController: Registration Success
    RegistrationController -->> User: Registration Confirmation
```
## Explanation

- User: Initiates the registration process by submitting a form.
- RegistrationController: Manages the user request and sends it to the service.
- RegistrationService: Validates and processes the registration.
- Database: Persists the user data.

This diagram shows a simple interaction for user registration. You can add more participants and messages as needed.

# Examples

## Users and MEssages
```mermaid
sequenceDiagram
    participant User
    participant Server
    User->>Server: Request Data
    Server-->>User: Send Data
    User-)Server: Acknowledge

```

## Alternatives and options with opt and alt 

```mermaid
sequenceDiagram
    participant Client
    participant API
    Client->>API: Request Account Balance
    alt Account Exists
        API-->>Client: Return Account Balance
    else Account Not Found
        API-->>Client: Error: Account Not Found
    end
    opt Additional Information Needed
        API->>Client: Request Additional Info
        Client-->>API: Send Additional Info
    end

```

# Loops
```mermaid
sequenceDiagram
    participant Sensor
    participant Monitor
    loop Every 5 Seconds
        Sensor->>Monitor: Send Temperature Data
        Monitor-->>Sensor: Acknowledge
    end

```

## Parallel Events
```mermaid
sequenceDiagram
    participant UserA
    participant UserB
    par UserA to Server
        UserA->>Server: Request A
    and UserB to Server
        UserB->>Server: Request B
    end
    Server-->>UserA: Response A
    Server-->>UserB: Response B

```

# Hihglight critial operations
```mermaid
sequenceDiagram
    participant Service
    participant Database
    critical Connect to DB
        Service->>Database: Establish Connection
    option Timeout
        Service->>Service: Log Error
    option Unauthorized
        Service->>Service: Retry Connection
    end

```


## Use 'break' to indicate interruptions 
```mermaid
sequenceDiagram
    participant User
    participant API
    participant PaymentService

    User->>API: Initiate Payment
    API->>PaymentService: Process Payment
    break Payment Failure
        API-->>User: Payment Failed
    end
    API-->>User: Payment Successful

```

## Use rect to group
```mermaid
sequenceDiagram
    participant Alice
    participant Bob

    %% A grey rectangle %%
    rect rgb(127, 127, 127) 
    Alice->>Bob: Hello Bob, how are you?
    Bob-->>Alice: Hi Alice, I'm good!
    end

```

## Use note to add notes
```mermaid
sequenceDiagram
    participant User
    participant System

    User->>System: Login Request
    Note right of System: Validate login credentials
    System-->>User: Login Success
    Note over User,System: User successfully authenticated

```

Many more examples at [Mermaid documentation - Squence Diagrams ](https://mermaid.js.org/syntax/sequenceDiagram.html)