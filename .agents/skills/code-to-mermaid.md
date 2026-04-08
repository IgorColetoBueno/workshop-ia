# Code to Mermaid Diagram Skill

This skill guides the AI to analyze codebase logic and generate visual documentation using Mermaid diagrams within a Markdown file.

## Workflow

1.  **Analyze the Code:** Read the provided code snippet, file, or module to understand its architecture, control flow, or class relationships.
2.  **Determine Diagram Type:** Decide the most appropriate Mermaid diagram type based on the code's nature:
    *   **Flowchart (`graph TD` or `flowchart LR`):** Best for logic flow, algorithms, or sequential processes.
    *   **Sequence Diagram (`sequenceDiagram`):** Best for showing interactions between different components, services, or actors over time.
    *   **Class Diagram (`classDiagram`):** Best for showing object-oriented structures, inheritance, and relationships.
    *   **State Diagram (`stateDiagram-v2`):** Best for state machines or components that transition between specific states.
3.  **Extract Components:** Identify the key actors, nodes, classes, or states from the code to be represented in the diagram.
4.  **Generate Mermaid Syntax:** Write the exact Mermaid block, ensuring syntax correctness (proper arrows, node shapes, and text escaping).
5.  **Output Markdown:** Provide the user with a `.md` file structure (or snippet) that wraps the generated Mermaid syntax in triple backticks with the `mermaid` language tag.
    ```markdown
    ## System Architecture

    ```mermaid
    graph TD
        A[Client] --> B(Server)
        B --> C{Database}
    ```
    ```
6.  **Explain the Diagram:** Briefly explain what the generated diagram represents and how it maps back to the original code.