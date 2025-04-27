# Diagram Generation Guide

This guide provides instructions for generating the diagrams needed for the presentation.

## Option 1: Generate using Mermaid.js

You can use the Mermaid Live Editor (https://mermaid.live/) to generate SVG diagrams from the following specifications.

### 1. ERRV Pattern

```mermaid
graph TD
    A[Extract] -->|Initial Data| B[Review]
    B -->|Validation Feedback| C[Revise]
    C -->|Refined Data| D[Verify]
    
    style A fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style B fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
    style C fill:#3a5a97,stroke:#333,stroke-width:2px,color:white
    style D fill:#5a7dbb,stroke:#333,stroke-width:2px,color:white
```

Export as SVG and save as `errv.svg` in the images directory.

### 2. Primordial Loop

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

Export as SVG and save as `primordial_loop.svg` in the images directory.

### 3. MemGPT Architecture

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

Export as SVG and save as `memgpt.svg` in the images directory.

### 4. State Machine

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
    
    state Initialize {
        [*] --> InitProcess
        InitProcess --> [*]
    }
    
    state Research {
        [*] --> GatherInfo
        GatherInfo --> Synthesize
        Synthesize --> [*]
    }
```

Export as SVG and save as `state_machine.svg` in the images directory.

## Option 2: Use a Diagramming Tool

Alternatively, you can use diagramming tools like:

1. **Draw.io** (https://app.diagrams.net/)
2. **Lucidchart** (https://www.lucidchart.com/)
3. **Figma** (https://www.figma.com/)

Use the specifications in the `diagram_specs.md` file to create these diagrams.

## Converting SVG to PNG

If PNG files are preferred for the presentation, convert the SVG files using:

1. Online converters like https://svgtopng.com/
2. Command line tools:
   ```bash
   # Using ImageMagick
   convert errv.svg errv.png
   ```
3. Graphics software like Adobe Illustrator, Inkscape, or GIMP

## Updating Slide Links

After generating the diagrams, you may need to update the file paths in `slides/main.md` to point to either `.svg` or `.png` files, depending on which format you choose.