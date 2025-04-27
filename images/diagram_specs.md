# Diagram Specifications

## 1. ERRV Pattern (errv.png)

Create a 2x2 grid showing the ERRV process:

- **Extract** (Top Left): Initial data extraction from raw input
  - Icon: Magnifying glass or data extraction symbol
  - Description: "Initial data gathering from source"

- **Review** (Top Right): Validation of extracted data
  - Icon: Checklist or review symbol
  - Description: "Validation of extracted information"

- **Revise** (Bottom Left): Refinement based on review
  - Icon: Edit/pencil symbol
  - Description: "Refinement based on validation feedback"

- **Verify** (Bottom Right): Final confirmation
  - Icon: Checkmark or verification symbol
  - Description: "Final confirmation of accuracy"

Add arrows showing the flow: Extract → Review → Revise → Verify
Use a consistent color scheme with the presentation theme (dark blues/purples).

## 2. Primordial Loop (primordial_loop.png)

Create a flowchart matching the description in req.md:
```
flowchart TD
  A[User Message] -->|input| B[Feed to LLM]
  B -->|process| C[Generate Response]
  C -->|output| D{Check for Tool Calls}
  D -->|No Tool Calls| E[Return Final Response]
  D -->|Has Tool Calls| F[Execute Tool Calls]
  F -->|loop back| B
```

Use rounded rectangles for process boxes and diamond shape for the decision node.
Use arrows with clear labels.
Color coding:
- Input/Output nodes: Blue
- Process nodes: Purple
- Decision node: Orange
- Loop back connection: Highlight with different color or style

## 3. MemGPT Architecture (memgpt.png)

Create a diagram that illustrates:
- Core components:
  - External Memory (large storage)
  - Internal Context (limited prompt window)
  - Retrieval Mechanism (connecting the two)
  - Function Calling Interface

- Key features:
  - Memory hierarchy
  - Context management
  - System messages
  - Function endpoints

Layout should show the "computation stack" paradigm versus the traditional "conversation" model.
Include arrows showing data flow between components.

## 4. State Machine (state_machine.png)

Create a simplified version of the state machine from req.md:
```
stateDiagram-v2
Initialize --> ValidateInitialization: InitializationComplete
ValidateInitialization --> Initialize: InitializationIncomplete
ValidateInitialization --> Research: InitializationComplete

Research --> ValidateResearch: ResearchInProgress

ValidateResearch --> Research: MoreResearchNeeded
ValidateResearch --> OutlineDraft: ResearchComplete

OutlineDraft --> ValidateOutline: OutlineNeedsRevision

ValidateOutline --> OutlineDraft: OutlineNeedsRevision
ValidateOutline --> Research: OutlineNeedsResearch
ValidateOutline --> Writing: OutlineApproved

Writing --> ValidateContent: DraftReview

ValidateContent --> Writing: ContentNeedsRevision
ValidateContent --> ExpandAnalysis: DraftComplete

ExpandAnalysis --> VerifyExpansion: AnalysisExpanded

VerifyExpansion --> ExpandAnalysis: AnalysisNeedsRevision
VerifyExpansion --> AddCitations: ExpansionComplete

AddCitations --> ValidateCitations: CitationsAdded

ValidateCitations --> AddCitations: CitationsNeedRevision
ValidateCitations --> Conclude: AllComplete
```

Color coding:
- Action states: Blue
- Validation states: Orange/Yellow
- Transitions: Gray arrows with condition labels

Highlight the alternating pattern between action and validation states to illustrate the ping-pong control concept.