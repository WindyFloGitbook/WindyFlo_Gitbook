# ✨ Pipeline Deplyment

### Pipeline Deployment: Website Embed and API Utilization ('Embed as API')

This guide explains how to integrate your WindyFlo pipeline into a website, call it programmatically, or share it as a standalone chatbot link. All deployment options are accessible via the **"Embed as API"** button on the pipeline editing screen.

\
Clicking the **"Embed as API"** button will display a popup window similar to the one below.

<figure><img src=".gitbook/assets/000 ~ 005.png" alt=""><figcaption></figcaption></figure>

This popup window provides the following main deployment methods:

* **Website Embed:** Directly insert a chatbot widget into your website (**Embed Tab**).
* **Programmatic API Call:** Call the pipeline directly from your server or application (**Python**, **JavaScript**, **cURL Tabs**).
* **Standalone Chatbot Share:** Generate a web chatbot link that can be easily shared (**Share Chatbot Tab**).

***

### 1. Embedding Chatbot Widget on Website (Embed Tab)

This is the most common method to add a chatbot interface that website visitors can directly interact with.

#### a. Select Embed Format

Within the **"Embed" tab**, choose the format that best suits your website design and needs:

* **Popup Html:** Adds a small button to your webpage. Clicking it reveals a popup chatbot window. (Screenshot example)
* **Fullscreen Html:** Uses the entire webpage for the chatbot interface.
* **Popup React / Fullscreen React:** Component code for integration into websites using the React framework.

#### b. Apply Code Snippet

Copy the provided code snippet based on your selected format and insert it into your website's HTML code. It's typically in the form of a `<script>` tag and is best placed within the `<body>` tag.

```
<!-- Example: Popup Html Snippet -->
<script type="module">
  // Import WindyFlo chatbot library
  import Chatbot from "https://cdn.jsdelivr.net/npm/windyflo-embed@<version>/dist/web.js" // Specify version if necessary

  // Initialize chatbot
  Chatbot.init({
    chatflowid: "b76dccea-4ce5-4a10-9470-a50151107759", // Your actual pipeline ID will be auto-filled here
    apiHost: "https://www.windyflo.com", // WindyFlo service address
    // ... additional configuration options (see 'c. Customize Settings' below)
  })
</script>
```

#### c. Customize Settings (Chatbot.init options)

You can customize the chatbot's behavior and appearance by adding various options within the Chatbot.init({...}) object.

* chatflowid (**Required**): The unique ID of the WindyFlo pipeline you want to embed. This is auto-filled when the code is generated.
* apiHost (**Required**): The host address of the WindyFlo service. This is typically auto-filled.
* theme (**Optional**): Sets the visual theme of the chatbot widget (e.g., colors, fonts. Refer to the WindyFlo Theme Guide for available options).
* chatWindow (**Optional**): Configures the chatbot window's title, initial message, etc.
*   ```
    chatWindow: {
      title: "WindyFlo Chatbot",
      welcomeMessage: "Hello! How can I help you today?",
      // ... other window-related settings
    }
    ```

    content\_copydownloadUse code [with caution](https://support.google.com/legal/answer/13505487).JavaScript
* button (**Optional**): (When using **Popup** format) Configures the popup button's icon, color, position, etc.

{% hint style="info" %}
**Tip:** Selecting the **"Show Embed Chat Config"** checkbox at the bottom of the popup window allows you to visually adjust these settings and get the Chatbot.init code with your configurations. (Actual functionality needs verification).
{% endhint %}

***

### 2. Programmatic API Calls (Python, JavaScript, cURL Tabs)

This method allows you to directly call the functionality of your WindyFlo pipeline from a server backend, mobile app, or other automation scripts and process the results.

* **Select Language Tab:** Choose the tab corresponding to your programming environment, such as **Python**, **JavaScript**, or **cURL**.
* **Review Code Example:** A code example for making an API call in the selected language will be provided. This code typically includes:
  * **Request URL:** The unique API endpoint address for your pipeline.
  * **HTTP Method:** Usually POST.
  * **Headers:** Content-Type: application/json and an Authorization header if required.
  * **Request Body/Payload:** A JSON object containing the input data to be passed to the pipeline. The structure of this object depends on the configuration of your pipeline's input nodes.
* **Apply Code:** Copy the provided example code and integrate it into your application. In practice, you will need to dynamically construct the input data and implement logic to parse and utilize the response (JSON) from the API.

***

### 3. Sharing as a Standalone Chatbot (Share Chatbot Tab)

This is the simplest way to share your pipeline, creating a standalone web chatbot page with a unique URL.

* **Select Share Chatbot Tab:** Click the **"Share Chatbot" tab** at the top of the popup window.
* **Adjust Settings:** Modify the chatbot page's **"Title,"** **"Welcome Message,"** etc., as desired.
* **Generate and Share URL:** After saving your settings, a unique shareable URL will be generated. Copy this URL and send it to others. Anyone can interact with the chatbot via this link without needing a WindyFlo account. This is useful for demos or quick feedback collection.

***

### 4. Security: API Authentication Setup (Authorization)

If you need to protect your pipeline API, you can set up API key-based authentication.

* **Access Authentication Settings:** Click the **"Authorization"** dropdown menu in the top-right corner of the **'Embed as API'** popup window. (Default: **No Authorization**).
* **Create/Select API Key:**
  * Select **"Create New API Key"** (or similar) to generate a new API key and give it a name.
  * If you have an existing key, select it from the list.
* **Use API Key:**
  * **For Programmatic API Calls:** You must copy the generated API key value and include it in the Authorization header of your HTTP request (typically in the format Bearer \<YOUR\_API\_KEY>).
  * **For Website Embed or Chatbot Share:** The code or link may be generated with authentication settings applied, or it might operate based on WindyFlo's internal handling mechanisms.
* **Caution:** API keys are sensitive information and must be managed securely. Refer to the API Security Guide for more details.

***

You can now effectively deploy your WindyFlo pipeline for various purposes using the diverse options provided through the **'Embed as API'** feature.
