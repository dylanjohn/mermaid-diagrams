```markdown
# Getting Started with Mermaid Diagrams

## Basic Flow Chart
```mermaid
graph TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Do Something]
    B -->|No| D[Do Nothing]
    C --> E[End]
    D --> E
```

## Basic Sequence Diagram
```mermaid
sequenceDiagram
    participant A as Alice
    participant B as Bob
    A->>B: Hello Bob!
    B->>A: Hi Alice!
```

## Basic Entity Relationship
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ ITEM : contains
```

## Usage Instructions
1. Each diagram begins with \```mermaid
2. Follow with the diagram type (graph, sequenceDiagram, etc.)
3. Add your diagram content
4. End with \```

## Common Types
- flowchart TD (top-down)
- sequenceDiagram
- erDiagram
- classDiagram
- gantt
- pie
```