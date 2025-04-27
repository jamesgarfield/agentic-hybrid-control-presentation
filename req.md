Presentation

* Title: Agentic Patterns and Hybrid Mechanisms of Control
* Intro 
    * introduce myself, background, EnFi
* Out of the Hype, and Through the Looking Glass
    * I was initially very skeptical of LLMs, working with them has changed my perspective
    * The hype-train is unfortunate because I think it obscures a truly useful tool underneath
    * Rapidly becoming a tool in a technologists too-belt that fills in a spot unlike any other
* Audience Survey. Who's using AI? Chatbots? Tools? Agents?
* Tools & Structured Responses
    * Tools are the first building block of hybrid control. They expand the abilities of the LLM beyond basic inference. These are table stakes to me. You will spend more time tuning these than your prompts
    * Structured responses via tools is much more relaiable than otherwise trying to coerce the LLM into returning the right structure. Built in spot for validation/errors & giving the AI another chance
        * Give the LLM one tool to answer with (optionally two if you want to give it an out), force tool use
* ERRV: Extract - Review - Revise - Verify
    * Excellent pattern for improving accuracy of data extration
    * A simple form of ping-pong hybrid control
    * Would like to show a 4-box visualization for this explaining each portion
* Primordial Loop
    * Every generic agent has this pattern. Langchain, Goose, Manus, etc. 
    * want to use this step to explain the loop at a high level, show a flowchart roughly like the one below
    * flowchart TD
        A[User Message] -->|input| B[Feed to LLM]
        B -->|process| C[Generate Response]
        C -->|output| D{Check for Tool Calls}
        D -->|No Tool Calls| E[Return Final Response]
        D -->|Has Tool Calls| F[Execute Tool Calls]
        F -->|loop back| B
    * Don't get locked into it ridgidly, it's much more useful if you can implement it in variations
* Oracles: Advanced prognostication
    * An abstraction above ERRV
    * Access to a "response" tool as well as any number of other tools use to gather information or reason about the question
    * Planning tool: dynamic Chain-of-Reasoning
    * Not sure what to show here
* MemGPT: A case study in hybrid control
    * Research paper in: memgpt-research-paper.pdf
    * More than just hybrid control, an ah-ha moment about getting out of the "conversation" paradigm and into "computation stack" mode
    * Would like to show something outlinine the basic MemGPT workflow
* State Machines: Everything old is new again
	* End-to-end agent control
        * Forced tool use to orchestrate going through an entire process without human intervention (far end of the hybrid control spectrum).
        * Your control comes from the structure of the SM and the prompts you supply for each one
        * Watch out for loops! Give your agent an out.
        * Would like to show a simplified version of this state machine:
            * stateDiagram-v2
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
	* Ping-pong control
        * Alternate between forced tool-use and algorithmc states
        * Your algorithmic states give you a chance to evaluate how the agent is doing an course correct
        * Want to highlight differences here from the SM from the last slide highlighting where we can insert algorithmic control in the Verify stages
	* Human in the loop 
        * Can apply to either of the above, but you give the agent a tool to communicate with a human as part of the process