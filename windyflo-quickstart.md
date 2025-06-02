# ⚡ WindyFlo Quickstart

WindyFlo is a visual platform for building and testing AI pipelines — from prompt chaining to model orchestration.

This guide will walk you through the basics. You'll be up and running with your first pipeline in minutes.

***

### 1. What is a Pipeline?

A **pipeline** in WindyFlo is a visual, node-based automation flow that connects inputs, logic, and outputs. It can power tasks such as conversational AI, document search, or external API calls.

#### How it works:

* Drag and drop nodes onto a visual canvas
* Connect them to create data flow from input → processing → output
* Control each node’s behavior using parameters (LLM prompts, API settings, etc.)

***

### 2. Creating a New Pipeline Workspace

WindyFlo uses **workspaces** to design and manage your AI pipelines.

#### Steps:

1.  **Go to My Pipeline**

    In the top menu, click **My Pipeline** to view your existing pipelines.
2.  **Click + Create Pipeline**

    This takes you to a form for creating a new workspace.
3. **Enter Basic Info**:
   * **Pipeline name**: e.g. `sample_chat`, `mail_assistant`
   * **Description**: Short description (max 100 characters)
   * **Tags**: Add keywords to categorize your pipeline
   * **Visibility**: Choose Public (shared) or Private (for Pro users)
   * **Allow others to run**: Toggle access permission for other users
4.  **Click Create AI Model Pipeline**

    This creates the pipeline and opens the visual editor.

***

### 3. Connecting Basic Nodes

WindyFlo pipelines follow a basic structure:

**Input → Processing → Output**

#### Key Concepts:

* Each node has:
  * **Inputs** on the left
  * **Outputs** on the right
* Common starting/ending nodes:
  * **Agents** and **Chains** nodes handle user input and generate the final response
* Extend functionality using:
  * **Document Loaders**: For document-based Q\&A
  * **Tools/API nodes**: For web searches, API calls, etc.

#### Advanced Flow Control Nodes:

*   **Multi Agents**:

    Combine `Supervisor` and `Worker` nodes to create agent teams with distinct roles
*   **Sequential Agents**:

    Use `seqStart`, `seqLoop`, `seqCondition`, `seqEnd` nodes for loops, conditions, and multi-step logic

This no-code interface lets you visually compose powerful AI workflows.

***

### 4. Configuring Node Parameters

Once nodes are connected, configure each one’s parameters for it to function properly.

#### Node Structure:

Each node includes:

* **Inputs**: Data from external sources or previous nodes (e.g., documents, chat models)
* **Parameters**: Controls logic (e.g., prompt text, model settings, loop count)
* **Outputs**: Passes results to the next node (e.g., summaries, search results)

#### Tips:

* **Fields marked with \* are required**
* Use the **expand icon** next to prompt fields to open a larger editor
* Some nodes offer advanced configuration (e.g., **Format Prompt Values**)
* For external APIs, set **Credentials** (API keys, tokens, etc.)

If a node is misconfigured, a red warning icon will appear.

***

### 5. Running and Testing the Pipeline

After setup, test your pipeline with the built-in chat interface.

#### How to Run:

1.  **Click Save**

    You must save the pipeline before running.
2.  **Click ▶ Run**

    This opens the chatbot interface.
3.  **Enter a Message**

    Type a question like:

    * “Summarize the contents of this PDF”
    * “Tell me the latest news”

    This message is passed to the starting Agent/Chain node.
4.  **View Responses**

    You’ll see output like plain text, summaries, JSON, or triggered tool actions.
5.  **Iterate**

    Modify nodes, click **Save**, then **Run** again to test updated logic.

#### Warnings:

* Check all required parameters
* **Agents/Chains must connect to a Chat Model**
* **Tool/API nodes require valid credentials**
* For complex pipelines (Multi Agents, Sequential), verify each step individually

***

### 6. Saving and Deploying Pipelines

Pipelines can be saved, shared, and deployed as APIs or embeddable components.

#### Edit Pipeline Info:

Click the ✏️ **Edit** icon in the left sidebar to update:

* Name
* Description
* Tags
* Visibility (Public = shared in Pipeline Hub, Private = user-only)
* Allow others to run

#### Add a README:

Click the 📄 icon to open the **README editor**

Add markdown content to explain use cases, warnings, and how to run it.

> This helps others understand your pipeline when you publish it.

#### Deploy as API:

Click **\</> Embed as API** (top-right) to open deployment options:

* **Embed**: Get HTML/JS code to add chatbot to your website
* **Python / JS / curl**: Auto-generated code to call your pipeline from external apps
* **Share Chatbot**: Generate a public URL for others to interact with your chatbot

You can customize title, welcome message, font, background color, and access permissions.

***

### Next Step: Try the Tutorial

Ready to build your own?

Follow the official tutorial and build a complete chatbot pipeline step-by-step.

👉 [Try the WindyFlo Tutorial](windyflo-tutorial.md)

***

Let me now export this into a Word and PDF format for you.

✅ Here is the complete, developer-friendly English version of the **WindyFlo Quickstart Guide** in Word format:

📄 Download WindyFlo\_Quickstart\_EN\_Full.docx

Let me know if you’d like a PDF version as well or want help embedding this into GitBook or your website.
