# Security & Privacy Notes

- No API keys, tokens, or credentials are stored in this repository.
- No real client data, contact lists, message content, or CRM records are included; all examples in `docs/workflows/` are illustrative.
- Sensitive or irreversible actions (sending an email, publishing publicly, calling a contact) are gated behind an optional human-approval step before execution.
- Any deployment of this architecture should scope each integration's API credentials to the minimum permissions the corresponding agent's tools require (principle of least privilege).