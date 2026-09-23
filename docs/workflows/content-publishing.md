# Workflow: Content Publishing Pipeline

**Trigger:** Manual, or scheduled content calendar run

**Instruction:** "Research today's top AI news and turn it into a blog post and a LinkedIn post."

**Flow:**
1. Director → Research Manager → General Research Agent: Google Search + Web Scraping on AI news
2. Research Manager returns a research summary to Director
3. Director → Content Manager: "write a blog post and LinkedIn post from this research"
4. Content Manager → Blog Agent: drafts long-form post (uses Stock Images tool for visuals)
5. Content Manager → LinkedIn Agent: drafts short-form post using the fine-tuned LinkedIn Writer (matches the user's personal writing style rather than generic AI phrasing)
6. Content Manager reviews both drafts for consistency
7. If human approval is required: pause and wait for user sign-off
8. Content Manager → Post to LinkedIn / Post to Webflow (blog) via its direct publishing tools
9. Director confirms publication back to the user