# Integrations

## Relevance AI
Hosts and orchestrates all agents (Director, Managers, Specialized Agents). Handles the reasoning layer, delegation, and inter-agent communication.

## Make.com
Handles integrations that either aren't natively available in Relevance AI or are faster to build as a scenario:
- Google Docs / Google Drive actions
- Notion read/write
- Google Flights & Hotels via SerpAPI
- WhatsApp message send/receive
- Scheduled triggers (cron-style, powers the daily/recurring workflows)

Pattern: Relevance AI Agent → HTTP/API call → Make.com scenario → target app (Google/WhatsApp/Notion/etc.) → response returned to Relevance AI.

## Unipile
Used to integrate Meta-owned messaging apps (WhatsApp, Instagram DMs) where direct API access is restricted or requires business verification. Unipile provided a unified inbox API layer that the WhatsApp Agent's tools call into, working around the more vague/limited parts of the base tool documentation.

## Triggers
- Manual trigger (chat message to Director)
- Voice/text message via WhatsApp
- Scheduled triggers (Make.com cron, feeding the Director on a timer)