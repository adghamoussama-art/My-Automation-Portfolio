# 🎬 YouTube Transcription & Interactive HTML Generator

A fully automated **n8n workflow** that retrieves YouTube video transcripts, translates them into the user's preferred language, and generates a polished **interactive HTML file** that is delivered directly through a Telegram bot.

The workflow combines **Telegram, YouTube transcript extraction, JavaScript, Google Gemini, HTML, and automation logic** to turn a simple YouTube link into a structured and interactive translated transcript.

## 🔄 How It Works

### 1. 📩 YouTube Link & Video ID Extraction

The workflow starts when the user sends a YouTube link to the custom Telegram bot.

A **Telegram Trigger** receives the message, and the following node extracts the unique **YouTube Video ID** from the URL.

The workflow also validates the input:

* ✅ Valid YouTube link → Continue processing
* ❌ Invalid input → Workflow stops immediately

This prevents unnecessary API requests and processing when the provided link is invalid.

---

## 📝 2. Retrieve & Clean the Transcript

Once the YouTube ID has been extracted, the workflow retrieves the video's **raw transcript**.

A dedicated processing node then cleans and restructures the transcript to make it:

* Easier to read
* Properly structured
* Free from unnecessary formatting
* Ready for translation and HTML generation

The original timestamps are preserved so they can later be synchronized with the interactive HTML output.

---

## 🌍 3. Language Selection

After retrieving the transcript, the Telegram bot sends an **interactive message** asking the user to select their preferred translation language.

For example:

```text id="r9h3qx"
1 → English
2 → Spanish
3 → French
...
```

The user's selection determines which language will be used during the translation process.

---

## 🔀 4. Conditional Language Routing

The user's selection is processed by a **Code node** that acts as a dynamic switch.

The selected number is mapped to its corresponding language:

```text id="a7k2lm"
1 → English
2 → Spanish
3 → French
4 → Other supported language
...
```

The selected language is then dynamically passed to the AI processing stage.

---

## 🤖 5. AI Translation with Gemini

The transcript is sent to **Google Gemini** together with the language selected by the user.

Gemini is responsible for:

* Translating the transcript
* Preserving the original meaning
* Structuring the translated text
* Maintaining the relationship between sentences and timestamps

The workflow intentionally separates translation from HTML generation to reduce the amount of work performed by the AI model and avoid unnecessary processing or overload errors.

---

## 💻 6. Interactive HTML & JavaScript Generation

After the translation is completed, a dedicated node generates the **HTML and JavaScript code**.

Instead of asking Gemini to handle the entire HTML generation process, this stage is handled separately to improve reliability and performance.

The generated HTML includes:

* 🎨 A polished and readable interface
* 📝 Structured transcript text
* ⏱️ Original timestamps
* ▶️ Interactive sentence-by-sentence navigation
* 🔄 Smooth transitions between transcript lines
* 💻 JavaScript functionality for synchronization

The JavaScript ensures that the transcript moves smoothly from one sentence to the next while respecting the **timestamp of each sentence**.

---

## 📄 7. HTML File Creation & Delivery

Once the translated content and HTML/JavaScript code are ready, the workflow converts the generated data into an actual **`.html` file**.

The completed file is then automatically sent back to the user through Telegram.

The user can open the file in a browser and interact with the translated transcript.

---

## 🧩 Workflow Architecture

```text id="v5q1nz"
Telegram User
      ↓
YouTube Link
      ↓
Telegram Trigger
      ↓
Extract & Validate Video ID
      ↓
Fetch Transcript
      ↓
Clean & Structure Transcript
      ↓
Language Selection
      ↓
Code Switch
      ↓
Gemini Translation
      ↓
HTML / JavaScript Generator
      ↓
Convert Data
      ↓
Create .html File
      ↓
Send File via Telegram
```

## 🛠️ Technologies Used

* **n8n** — Workflow automation and orchestration
* **Telegram Bot API** — User interaction and file delivery
* **YouTube** — Video and transcript source
* **Google Gemini** — Translation and text structuring
* **JavaScript** — Data processing, routing, and interactive HTML functionality
* **HTML / CSS** — Interactive transcript interface
* **Timestamps** — Sentence-level synchronization

## 🎯 Project Goal

The goal of this project was to automate the entire process of transforming a **YouTube video into a translated, structured, and interactive transcript**.

Instead of manually downloading a transcript, translating it, formatting it, and creating an HTML document, the user only needs to **send a YouTube link and select a language**.

The workflow handles everything else automatically — from **video ID extraction and transcript retrieval to AI translation, HTML generation, and Telegram delivery**.

This project demonstrates practical experience with **n8n workflow automation, API integration, AI-powered translation, JavaScript, HTML generation, conditional logic, data processing, and automated Telegram interactions**.
