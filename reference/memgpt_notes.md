# MemGPT Reference Notes

These notes summarize key concepts from memgpt-research-paper.pdf for use in the presentation.

## Core Concepts

MemGPT represents a significant innovation in LLM design, moving beyond the conversation paradigm to a computation stack model. Key concepts include:

1. **Memory Management**
   - External memory storage beyond context window
   - Intelligent context window management
   - Automatic archival and retrieval 

2. **Hybrid Control Mechanisms**
   - Function-calling for controlling memory operations
   - Interrupt system for context management
   - Reflection capabilities through self-interrogation

3. **Architectural Paradigm Shift**
   - Computer-inspired architecture
   - Memory hierarchy (context window = registers/cache, external storage = main memory)
   - Interrupt system (context management through interrupts/handlers)
   - Function calling API (similar to system calls)

## Why It's Significant

MemGPT demonstrates several key insights for the presentation:

1. **Beyond the Conversation Paradigm**
   - Moving from chat-style interaction to computational model
   - Breaking free of the token window constraint
   - Enabling persistent state across interactions

2. **Hybrid Control in Action**
   - Function-based interaction between LLM and external systems
   - External algorithms managing what enters/leaves context
   - Cooperative control between LLM and external systems

3. **Implementation of Control Patterns**
   - Shows practical implementation of primordial loop
   - Demonstrates ping-pong control between LLM and external systems
   - Provides real-world example of hybrid control benefits

## Key Diagram Elements

For the MemGPT workflow diagram, emphasize:

1. **Memory Hierarchy**
   - Context window (limited, active processing)
   - External memory (persistent, large storage)
   - Retrieval mechanisms (connecting the two)

2. **Control Flow**
   - Function calls from LLM to external systems
   - Interrupt-based context management
   - Decision points for memory operations

3. **Architectural Components**
   - Message passing system
   - External function endpoints
   - Memory manager
   - Archival storage


## Workflow

* Push message onto FIFO queue
* Check context size
   - Over warning threshold? Push warning onto queue
   - Over context size? Summarize oldest x% of history, add that to the end of the queue
* Send to LLM
   - Got warning message? -> StoreInContext
   - Missing history? -> SearchRecallStorage