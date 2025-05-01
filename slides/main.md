# Agentic Patterns and Hybrid Mechanisms of Control



---

## About Me

* James Garfield
* Sr. Principal Engineer @ EnFi
* 20+ years in New England area start-ups

Note: Brief introduction about myself and my work with EnFi.

---


## Audience Survey

* Founders?
* Engineers & Data Scientists?
* Product?
* Sales and Marketing?
* Ops?




--

## AI Use

* ChatGPT?
* Chatbots? 
* Tools?
* Agents?



---


## Out of the Hype &
## Through the Looking Glass

* Skeptic ➡️ Pragmatist
* Beyond the hype: real utility
* A unique tool in the technologist's toolbelt


--


## Hybrid Control
### OR: How I learned to stop worrying and love LLMs
* Using an LLM is letting go of control
* Design Patterns as a coping mechanism
* How to effectivly let go of and regain control

---


## Tools

* Expand capabilities beyond basic inference
* Built-in space for validation/error checking/retries
* First building block in sharing control

Note: Tools are table stakes. You will spend more time tuning these than your prompts. Structured responses via tools is much more reliable than otherwise trying to coerce the LLM into returning the right structure. They provide a built-in spot for validation/errors and giving the AI another chance.

--

## Structured Responses

```typescript
`
    Extract the name from the text and return
    it in json that looks like the following:
    <schema>
    {
      "firstName": "Users first name",
      "lastName": "User's use name",
    }
    </schema>
`
```

--

## Structured Responses


```json
{
  "name": "ExtractName",
  "description": "Use this tool to extract the user's name.",
  "schema": {
    "type": "object",
    "required": ["firstName", "lastName"],
    "properties": {
      "firstName": {
        "type": "string",
        "description": "First name of the user"
      },
      "lastName": {
        "type": "string",
        "description": "Last name of the user"
      },
    }
  }
}
```

--

## Forced Tool Use

* Default mode: Text Response or Tool Use
* Required Mode: Must use a tool

---


## ERRV

* Extract 
* Review 
* Revise 
* Verify


Note: ERRV is an excellent pattern for improving accuracy of data extraction. It's a simple form of ping-pong hybrid control.

--

## ERRV

![ERRV Pattern](images/errv_horizontal.svg)



--

## Extract

```ts
`
Identify all the users in the source text. 
`
```

```json
{
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "name": {
        "type": "string",
        "description": "The user's full name"
      },
      "email": {
        "type": "string",
        "format": "email",
        "description": "The user's email address"
      },
      "role": {
        "type": "string",
        "description": "The user's role in the system"
      }
    },
  }
}
```

--

## Review

```json
{
  "type": "object",
  "properties": {
    "invalid_emails": {
      "type": "array",
      "description": "Array of invalid email values",
      "items": {
        "type": "string"
      },
    },
    "invalid_roles": {
      "type": "array",
      "description": "Array of invalid role values",
      "items": {
        "type": "string"
      },
    }
  },
}
```


--

## Revise

```ts
`
Your goal is to correct extracted data from source text. 
Review the source data, initial extraction, and identified errors.
Provide a corrected extraction after review
<source_text>
%s
<source_text>
<initial_extraction>
%s
</initial_extraction>
<errors>
%s
</errors>
`
```

--

## Verify

* See if values have changed
* Run deterministic checks
* LLM as a Judge

---

## Primordial ~Soup~ Loop

* Core of any agent
* LangChain, Goose, Manus, etc.
* Might implement more than once

Note: Every generic agent has this pattern. It's seen in frameworks like Langchain, Goose, Manus, etc. I want to use this step to explain the loop at a high level. Don't get locked into it rigidly, it's much more useful if you can implement it in variations.

--


![Primordial Loop](images/primordial_loop.svg)


---


## Oracles
#### Agentic Divination

* Structured response
* Extra information gathering tools
* Planning tool: dynamic Chain-of-Reasoning


--

```Go
type Oracle struct {
  llm.MessageClient
  // How many times the LLM can get the schema wrong
  MaxInvalidAttempts int
  // How many total loops before giving up
  MaxLoops int
  Schema   jsonschema.Schema
}

func (o Oracle) Ask(p llm.Prompt) (json.RawMessage, error) {
  responseTool := NewResponseTool(o.Schema)
  p.Tools = append(p.Tools, responseTool)
  p.ToolChoice = llm.ToolChoiceRequired
  // Primordial loop
}

```

--

## Oracle Loop

![Oracle Loop Diagram](images/oracle_loop.svg)


---

## MemGPT
### A Case Study in Hybrid Control

* More than just hybrid control
* From "conversation" to "computation stack"

https://arxiv.org/abs/2310.08560

--

## MemGPT Workflow

![MemGPT Workflow](images/memgpt_workflow.svg)



--

## Anatomy of a Conversation

![Prompt Packet Anatomy](images/prompt_packet.svg)


--

## Generative Computation

![Prompt Packet Anatomy](images/memgpt_packet.svg)

---

## State Machines
### Everything Old is New Again


--

## Progressive, Embeded Control

* Expose the state graph
* Provide tools to trigger state changes
* Each state comes with its own prompt

--

## End-to-End Agent Control

* Configure states to require tool use to orchestrate processes
* Control through state machine structure and prompts
* Watch out for loops!


--

## E2E Report Writer

![State Machine](images/e2e_sm.svg)

Note: This is a simplified version of a state machine for agent control. Note the alternating pattern between action and validation states.

--

## Blended Control

* Insert algorithmic steps in-between forced tool-use states
* Algorithmic states for evaluation and course correction

Note: Ping-pong control alternates between forced tool-use and algorithmic states. Your algorithmic states give you a chance to evaluate how the agent is doing an course correct.

--

## Blended Report Writer

![State Machine](images/pingpong_sm.svg)

Note: This is a simplified version of a state machine for agent control. Note the alternating pattern between action and validation states.

--

## Human in the Loop

* Open up spots for human input
  * Drop required tool use
  * Provide communication tool

Note: Human in the loop can apply to either of the above patterns, but you give the agent a tool to communicate with a human as part of the process.

---

## Final Thoughts

* Get in and get your hands dirty
* Embrace failure
* Evals are the new unit tests


## Thank You!



