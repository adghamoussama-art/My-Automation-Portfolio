Workflow Description: This n8n workflow autonomously manages messages received by a Telegram bot. It uses conditional logic to separate text messages, processed by Artificial Intelligence, from social media links, from which it automatically extracts videos.

1. Initial Analysis and Sorting

Trigger (Telegram Trigger): Activates upon receiving each message.

Condition (IF Node): Checks the structure of the message. If the text is not a link, the workflow goes to the AI branch. If it is a link, it is sent to the Switch node for platform identification.

2. AI Branch: Text Processing

Generation: The text is transmitted to the Message a model node (via Google Gemini), which generates an appropriate response.

Sending: The Send a text message node returns the text response to the user on Telegram.

3. Media Branch: Video Extraction

The Switch node routes the link to one of the three specific channels according to the detected platform:

Instagram: The HTTP Request node makes an API request to extract the video from the link, then the Send a video node transmits the final file.

TikTok: The process uses two successive nodes. The HTTP Request1 node retrieves the download address, then the HTTP Request2 node downloads the video as binary data (data) before sending it via the Send a video2 node.

YouTube: A JavaScript Code node extracts the unique identifier (ID) from the link. This ID is injected into the HTTP Request3 node to call the download API, and the file is sent via the Send a video1 node.

Summary: This architecture creates a hybrid assistant capable of answering users' questions and serving as a universal media downloader in a fully automated manner.
