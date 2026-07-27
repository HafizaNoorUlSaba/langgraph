# 🧠 LangGraph Learning Repository

A hands-on learning repository for understanding and building **stateful, controllable, and production-oriented AI agents using LangGraph**.

This repository contains practical implementations, experiments, and examples covering core LangGraph concepts — from basic graphs and state management to tool calling, memory, human-in-the-loop workflows, multi-agent systems, and advanced agentic AI architectures.

---

## 🚀 Why LangGraph?

Traditional LLM applications often follow a simple pattern:

```text
User
 ↓
LLM
 ↓
Response
```

However, real-world AI applications often require:

* Multiple steps
* Memory
* Conditional decisions
* Tool usage
* Loops
* Human approval
* Multiple agents
* Error handling
* Stateful workflows

LangGraph helps build these systems by representing an AI workflow as a graph.

```text
        ┌─────────────┐
        │    Input    │
        └──────┬──────┘
               │
               ▼
        ┌─────────────┐
        │     Agent   │
        └──────┬──────┘
               │
       ┌───────┴────────┐
       │                │
       ▼                ▼
    Tool Call       Final Answer
       │
       ▼
    Agent Loop
```

---

# 🧩 Core LangGraph Concepts

This repository covers the following concepts:

## 1. Graphs

A LangGraph workflow is represented as a graph consisting of:

* Nodes
* Edges
* State
* Conditional routing

```text
Graph
 ├── Nodes
 ├── Edges
 └── State
```

---

## 2. State

State represents the information that flows through the graph.

For example:

```python
from typing import TypedDict

class State(TypedDict):
    messages: list
```

The state can contain:

* User messages
* AI responses
* Tool outputs
* Intermediate results
* Agent decisions
* Metadata

Conceptually:

```text
Initial State
      ↓
   Node 1
      ↓
 Updated State
      ↓
   Node 2
      ↓
 Final State
```

---

## 3. Nodes

Nodes are functions that perform specific tasks.

For example:

```python
def chatbot_node(state):
    response = llm.invoke(state["messages"])

    return {
        "messages": [response]
    }
```

A node can:

* Call an LLM
* Execute a tool
* Retrieve documents
* Make a decision
* Transform data
* Call another agent

---

## 4. Edges

Edges define the flow between nodes.

```text
Node A
  ↓
Node B
  ↓
Node C
```

Example:

```python
graph.add_edge("node_a", "node_b")
```

Edges determine the execution order of the workflow.

---

## 5. Conditional Edges

Conditional edges allow the graph to make decisions.

```text
          ┌──────────────┐
          │    Agent     │
          └──────┬───────┘
                 │
          ┌──────┴──────┐
          │             │
          ▼             ▼
      Use Tool      Final Answer
```

Example:

```python
def route_decision(state):
    if should_use_tool(state):
        return "tool"

    return "end"
```

This enables dynamic agentic behavior.

---

# 🔄 LangGraph Execution Flow

A typical LangGraph workflow looks like:

```text
Input
  ↓
State
  ↓
Node
  ↓
State Update
  ↓
Conditional Decision
  ↓
Next Node
  ↓
Tool / Agent / Retrieval
  ↓
Updated State
  ↓
Final Response
```

---

# 🤖 Building AI Agents with LangGraph

A basic agent workflow can be represented as:

```text
              ┌─────────────┐
              │    User     │
              └──────┬──────┘
                     │
                     ▼
              ┌─────────────┐
              │    Agent    │
              └──────┬──────┘
                     │
          ┌──────────┴──────────┐
          │                     │
          ▼                     ▼
      Tool Call            Final Answer
          │
          ▼
      Tool Result
          │
          ▼
       Agent Again
```

This loop allows an agent to:

1. Understand the user request
2. Decide whether a tool is required
3. Call the tool
4. Observe the result
5. Continue reasoning
6. Return the final response

---

# 🛠️ Tool Calling

LangGraph can be used to create agents that interact with external tools.

Examples include:

* Web search
* Calculators
* APIs
* Databases
* Python execution
* File systems
* Custom business tools

Example architecture:

```text
User
 ↓
LLM Agent
 ↓
Tool Decision
 ↓
Tool Execution
 ↓
Tool Result
 ↓
LLM Agent
 ↓
Final Answer
```

---

# 🧠 Memory and Persistence

One of the most important features of LangGraph is state persistence.

A graph can maintain information across interactions.

```text
Conversation 1
      ↓
   State
      ↓
Conversation 2
      ↓
   Updated State
      ↓
Conversation 3
```

This enables:

* Conversational memory
* Long-running workflows
* Persistent agent state
* Thread-based conversations
* Resumable execution

---

# 🧑‍💻 Human-in-the-Loop

LangGraph allows workflows to pause and wait for human input.

Example:

```text
Agent
  ↓
Generate Action
  ↓
⏸ Human Approval
  ↓
Approved?
  │
  ├── Yes → Execute
  │
  └── No → Modify / Stop
```

This is useful for:

* Financial decisions
* Sensitive operations
* Approval workflows
* Content generation
* Enterprise AI systems

---

# 🤝 Multi-Agent Systems

LangGraph can coordinate multiple specialized agents.

Example:

```text
                 Supervisor
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
   Researcher     Coder       Reviewer
        │            │            │
        └────────────┼────────────┘
                     │
                     ▼
                 Final Output
```

Each agent can have:

* A specific role
* Its own tools
* Its own instructions
* Its own state
* A specialized responsibility

---


# 🎯 Learning Objective

The goal of this repository is to move beyond simple LLM applications and understand how to build **reliable, stateful, and controllable AI agents**.

The main focus is:

```text
LLM
  +
State
  +
Tools
  +
Memory
  +
Conditional Logic
  +
Multiple Agents
  =
Agentic AI System
```

---




This repository represents my hands-on journey of learning and building with LangGraph.

