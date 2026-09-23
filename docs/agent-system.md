# Agent System Design

## Agent vs. Tool

- **Agent** — an LLM-driven decision-maker. It decides *what* to do and *when*, given a goal and a constrained toolset.
- **Tool** — a single deterministic action (an API call) the agent can invoke. It has no reasoning of its own.

Example — Travel Research Agent:
- Reasoning: interprets "find me a cheap flight to Lisbon next month" into a search plan
- Tools it can call: `Search Airport Codes`, `Search Airline Codes`, `Check Google Flights`, `Check Google Hotels`

## Prompt Design for Agents

Every agent prompt in this system follows the same template:

Role: who this agent is and what domain it owns
Objective: what a "successful" task completion looks like
Responsibilities: the scope of decisions it's allowed to make
Available sub-agents: (Managers only) who it can delegate to
Available tools: exact list, with 1-line description each
Rules/limitations: what it must never attempt
Examples: 2-3 worked input → output examples
Quality-control instructions: how it verifies its own output before returning it


## The Golden Delegation Rule

> An agent must only delegate a task to another agent that is actually capable of performing it.

Bad:

Communication Manager, get unread messages AND create a Google Doc.

Communication Manager has no Google Docs tool — this instruction breaks mid-execution.

Good:

Communication Manager → retrieve unread messages
Project Manager → create the Google Doc from that content


## Quality Control Layers

1. **Sub-agent self-check** — did the tool call return valid, complete data?
2. **Manager-level check** — does the combined sub-agent output actually answer the delegated task?
3. **Director-level check** — does the Manager's result satisfy the user's original request?
4. **Optional human approval gate** — for sensitive actions (e.g., sending an email, posting publicly), the workflow pauses for explicit user approval before executing.

## Scheduling as a First-Class Feature

Any natural-language instruction can become a recurring workflow by attaching a Make.com scheduled trigger that fires the Director Agent on a cadence. Examples:

- "Every morning at 8am, pull all unread messages and put them in a doc."
- "Every day, research 5 new leads matching [criteria] and add qualified ones to CRM."
- "Every evening, compile today's AI news into a report and send it to me on WhatsApp."

The instruction itself is the workflow definition — no separate automation needs to be hand-built per use case.