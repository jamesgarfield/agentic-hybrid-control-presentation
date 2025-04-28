# Agentic Patterns and Hybrid Mechanisms of Control

<!-- .slide: data-background="rgb(30, 30, 60)" -->

Note: Welcome everyone! Today I'll be sharing some insights on how we can use different control patterns with LLM agents to create more effective systems.


<!-- INTRODUCTION -->


## About Me

* Background & Experience
* EnFi Context

Note: Brief introduction about myself and my work with EnFi.


## Out of the Hype, and Through the Looking Glass

* Initial skepticism → practical experience 
* Beyond the hype: real utility
* A unique tool in the technologist's toolbelt

Note: I was initially very skeptical of LLMs, but working with them has changed my perspective. The hype-train is unfortunate because I think it obscures a truly useful tool underneath. They're rapidly becoming a tool in a technologist's tool-belt that fills in a spot unlike any other.


<!-- AUDIENCE INTERACTION -->


## Who's Using AI?

* Chatbots? 
* Tools?
* Agents?

<!-- .slide: data-background="rgb(40, 40, 80)" -->

Note: Quick survey to understand audience experience levels and tailor examples.


<!-- BUILDING BLOCKS -->


## Tools & Structured Responses

* First building block of hybrid control
* Expand capabilities beyond basic inference
* More reliable than text coercion
* Built-in validation/errors

Note: Tools are the first building block of hybrid control. They expand the abilities of the LLM beyond basic inference. These are table stakes to me. You will spend more time tuning these than your prompts. Structured responses via tools is much more reliable than otherwise trying to coerce the LLM into returning the right structure. They provide a built-in spot for validation/errors and giving the AI another chance.


## Example: Forced Tool Use

```json
{
  "function_call": {
    "name": "answer_question",
    "arguments": {
      "reasoning": "...",
      "answer": "..."
    }
  }
}
```

Note: Here's an example of how you might implement forced tool use to get structured data back from an LLM.


<!-- PATTERNS -->


## ERRV: Extract - Review - Revise - Verify

<!-- .slide: data-background="rgb(30, 40, 70)" -->

Note: ERRV is an excellent pattern for improving accuracy of data extraction. It's a simple form of ping-pong hybrid control.


## ERRV: 4-Box Visualization

![ERRV Pattern](images/errv.svg)

Note: This visualization shows the four components of the ERRV pattern and how they work together.


## The Primordial Loop

* Core pattern in every generic agent
* LangChain, Goose, Manus, etc.
* Flexible implementation

Note: Every generic agent has this pattern. It's seen in frameworks like Langchain, Goose, Manus, etc. I want to use this step to explain the loop at a high level. Don't get locked into it rigidly, it's much more useful if you can implement it in variations.


## Primordial Loop: Flowchart

![Primordial Loop](images/primordial_loop.svg)

Note: This flowchart shows the basic structure of the primordial loop pattern.


<!-- ADVANCED PATTERNS -->


## Oracles: Advanced Prognostication

* Abstraction above ERRV
* "Response" tool + information gathering tools
* Planning tool: dynamic Chain-of-Reasoning

Note: An oracle is an abstraction above ERRV. It has access to a "response" tool as well as any number of other tools used to gather information or reason about the question. The planning tool enables dynamic Chain-of-Reasoning.


## MemGPT: A Case Study in Hybrid Control

* More than just hybrid control
* From "conversation" to "computation stack"

Note: MemGPT is more than just hybrid control, it represents an ah-ha moment about getting out of the "conversation" paradigm and into "computation stack" mode.


## MemGPT Workflow

![MemGPT Architecture](images/memgpt.svg)

Note: This diagram outlines the basic MemGPT workflow and architecture, showing the shift from conversation to computation stack paradigm.


<!-- STATE MACHINES -->


## State Machines: Everything Old is New Again

<!-- .slide: data-background="rgb(40, 50, 80)" -->

Note: State machines represent an established pattern that's finding new applications in LLM agent control.


## End-to-End Agent Control

* Forced tool use to orchestrate processes
* Control through SM structure and prompts
* Watch out for loops!

Note: End-to-end agent control uses forced tool use to orchestrate going through an entire process without human intervention (far end of the hybrid control spectrum). Your control comes from the structure of the state machine and the prompts you supply for each one. Watch out for loops! Give your agent an out.


## State Machine Example

![State Machine](images/state_machine.svg)

Note: This is a simplified version of a state machine for agent control. Note the alternating pattern between action and validation states.


## Ping-Pong Control

* Alternate between forced tool-use and algorithmic states
* Algorithmic states for evaluation and course correction

Note: Ping-pong control alternates between forced tool-use and algorithmic states. Your algorithmic states give you a chance to evaluate how the agent is doing an course correct.


## Human in the Loop

* Can apply to either control pattern
* Provide agent with human communication tool

Note: Human in the loop can apply to either of the above patterns, but you give the agent a tool to communicate with a human as part of the process.


<!-- CONCLUSION -->


## Key Takeaways

* Hybrid control enables reliable agent systems
* Pattern selection depends on application needs
* Architecture matters more than prompting

Note: In conclusion, hybrid control patterns provide a framework for building more reliable agent systems. The pattern you select should depend on your specific application needs. And remember that architecture decisions often matter more than prompt engineering.


## Thank You!

Questions?

<!-- .slide: data-background="rgb(30, 30, 60)" -->

Note: Thank you for your attention! I'm happy to take any questions.