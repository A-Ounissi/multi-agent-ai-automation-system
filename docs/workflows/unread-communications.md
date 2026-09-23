# Workflow: Unread Communications Digest

**Trigger:** Manual or scheduled (e.g., every morning at 8am)

**Instruction:** "Retrieve all unread messages from my communication channels and summarize them in a Google Doc."

**Flow:**
1. Director → Communication Manager: "get all unread messages across channels"
2. Communication Manager delegates in parallel to: WhatsApp Agent, LinkedIn Comms Agent, Slack Agent, Email Agent
3. Each sub-agent calls its respective "get unread" tool
4. Communication Manager merges and validates completeness
5. Director → Project Manager: "summarize this content into a new Google Doc"
6. Project Manager → Google Docs/Drive Agent → Create Google Doc
7. Director reports the doc link back to the user