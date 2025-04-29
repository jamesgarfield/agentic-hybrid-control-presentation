# SVG Diagram Reference

This file documents the SVG diagrams used in the presentation. All diagrams have been pre-generated as static SVG files and are displayed in the slides/main.md file.

## 1. ERRV Pattern

```mermaid
graph LR
    A[Extract] -->|Initial Data| B[Review]
    B -->|Validation Feedback| C[Revise]
    C -->|Refined Data| D[Verify]
    
    style A fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style B fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
    style C fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style D fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
```

## 2. Primordial Loop

```mermaid
flowchart TD
    A[User Message] -->|input| B[Feed to LLM]
    B -->|process| C[Generate Response]
    C -->|output| D{Check for Tool Calls}
    D -->|No Tool Calls| E[Return Final Response]
    D -->|Has Tool Calls| F[Execute Tool Calls]
    F -->|loop back| B
    
    style A fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style B fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
    style C fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style D fill:#e8ae68,stroke:#333,stroke-width:2px,color:white
    style E fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
    style F fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
```

## 3. MemGPT Architecture

```mermaid
graph TD
    User[User Input] --> System[System Message]
    System --> Context[Context Window<br>Limited Space]
    Context <--> MemOps[Memory Operations]
    MemOps <--> ExtMem[External Memory<br>Unlimited Storage]
    Context --> Funcs[Function Calls]
    Funcs --> Tools[External Tools]
    Tools --> Funcs
    Funcs --> Context
    
    subgraph "Computation Stack Paradigm"
        Context
        MemOps
        ExtMem
        Funcs
        Tools
    end
    
    style User fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style System fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
    style Context fill:#6a62c5,stroke:#333,stroke-width:2px,color:white
    style MemOps fill:#9370db,stroke:#333,stroke-width:2px,color:white
    style ExtMem fill:#4b3d8f,stroke:#333,stroke-width:2px,color:white
    style Funcs fill:#9370db,stroke:#333,stroke-width:2px,color:white
    style Tools fill:#4b3d8f,stroke:#333,stroke-width:2px,color:white
```

## 4. State Machine

```mermaid
stateDiagram-v2
    [*] --> Initialize
    Initialize --> ValidateInitialization
    ValidateInitialization --> Initialize: InitializationIncomplete
    ValidateInitialization --> Research: InitializationComplete
    
    Research --> ValidateResearch
    
    ValidateResearch --> Research: MoreResearchNeeded
    ValidateResearch --> OutlineDraft: ResearchComplete
    
    OutlineDraft --> ValidateOutline
    
    ValidateOutline --> OutlineDraft: OutlineNeedsRevision
    ValidateOutline --> Research: OutlineNeedsResearch
    ValidateOutline --> Writing: OutlineApproved
    
    Writing --> ValidateContent
    
    ValidateContent --> Writing: ContentNeedsRevision
    ValidateContent --> Conclude: DraftComplete
    
    Conclude --> [*]
```

## Mermaid Diagram Tips

1. **Colors**: Use the following colors to maintain consistency:
   - Primary boxes: `fill:#3a5a97,stroke:#333,stroke-width:2px,color:white`
   - Secondary boxes: `fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white`
   - Highlight elements: `fill:#e8ae68,stroke:#333,stroke-width:2px,color:white`

2. **Text**: Keep text concise for better readability in presentation mode

3. **Complexity**: Limit diagram complexity to ensure it renders well in presentation mode

4. **Flow**: Use clear directional arrows with descriptive labels

5. **Testing**: Test diagrams in presentation mode to verify readability from a distance