```markdown
# Contributing Guidelines

## Diagram Structure
```mermaid
graph TD
    A[Create Branch] -->|feature/diagram-name| B[Add Diagram]
    B --> C[Add Documentation]
    C --> D[Create PR]
    D --> E{Review Process}
    E -->|Approved| F[Merge]
    E -->|Changes Requested| B
```

## Folder Structure
```mermaid
graph TD
    root[mermaid-diagrams] --> diagrams
    root --> docs
    diagrams --> cat1[web-flows]
    diagrams --> cat2[system-architecture]
    diagrams --> cat3[database-schemas]
    diagrams --> cat4[sequence-diagrams]
```

## File Format
Each diagram file should include:
1. Title and description
2. The Mermaid diagram code
3. Usage examples
4. Related diagrams
```