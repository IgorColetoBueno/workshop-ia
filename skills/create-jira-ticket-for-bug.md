# Create Jira Ticket for Bug Skill

This skill guides the AI to generate a well-structured Jira ticket for a reported bug, utilizing the Jira MCP server if available.

## Workflow

1.  **Extract Information:** Gather the bug description, steps to reproduce, expected behavior, and actual behavior from the user's prompt or error logs.
2.  **Format Ticket Content:**
    *   **Summary:** A concise, descriptive title (e.g., `[BUG] App crashes on login with empty password`).
    *   **Description:** Include clear sections: "Steps to Reproduce", "Expected Result", "Actual Result", and "Technical Context" (stack traces, affected components).
    *   **Priority/Severity:** Suggest a priority based on the impact.
3.  **Create Ticket:** Use the Jira MCP Server tool (e.g., `create_issue`) to submit the ticket to the configured Jira project.
4.  **Confirm:** Provide the user with the generated Jira ticket ID and a brief summary of what was created.
