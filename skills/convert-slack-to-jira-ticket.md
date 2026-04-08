# Convert a Slack Message into a Jira Ticket Skill

This skill guides the AI to take a feature request, bug report, or task mentioned in Slack and convert it into an actionable Jira ticket.

## Workflow

1.  **Fetch Context (Optional):** If a Slack thread URL is provided, use the Slack MCP Server to read the full context of the discussion. Otherwise, use the text provided by the user.
2.  **Synthesize Information:** Extract the core problem or request from the conversational text. Ignore pleasantries and off-topic chat.
3.  **Format Ticket:**
    *   **Summary:** Create a clear, professional title for the ticket.
    *   **Description:** Write a structured description detailing the request, background context from the Slack thread, and any explicit requirements mentioned.
4.  **Create Ticket:** Use the Jira MCP Server to create the ticket in the appropriate project.
5.  **Confirm:** Provide the user with the new Jira ticket ID and link.
