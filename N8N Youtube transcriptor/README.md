Workflow Description: Transcription and HTML Formatting Automation

This workflow automates the process of retrieving, translating, formatting, and sending YouTube video transcriptions as an interactive HTML file via a Telegram bot.

1. Receiving and Extracting the YouTube ID

The cycle begins when the user sends a YouTube link to the custom Telegram bot (Trigger Node). The next node extracts and isolates only the video ID from the received URL to prepare for the querying step.

⚠️ Note: If the input provided by the user is not a valid link, the automation process stops immediately at the second node.

2. Retrieving and Cleaning the Transcript

Once the ID is obtained, a dedicated node retrieves the raw transcript of the video. Then, another node intervenes to clean and restructure the text to make it perfectly readable and understandable.

3. Language Selection (Bot Interaction)

The Telegram bot sends an interactive message to the user, asking them to choose their desired translation language.

4. Conditional Routing (Code Switch)

The data then passes through a code node that acts as a switch based on the user's choice:

1: English
2: Spanish
3: French
(And so on for the other options)

5. AI Generation and Translation

The selected language is dynamically injected into the prompt sent to Gemini. To optimize the model's performance and avoid overload errors, Gemini focuses only on translating and structuring the text.

6. Advanced HTML/JS Formatting

To reduce Gemini's workload, a separate node takes over to generate the HTML and JavaScript code. This code applies a polished design and integrates a JS script to ensure a smooth transition from one line to another, while strictly respecting the timestamp (time marker) of each sentence.

7. File Conversion and Sending

Finally, the textual data and code are converted into raw data, then transformed into an actual .html file. The final node of the workflow sends this file directly to the user on Telegram.

Technical Summary of the Steps:

Telegram Input ➔ ID Extraction & Validation ➔ Transcript Fetch ➔ Text Formatting ➔ Language Selection ➔ Switch Code ➔ Gemini Translation ➔ HTML/JS Generator ➔ Data Conversion ➔ HTML File Creation ➔
