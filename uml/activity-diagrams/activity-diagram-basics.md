# Activity Diagram: Basic Concepts

Activity diagrams are used to describe the flow of control in a system, showing how different activities are coordinated.

# NOTE:
Mermaid does not have a specific type of diagram for representing activity diagrams exactly as defined in UML. However, it is possible to approximate activity diagrams using Mermaid's `flowchart` syntax to represent the flow of control. Some UML-specific elements like "decision nodes," "forks," and "swimlanes" may not be supported directly or may require creative workarounds.


## Activity Diagram: Order Fulfillment Process
```mermaid
graph TD;
    A[Start] --> B[Order Placed]
    B --> C{In Stock?}
    C -->|Yes| D[Prepare Order]
    C -->|No| E[Notify Customer]
    D --> F[Ship Order]
    F --> G[End]
    E --> G[End]
```   
## Explanation

- Order Placed: The process starts when an order is placed.
- In Stock?: Checks if the item is available.
- Prepare Order: Prepares the order for shipping if in stock.
- Notify Customer: Notifies the customer if the item is out of stock.
- Ship Order: Ships the order and ends the process.

This diagram is useful for visualizing a decision-making process.

# Activity Diagram: Advanced Concepts

Activity diagrams can also include additional elements like entry/exit points, forks, and joins. Here's an example demonstrating these concepts:

## Activity Diagram: E-commerce Order Process with Forks and Joins
```mermaid
graph TB;
    %% Define entry point
    Start --> A[User Browses Products]
    A --> B{Product Selected?}
    B -- Yes --> C[Add to Cart]
    B -- No --> A

    %% Decision and merge nodes
    C --> D[Checkout]
    D --> E{Logged In?}
    E -- No --> F[Redirect to Login]
    F --> G[User Logs In] --> E

    %% Fork and Join
    E -- Yes --> H{Payment Method Selected?}
    H -- Yes --> I[Proceed to Payment]
    H -- No --> J[Select Payment Method]
    I --> K[Process Payment]

    %% End nodes
    K --> L[Order Confirmed]
    L --> End[Process Complete]
```

## Explanation
- **Start:** Represents the initial state of the process.
- **Product Selected?:** Decision node to check if a product is selected.
- **Fork:** Payment processing steps occur in parallel (omitted here for simplicity).
- **End:** Represents the final state of the process.

## Key Concepts Included:
1. Entry/Exit Points: Represented using the "Start" and "End" nodes.
1. Decision Nodes: Used for branching the flow based on conditions (Yes/No paths).
1. Fork and Join: Can be simulated by breaking the flow into parallel branches using separate paths.



## Alternatives to Decision Nodes and Forks in Mermaid
Although Mermaid does not have direct support for elements such as decision nodes or branching points that are standard in UML diagrams, diamond nodes or conditional text labels can be used to simulate them.

```mermaid
graph TD;
    Start --> A[Initial State]
    A --> B{Is User Authenticated?}
    B -- Yes --> C[Access Granted]
    B -- No --> D[Access Denied]
    D --> E[Request Authentication]
    E --> B

    C --> F[Final State]

```

## Adding Entry and Exit Nodes to Activity Diagrams in Mermaid
If you want to add explicit entry and exit points, you can use the following conventions in Mermaid:
```mermaid
graph LR;
%% Here LR means from Left to Right %%
Input[Entry Point] --> A[User Authentication]
A --> B[Check Permissions]
B --> C{Access Granted?}
C -- Yes --> D[Load Dashboard]
C -- No --> E[Show Access Denied Message]
E --> F[Exit Point]
D --> F
```

# Explaining Algorithms with Activity Diagrams
When we want to explain algorithms like Quicksort or Backtracking, Activity  and Sequence Diagrams can be used to illustrate the flow of an algorithm effectively. Below is an explanation of these two well-known algorithms with its respective activity diagram representation:

## 1. Quicksort Algorithm
Description: Quicksort is a divide-and-conquer sorting algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

### Step-by-Step Explanation:

1. Choose a pivot element from the array.
1. Partition the array into two sub-arrays: elements less than the pivot and 1. elements greater than the pivot.
1. Recursively apply the same steps to each sub-array.
1. Combine the sub-arrays and the pivot to get the sorted array.

### Best Diagram for Quicksort:

**Activity Diagram:** It can represent the flow of the sorting process.

```mermaid
graph TD;
    A[Start] --> B{Is Array Empty or One Element?}
    B -->|Yes| C[Return]
    B -->|No| D[Choose Pivot]
    D --> E[Partition Array]
    E --> F[Quicksort Left Sub-array]
    F --> G[Quicksort Right Sub-array]
    G --> H[Combine Sub-arrays]
    H --> I[Return Sorted Array]
    I --> J[End]
```

#### Explanation
- Start: Start of the Quicksort process.
- Is Array Empty or One Element?: Base condition to stop the recursion.
- Choose Pivot: Select a pivot to divide the list.
- Partition Array: Separation of elements smaller and larger than the pivot.
- Quicksort Left/Right Sub-array: Recursive calls to Quicksort on the sub-arrays.
- Combine Sub-arrays: Unification of the results of the recursive calls.
- Return Sorted Array: Return of the sorted array.

**Sequence Diagram:** It can show the interaction between recursive calls.

```mermaid
sequenceDiagram
    participant Main
    participant Quicksort
    participant Partition
    participant SubArray1
    participant SubArray2

    Main->>Quicksort: Call quicksort(array)
    loop While array has more than one element
        Quicksort->>Partition: Select pivot and partition array
        Partition-->>Quicksort: Return left and right sub-arrays
        Quicksort->>SubArray1: Call quicksort(left sub-array)
        SubArray1-->>Quicksort: Return sorted left sub-array
        Quicksort->>SubArray2: Call quicksort(right sub-array)
        SubArray2-->>Quicksort: Return sorted right sub-array
    end
    Quicksort-->>Main: Return sorted array
```

#### Explanation
The loop shows that the quicksort function is called recursively as long as the array has more than one element. Each call partitions the array into left and right sub-arrays, which are also recursively sorted.

## 2. Backtracking Algorithm
Description: Backtracking is an algorithmic paradigm used to solve constraint satisfaction problems, such as Sudoku, N-Queens, and other puzzles. It incrementally builds a solution and removes those solutions that fail to satisfy the constraints.

### Step-by-Step Explanation:

Start with an empty solution.
Add an element to the solution if it doesn't violate the constraints.
If the constraints are violated, backtrack and remove the last added element.
Continue this process until all constraints are satisfied or all options are exhausted.

### Best Diagram for Backtracking:

**Activity Diagram:** It can represent the branching and backtracking flow.

```mermaid
graph TD
    A[Start Backtracking] --> B[Check Constraints]
    B -->|Fail| C[Backtrack]
    B -->|Succeed| D[Add to Solution]
    D --> E{Solution Complete?}
    E -->|Yes| F[Return Solution]
    E -->|No| G[Move to Next Option]
    G --> B
```


**Sequence Diagram:** It can show the sequence of choices and backtracking steps.

```mermaid
sequenceDiagram
    participant Main
    participant Backtrack
    participant CheckConstraints
    participant Solution

    Main->>Backtrack: Start backtracking()
    loop For each option in set
        Backtrack->>CheckConstraints: Check current solution constraints
        alt Constraints satisfied
            Backtrack->>Solution: Add option to solution
            Backtrack->>CheckConstraints: Check constraints for updated solution
        else Constraints violated
            Backtrack->>Solution: Remove last option (backtrack)
        end
    end
    Backtrack-->>Main: Return solution if complete
```

#### Explanation
The loop indicates that backtracking iterates over each option in a set, checking constraints, adding or removing options based on whether the constraints are satisfied or violated, and continuing until a complete solution is found.