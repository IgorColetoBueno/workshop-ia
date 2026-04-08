# Read Jira Ticket and Implement Skill

This skill guides the AI to fetch a task's requirements from Jira and implement the required code changes.

## Workflow

1.  **Fetch Requirements:** Use the Jira MCP Server (e.g., `get_issue`) to retrieve the details of the specified Jira ticket ID.
2.  **Analyze Context:** Read the ticket's description, acceptance criteria, and any linked technical context.
3.  **Locate Code:** Use search tools to find the files in the codebase that need to be modified.
4.  **Implement:** Write the code to fulfill the acceptance criteria. Ensure existing functionality is not broken.
5.  **Verify:** Cross-check the implemented changes against the Jira ticket requirements. Provide a summary of the changes made to the user.
