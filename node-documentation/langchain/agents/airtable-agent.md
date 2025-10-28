# Airtable Agent

**The Airtable Agent** node is an agent designed in WindyFlo to query data stored in Airtable and receive results in natural language. Without a complex interface, you can obtain necessary information interactively through simple questions, and it's useful in various automation scenarios.

For example, it can handle questions like these:

* “How many incomplete tasks are there in my project tracker table?”
* “Tell me the contact information of customers registered in the CRM.”
* “Give me a summary of all records added last week.”

The Airtable Agent goes beyond simply fetching data - **it understands and summarizes data through LLM**, so even non-developers can intuitively utilize the data.

<figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption><p>WindyFlo Airtable Agent</p></figcaption></figure>

### Inputs

| Item                      | Description                                                                                                                         | Required |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | -------- |
| **Language Model**        | ChatModel connection (e.g., GPT, Claude, etc.). Used for query analysis and response generation.                                    | Required |
| **Input Moderation**      | Whether to automatically filter inappropriate questions.                                                                            | Optional |
| **Connect Credential**    | Authentication information such as API key for Airtable connection.                                                                 | Required |
| **Base ID**               | Unique ID of the Airtable Base. Example URL: `https://airtable.com/app11RobdGoX0YNsC/...` → `app11RobdGoX0YNsC`                     | Required |
| **Table ID**              | <p>Unique ID of the Airtable Table. </p><p>Example URL: <code>.../tblJdmvbrgizbYlCO/...</code> → <code>tblJdmvbrgizbYlCO</code></p> | Required |
| **Additional Parameters** | Detailed configuration values in JSON format.                                                                                       | Optional |
| **Return All**            | Whether to retrieve all records from the table.                                                                                     | Optional |
| **Limit**                 | Maximum number of records (default: 100). Applied only when Return All is turned off.                                               | Optional |

### Use Cases

| Usage Scenario      | Example                                           |
| ------------------- | ------------------------------------------------- |
| **Work Automation** | "Show me only tasks due today"                    |
| **CRM Query**       | "Show me the list of customers residing in Seoul" |
| **Data Summary**    | "Summarize the items added last week"             |
