# Multi Agent AI Automation System (Super Agent Team)

A 20-agent, 50+ tool AI orchestration system that lets a single natural-language request trigger complex, multi-software workflows messaging, CRM, research, content publishing, and scheduling built on Relevance AI + Make.com, with Unipile for Meta app integrations.

## What It Does

Send one instruction like:

> "Find three cheap flights, put them in a Google Doc, and send them to my mom on WhatsApp."

...and the system decomposes it, delegates it across specialized agents, executes it across real tools (WhatsApp, Slack, Email, LinkedIn, HubSpot, Google Docs, Notion, Calendar), cross-checks the results, and reports back.

## Architecture

YOU
↓
EXECUTIVE DIRECTOR AGENT
↓
┌───────────────┬───────────────┬───────────────┬───────────────┐
Communication Project Research Content
Manager Manager Manager Manager
↓ ↓ ↓ ↓
Specialized Specialized Specialized Specialized
Agents Agents Agents Agents
↓ ↓ ↓ ↓
WhatsApp/Slack/ CRM/Docs/ Web/LinkedIn LinkedIn/X/
Email/Calendar/ Notion Search/Travel Blog/YouTube
LinkedIn/Voice


Full breakdown in [`docs/architecture.md`](docs/architecture.md).

## Why This Design

Single agents with too many tools become unreliable decision-makers. This system enforces:

- **Narrow responsibility per agent** (each agent owns one domain, e.g. WhatsApp-only, Calendar-only)
- **Manager-level evaluation** (a Manager checks its sub-agents' output before passing it up)
- **Director-level evaluation** (final quality gate before reporting back to the user)
- **Strict delegation boundaries** (a manager never asks an agent to do something outside its tool set)

See [`docs/agent-system.md`](docs/agent-system.md) for the full design rationale.

## Stack

| Layer | Tool |
|---|---|
| Agent orchestration | [Relevance AI](https://relevanceai.com) |
| Workflow/integration automation | [Make.com](https://make.com) |
| Meta app integrations (WhatsApp/etc.) | [Unipile](https://unipile.com) |
| LLM | GPT-based reasoning agents |

## Repo Structure

docs/ → architecture, agent design, tool catalog, workflows, security notes
agents/ → one markdown spec per agent, grouped by manager domain
integrations/ → how Make.com, Relevance AI, and Unipile are wired together
screenshots/ → system diagram


## Example Workflows

- [Unread communications digest](docs/workflows/unread-communications.md) — pulls unread WhatsApp/LinkedIn/Slack/Email, summarizes into a Google Doc
- [Lead research → CRM](docs/workflows/lead-research-and-crm.md) — researches a LinkedIn lead, enriches it, adds to HubSpot, notifies Slack
- [Content publishing pipeline](docs/workflows/content-publishing.md) — researches a topic, drafts a blog + LinkedIn post, publishes/schedules

## Status

This was built as a real client engagement (scope, agent design, and integration work done end-to-end). This repo documents the architecture and agent specs; credentials, workspace exports, and client-specific data are intentionally excluded (see `.gitignore` and [`docs/security-and-privacy.md`](docs/security-and-privacy.md)).

## Author

Built by Ahmed Ounissi. Open to consulting/collaboration on agentic automation systems.
