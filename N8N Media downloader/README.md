#  Telegram AI Assistant & Universal Media Downloader

A fully automated **n8n workflow** that transforms a Telegram bot into a hybrid AI assistant and media downloader.

The workflow automatically analyzes every incoming message and determines whether it is a **text message** that should be processed by AI or a **social media link** from which a video should be extracted and sent back to the user.

## 🔄 How It Works

### 1. 📩 Message Detection & Routing

The workflow starts with a **Telegram Trigger**, which activates whenever the bot receives a new message.

An **IF node** analyzes the incoming message and determines whether it contains:

* 💬 A normal text message
* 🔗 A social media link

The workflow then routes the message to the appropriate branch automatically.

---

## 🧠 AI Branch — Text Processing

When the user sends a normal text message, it is processed by the AI branch.

### Process

1. The message is sent to the **Message a Model** node.
2. **Google Gemini** processes the user's request and generates an appropriate response.
3. The response is sent back to the user through Telegram using the **Send a Text Message** node.

This allows the Telegram bot to function as an **AI-powered conversational assistant**.

---

## 🎥 Media Branch — Automatic Video Downloading

When the user sends a supported social media link, the workflow identifies the platform and automatically downloads the corresponding video.

A **Switch node** analyzes the URL and routes it to the appropriate platform-specific workflow.

### 📸 Instagram

For Instagram links:

1. The **HTTP Request** node sends the URL to a media extraction API.
2. The API returns the video information.
3. The extracted video is sent directly to the user through Telegram using the **Send a Video** node.

### 🎵 TikTok

The TikTok workflow uses two HTTP requests:

1. **HTTP Request1** retrieves the video download URL.
2. **HTTP Request2** downloads the video as binary data.
3. **Send a Video2** sends the downloaded video to the Telegram user.

This two-step process allows the workflow to retrieve and download the actual media file before sending it.

### ▶️ YouTube

For YouTube links:

1. A **JavaScript Code** node extracts the unique YouTube video ID from the URL.
2. The extracted ID is passed to **HTTP Request3**.
3. The request calls the video download API.
4. The resulting file is sent to the user through Telegram using **Send a Video1**.

---

## 🧩 Workflow Architecture

```text id="f7s8ka"
                    ┌── 💬 Text
                    │
Telegram Trigger ──→ IF Node
                    │
                    └── 🔗 Link
                           │
                           ↓
                       Switch Node
                    ┌──────┼──────┐
                    ↓      ↓      ↓
               Instagram TikTok YouTube
                    ↓      ↓      ↓
                 API     API    Extract ID
                    ↓      ↓      ↓
                 Video   Video   API
                    ↓      ↓      ↓
                    └──────┼──────┘
                           ↓
                    Telegram Video
```

The text branch follows a separate path:

```text id="8j3m1p"
Telegram Message
       ↓
    IF Node
       ↓
 Message a Model
   (Gemini AI)
       ↓
Send a Text Message
       ↓
    Telegram
```

## 🛠️ Technologies Used

* **n8n** — Workflow automation and orchestration
* **Telegram Bot API** — User interaction and media delivery
* **Google Gemini** — AI-powered message processing
* **HTTP Requests** — Communication with media extraction APIs
* **JavaScript** — YouTube URL and video ID processing
* **Binary Data Processing** — Downloading and handling video files
* **Switch / IF Nodes** — Conditional routing and platform detection

## 🎯 Project Goal

The goal of this project was to build a **single Telegram assistant capable of handling two different types of tasks automatically**.

Users can communicate with the bot normally and receive AI-generated responses, or simply send a supported social media URL and receive the extracted video directly in Telegram.

This creates a **hybrid automation system** that combines **AI conversation, conditional logic, API integration, media processing, and Telegram automation** into one workflow.

The project demonstrates practical experience with **n8n workflow architecture, AI integration, API requests, JavaScript, binary data handling, conditional routing, and automated Telegram interactions**.
