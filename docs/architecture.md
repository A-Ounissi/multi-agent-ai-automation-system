# System Architecture

## Hierarchy

1. **You** — issue a plain-English instruction.
2. **Executive Director Agent** — the only agent you talk to directly.
3. **Manager Agents (4)** — Communication, Project, Research, Content.
4. **Specialized Agents** — one per software surface (WhatsApp, Slack, CRM, etc.).
5. **Tools** — the actual API actions each specialized agent can call.

## Executive Director Agent

Responsibilities:
- Break the user's request into sub-tasks
- Delegate each sub-task to the correct Manager
- Evaluate whether Managers' results actually satisfy the request
- Report a single, consolidated answer back to the user

Tools: `Send WhatsApp Message`, `Get Current Date`. Deliberately minimal — its job is reasoning and delegation, not execution.

## Manager Agents

| Manager | Owns | Sub-agents |
|---|---|---|
| Communication Manager | Messaging & scheduling surfaces | Slack, Email, LinkedIn Comms, WhatsApp, Voice, Calendar |
| Project Manager | Internal record-keeping | CRM, Google Docs/Drive, Notion |
| Research Manager | Information gathering | General Research, Travel Research |
| Content Manager | Publishing | LinkedIn, X, Blog, YouTube |

Each Manager: receives a scoped task from the Director → delegates to the right sub-agent(s) → checks the sub-agent's output → returns a verified result upward.

## Why Hierarchical, Not Flat

A single agent holding 20 agents' worth of tools has to pick correctly across 50+ options every time — accuracy drops as tool count grows. Splitting by domain means:

- Each agent's decision space is small and unambiguous
- Errors are caught one level up before they propagate
- New tools/integrations can be added to one sub-agent without retraining the whole system's prompt

## Data Flow Example — "Get my unread messages and summarize them in a doc"

```
Director → Communication Manager: "get all unread messages"
Communication Manager → WhatsApp Agent, LinkedIn Comms Agent, Slack Agent, Email Agent (parallel)
Each Agent → its own tools (Get Unread Chats / Get Unread Messages / Get Emails)
Communication Manager → checks completeness, merges results
Director → Project Manager: "create a Google Doc summarizing this content: [...]"
Project Manager → Google Docs/Drive Agent → Tool: Create Google Doc
Director → reports back to user with doc link
```