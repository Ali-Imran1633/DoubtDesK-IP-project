# DoubtDesk Diagrams

You can preview this file directly in VS Code by right-clicking the file tab and selecting **"Open Preview"** (or press `Ctrl+Shift+V`).

## 1. Architecture & Data Flow Diagram

```mermaid
flowchart LR
    Client([Client Browser / User])
    
    subgraph Frontend [Frontend Application]
        React[React.js + Vite\nPort: 5173]
    end
    
    subgraph Backend [Backend API Server]
        Node[Node.js + Express\nPort: 3001]
    end
    
    subgraph Database Layer
        DB[(SQLite Database\nSequelize ORM)]
    end

    Client -->|1. User Interactions| React
    React -->|6. UI Updates| Client
    
    React -->|2. HTTP API Requests| Node
    Node -->|5. JSON Responses| React
    
    Node -->|3. SQL Queries| DB
    DB -->|4. Query Results| Node

    classDef default fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef client fill:#dae8fc,stroke:#6c8ebf,stroke-width:2px;
    classDef frontend fill:#d5e8d4,stroke:#82b366,stroke-width:2px;
    classDef backend fill:#ffe6cc,stroke:#d79b00,stroke-width:2px;
    classDef db fill:#e1d5e7,stroke:#9673a6,stroke-width:2px;
    
    class Client client;
    class React frontend;
    class Node backend;
    class DB db;
```

---

## 2. Use Case Diagram

```mermaid
flowchart LR
    %% Actors
    Student((Student))
    Teacher((Teacher))
    Admin((Admin))

    %% System Boundary
    subgraph DoubtDesk Platform
        direction TB
        UC1([Register / Login])
        UC2([Enroll in Course])
        UC3([Ask a Question])
        UC4([View My Questions])
        
        UC5([View Pending Questions])
        UC6([Provide Solution])
        UC7([Track Solved Count])
        
        UC8([Manage Users])
        UC9([Manage Courses])
    end

    %% Student Relationships
    Student --> UC1
    Student --> UC2
    Student --> UC3
    Student --> UC4

    %% Teacher Relationships
    Teacher --> UC1
    Teacher --> UC5
    Teacher --> UC6
    Teacher --> UC7

    %% Admin Relationships
    Admin --> UC1
    Admin --> UC8
    Admin --> UC9

    classDef actor fill:#f8cecc,stroke:#b85450,stroke-width:2px;
    classDef usecase fill:#fff2cc,stroke:#d6b656,stroke-width:2px;
    
    class Student,Teacher,Admin actor;
    class UC1,UC2,UC3,UC4,UC5,UC6,UC7,UC8,UC9 usecase;
```
