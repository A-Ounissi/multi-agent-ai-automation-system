# Make.com Integration

Make.com scenarios back the following:
- Google Docs create/read
- Notion read/write
- Google Flights/Hotels via SerpAPI
- WhatsApp send/receive
- Scheduled (cron) triggers that fire the Executive Director Agent

Pattern: Relevance AI agent tool → HTTP request → Make.com webhook → scenario executes → JSON response returned to the calling agent.