Automated Lead Qualification via n8n and AI

This project presents an automation workflow designed on n8n to automatically capture, qualify, and process prospects based on their budget, integrating artificial intelligence for needs analysis.

Workflow

Input and Notification

n8n Form: The prospect enters their name, email, budget, and type of need.

Slack: An instant notification containing all the data is sent to a dedicated channel.

Routing (IF Node): Automatic routing of the lead based on their financial capacity (threshold of $5,000).

Premium Branch (Budget above $5,000)

Double Opt-in: A confirmation email in HTML format is sent. The system pauses via a Wait node until the prospect clicks the button linked to a Webhook.

Project Suggestions: After validation, the prospect receives a list of business ideas (E-commerce, etc.) including an "Other" option.

AI Idea Analysis: Selecting the "Other" option opens an automatic reply interface in Gmail. A Gmail Trigger intercepts the project description sent by the prospect. The AI validates the seriousness of the request (assigning the value it_is_lead). If the condition is met, the AI generates an analysis report detailing the strengths, weaknesses, and a strategic recommendation, which is sent to the prospect in a professional HTML template.

Secondary Branch (Budget below $5,000)

Storage: The prospect's contact details are immediately recorded in a Google Sheets spreadsheet.

Daily Report: Every day at 7:00 PM, a JavaScript node extracts the data and transforms it into text.

Final Decision: The AI converts this information into a clean HTML table sent directly to the project owner, allowing them to quickly decide which profiles to contact again.

Technical Stack

Orchestration: n8n
Communication: Slack, Gmail
Database: Google Sheets
Artificial Intelligence: AI and LLM Nodes (n8n)
Formatting: JavaScript, HTML / CSS templates
