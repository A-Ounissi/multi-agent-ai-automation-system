# Workflow: Lead Research → CRM

**Trigger:** Manual, or scheduled daily lead-gen run

**Instruction:** "Research this LinkedIn lead, and if qualified, add them to CRM and notify me on Slack."

**Flow:**
1. Director → Research Manager: "research this LinkedIn profile"
2. Research Manager → General Research Agent: Google Search to locate/confirm the profile
3. Research Manager → LinkedIn Agent: LinkedIn scraping to extract role, company, activity
4. Research Manager evaluates against qualification criteria, returns summary to Director
5. If qualified: Director → Project Manager → CRM Agent: Add Contact to CRM
6. Director → Communication Manager → Slack Agent: Send Slack Message notifying the team