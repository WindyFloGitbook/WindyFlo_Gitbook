# WindyFlo – Zapier MCP Server Integration Guide

This document explains how to create a Zapier Model Context Protocol (MCP) server, retrieve the server-specific URL, and integrate it with the **Custom MCP node in WindyFlo** to perform various external automation actions.

***

### Step 1: Create a Zapier MCP Server

1. Go to the Zapier MCP Portal and log in.
2. Click the **+ New MCP Server** button.
3. In the **MCP Client** dropdown, select **Other**.
4. Enter a name in the **Name** field for your MCP server.
5. Click **Create MCP Server** to finalize the setup.

***

### Step 2: Add Tools (Actions)

1. In the left sidebar, select the newly created MCP server.
2. Navigate to the **Configure** tab.
3. Click the **+ Add tool** button.
4. Search and select the app you want to use (e.g., Gmail, Google Sheets).
5. Choose the action (e.g., **Send Email**, **Create Spreadsheet Row**, etc.).
6. For each required field, choose how it should be populated:
   * Manually set by the user
   * Automatically selected by AI (recommended)
   * From a predefined list of values
   * Use a default value
7. If required, connect your account (OAuth/API key).
8. Click **Save** to register the tool.

> 💡 **Tip**: You can add multiple tools to a single MCP server and execute them based on incoming data.

***

### Step 3: Copy the MCP Server URL

1. Go to the **Connect** tab.
2. Find the field labeled **Connect with server-specific URL**.
3. Click **Copy URL** to copy the endpoint.
   *   Example:

       ```
       https://mcp.zapier.com/api/mcp/...
       ```

> ⚠️ **Caution**: This is a unique server endpoint. Treat it as sensitive information—do not expose it publicly.

***

### Step 4: Configure the MCP Node in WindyFlo (Actual Usage)

1. In WindyFlo, add a **Custom MCP** node to your canvas.
2. In the **MCP Server Config** field, input the copied URL in JSON format as shown below:

```json
{
  "url": "https://mcp.zapier.com/api/mcp/..." 
}
```

* Replace the value with the actual URL copied from Zapier.
* Make sure it follows correct JSON syntax: `"url": "..."`

3.  In the **Available Actions** dropdown, click the expand icon (∨) to load available tools you previously configured in Zapier.

    Example actions include:

    * `GMAIL_SEND_EMAIL` – Send an email
    * `GMAIL_CREATE_DRAFT` – Create an email draft
    * `GMAIL_ARCHIVE_EMAIL` – Archive a message
    * `GMAIL_ADD_LABEL_TO_EMAIL` – Add a label to an email
4. Select one or more actions to define the operations this node will trigger.

> ✅ You can also link a preceding LLM node (e.g., GPT) to dynamically generate JSON payloads for execution based on input text.

***

If you'd like a pipeline template or pre-configured demo, let me know. I’d be happy to help set it up for your use case.
