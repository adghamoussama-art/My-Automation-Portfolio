Automated Lead Qualification via n8n and AI
This project presents an automation workflow designed on n8n to capture, qualify, and process leads automatically based on their budget, integrating artificial intelligence for needs analysis.

Workflow

1. Entry and Notification
n8n Form: The prospect enters their name, email, budget, and type of need.
Slack: Instant notification sent with all submitted data to a dedicated channel.
Routing (IF Node): Automatic lead routing based on financial capacity ($5,000 threshold).

2. Premium Branch (Budget over $5,000)
Double Opt-in: Confirmation email sent in HTML format. The system pauses via a Wait node until the button linked to a Webhook is clicked.
Project Suggestions: After validation, the prospect receives a list of business ideas (E-commerce, etc.) including an "Other" option.
Idea Analysis by AI: Selecting the "Other" option opens an automated response interface in Gmail. A Gmail Trigger intercepts the project description sent by the prospect. The AI validates the seriousness of the request (assigning the value it_is_lead). If the condition is met, the AI generates an analysis report detailing strengths, weaknesses, and strategic advice, sent to the prospect in a professional HTML template.

3. Secondary Branch (Budget under $5,000)
Storage: Immediate logging of the prospect's contact information in a Google Sheets table.
Daily Report: Every day at 7:00 PM, a JavaScript node extracts the data and transforms it into text.
Final Decision: The AI converts this information into a clean HTML table sent directly to the project owner, allowing them to quickly decide which profiles to contact back.

Tech Stack
Orchestration: n8n
Communication: Slack, Gmail
Database: Google Sheets
Artificial Intelligence: AI and LLM Nodes (n8n)
Formatting: JavaScript, HTML / CSS templates
