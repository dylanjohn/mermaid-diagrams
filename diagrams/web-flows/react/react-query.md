```mermaid
sequenceDiagram
    participant User
    participant Component as React Component
    participant Query as React Query
    participant API as API Service
    participant Server
    participant DB as Database

    User->>Component: Interact (load page, click button)
    Component->>Query: useQuery/useMutation
    
    alt Data Fetch
        Query->>Query: Check cache first
        
        alt Cache Miss or Stale Data
            Query->>API: Request data
            API->>Server: HTTP Request (GET/POST/PUT/DELETE)
            Server->>DB: Database operation
            DB-->>Server: Return data
            Server-->>API: HTTP Response
            API-->>Query: Return data
            Query-->>Query: Update cache
            Query-->>Component: Return data
        else Cache Hit (Fresh)
            Query-->>Component: Return cached data
        end
    end
    
    Component-->>User: Render UI with data
    
    User->>Component: Trigger mutation (create/update)
    Component->>Query: useMutation
    Query->>API: Send mutation
    API->>Server: HTTP Request
    Server->>DB: Update database
    DB-->>Server: Confirm update
    Server-->>API: Success response
    API-->>Query: Return result
    Query-->>Query: Invalidate related queries
    Query-->>Component: Trigger refetch
    Component-->>User: Update UI
