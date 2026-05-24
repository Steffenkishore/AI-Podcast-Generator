# 🎙️ AI Podcast Generator using n8n + Gemini + Murf AI

An AI-powered Podcast Generator that converts any topic into an audio podcast automatically using `n8n`, `Google Gemini`, and `Murf AI`.

This project allows users to enter a topic from a frontend interface, sends the request to an n8n workflow through a webhook, generates podcast content using AI, converts it into voice audio, and returns the generated podcast back to the user.

## Live Link: https://bubbly-audio-box.lovable.app/

---

## 🚀 Features

* Generate podcasts from any topic using AI
* Beautiful frontend interface
* AI-generated podcast script using Google Gemini
* Convert text into realistic voice audio using Murf AI
* Fully automated workflow using n8n
* Webhook integration between frontend and backend
* Real-time audio response to frontend

---

# 🛠️ Tech Stack

* Frontend : HTML/CSS/JavaScript (Generated using AI tools like Lovable)
* Automation : n8n
* LLM : Google Gemini
* Text-to-Speech : Murf AI
* Communication : Webhooks

---

# 📌 Workflow Architecture

```text
Frontend → Webhook → LLM Chain → Gemini AI → Murf AI → Respond to Webhook → Frontend Audio Player
```

---

# 📷 Workflow Screenshot

![AI-Podcast-Generator](./assets/n8n%20workflow%20screenshot.png)

---

# ⚙️ How This Automation Works

## 1️⃣ User Enters a Topic

The user types a topic in the frontend interface.

Example:

```json
{
  "text": "Generative AI"
}
```

This data is sent to the n8n webhook URL.

---

## 2️⃣ Webhook Receives the Request

The `Webhook` node acts as the starting point of the workflow.

### Webhook Configuration

* HTTP Method → `POST`
* Response Mode → `Respond to Webhook`

The webhook receives data from the frontend and triggers the workflow automatically.

---

## 3️⃣ LLM Chain Processes the Topic

The received topic is passed into the `Basic LLM Chain` node.

### Input Configuration

```javascript
{{ $json.body.text }}
```

This captures the topic sent from the frontend.

The LLM chain then sends the prompt to the Google Gemini model.

---

## 4️⃣ Google Gemini Generates Podcast Script

The `Google Gemini Chat Model` generates podcast content based on the topic provided by the user.

Example:

* Topic → "Artificial Intelligence"
* Output → AI-generated podcast script

---

## 5️⃣ Murf AI Converts Text into Audio

The generated podcast script is sent to `Murf AI` using an HTTP Request node.

Murf AI converts the generated script into realistic voice audio.

---

## 6️⃣ Respond to Webhook Sends Audio Back

The `Respond to Webhook` node sends the generated podcast audio back to the frontend.

### Configuration

* Respond With → `Binary File`
* Response Data Source → `Automatically from Input`

The frontend then receives the generated audio and displays a podcast player.

---

# 🌐 Frontend Integration

The frontend communicates with n8n using the webhook URL.

Example API Request:

```javascript
fetch("YOUR_WEBHOOK_URL", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    text: userInput,
  }),
});
```

---

# 🧩 Steps to Create This Automation

## Step 1 — Create Frontend

Create a simple frontend using:

* HTML/CSS/JavaScript
* React
* AI UI tools like Lovable

The frontend should contain:

* Text input field
* Generate Podcast button
* Audio player section

---

## Step 2 — Create n8n Workflow

Inside n8n:

### Add Nodes

* Webhook Node
* Basic LLM Chain
* Google Gemini Chat Model
* HTTP Request Node
* Respond to Webhook Node

---

## Step 3 — Configure Webhook

Set:

```text
HTTP Method → POST
Response Mode → Respond to Webhook
```

Copy the webhook URL.

---

## Step 4 — Connect Frontend to Webhook

Send frontend data to the webhook URL using a POST request.

---

## Step 5 — Configure Gemini Prompt

Inside the LLM Chain node:

```javascript
{{ $json.body.text }}
```

This captures the frontend topic dynamically.

---

## Step 6 — Generate Audio Using Murf AI

Use Murf AI API inside the HTTP Request node to convert generated text into speech.

---

## Step 7 — Send Audio Back to Frontend

Use the `Respond to Webhook` node to return the generated audio file.

---

# ▶️ Running the Project

## Run n8n Workflow

1. Open n8n
2. Execute the workflow
3. Make sure workflow status is set to `Active`

---

## Run Frontend

Open your frontend project and start it.

Example:

```bash
npm run dev
```

---

## Test the Application

1. Enter a podcast topic
2. Click `Generate Podcast`
3. Wait for AI processing
4. Audio player appears
5. Play the generated podcast

---

# 📚 What I Learned

Through this project, I learned:

* How webhooks work
* Connecting frontend with n8n workflows
* Using AI models inside automation
* Sending and receiving data using APIs
* Building AI-powered real-world applications
* Automating content generation workflows

---

# 🙌 Credits

Special thanks to NxtWave for teaching and guiding these AI automation concepts using n8n and AI tools.
