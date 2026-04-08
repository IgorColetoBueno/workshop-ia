# Code Review Skill

This skill guides the AI to perform a comprehensive, context-aware code review based on a Pull Request (PR) link.

## Workflow

1.  **Fetch PR Information:** Receive a PR link from the user. Use the GitHub MCP Server (or `gh` CLI) to read the PR body, description, and metadata.
2.  **Extract Ticket Context:** Read the Jira ticket or other issue tracker references mentioned in the PR body. If an integration (like Jira MCP) is available, briefly read the ticket context to understand the business requirements.
3.  **Analyze Existing Feedback:** Read the existing PR comments to avoid duplicating feedback or to understand ongoing discussions.
4.  **Review the Changes:** Read the actual code changes (diffs).
    *   Check for bugs, security vulnerabilities, and performance bottlenecks.
    *   Verify adherence to clean code principles (SOLID, DRY) and project architecture.
    *   Ensure the changes fulfill the requirements stated in the PR body and the associated ticket.
5.  **Draft Feedback (as an AI Agent):**
    *   Draft actionable feedback with code examples showing the improved version.
    *   Categorize feedback by severity (Critical, Minor, Nitpick).
    *   Include positive feedback for well-written code.
    *   *Important:* Format your drafted comments so the user can easily review them. **Do not post them directly to the PR yet.**
6.  **User Confirmation:** Present the drafted review to the user. Explicitly identify yourself as an AI assistant (e.g., "I am your AI code review assistant. Here are my drafted comments for PR #..."). Ask the developer which specific comments they would like you to officially post on the PR.
7.  **Publish Comments:** Once the user confirms or edits the drafted comments, use the GitHub integration to post the approved comments directly to the PR.
