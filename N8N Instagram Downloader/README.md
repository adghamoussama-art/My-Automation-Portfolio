#  Automated Sales & Order Management with n8n

A fully automated **sales and order management system** built with **n8n**, **Telegram**, **Google Sheets**, **Gemini AI**, **webhooks**, and **Gmail**.

The workflow allows customers to interact with an AI-powered Telegram bot to browse products, check stock availability, and place orders — while automating the entire process from order creation to owner approval, stock updates, and customer confirmation.

## 🔄 How It Works

### 1. 🛒 Customer Order

The customer interacts with the Telegram bot and can:

* Browse available products
* Ask questions about products
* Check product availability
* Place an order through the AI Agent

The AI Agent understands the customer's request and retrieves the required product and order information from **Google Sheets**.

### 2. 📋 Order Creation

Once an order is placed, the workflow:

* Generates or retrieves a unique **Order ID**
* Stores the order information in Google Sheets
* Retrieves the customer's Telegram Chat ID
* Collects the required product and order details
* Prepares the order for owner approval

### 3. 📧 Owner Approval

After the order is created, **Gemini AI** generates a professional HTML email containing the order details.

The email is sent to the owner for approval through Gmail.

The owner can securely approve the order using a **webhook** connected to the workflow.

### 4. 📦 Stock & Order Processing

Once the owner approves the order, a second workflow is triggered.

It automatically:

* Updates the order status
* Updates the product stock
* Records the completed order
* Generates a professional HTML confirmation email
* Sends the confirmation directly to the customer

The entire process happens automatically without requiring manual data entry.

## 🛡️ Security & Owner Mode

The workflow includes a dedicated **owner mode** protected by a security code.

Authorized owners can access internal business operations such as:

* Viewing order information
* Accessing product data
* Checking internal Google Sheets
* Requesting business reports by email

Customers are strictly limited to customer-facing actions such as **product inquiries and purchasing**.

This separation prevents customers from accessing sensitive business information while keeping the ordering experience simple and automated.

## 🚨 Automatic Error Handling

The workflow also includes an automated error-handling system.

If an error occurs during the process, the system:

* Detects the failed operation
* Sends an error notification to the customer through Telegram
* Retrieves the customer's Chat ID when necessary
* Clears the stored Chat ID after the process is completed

This ensures that failed operations are handled automatically instead of leaving the customer without a response.

## 🧩 Technologies Used

* **n8n** — Workflow automation and orchestration
* **Telegram Bot API** — Customer communication
* **Google Sheets** — Product, order, and customer data management
* **Gemini AI** — AI Agent and HTML email generation
* **Gmail** — Automated owner and customer emails
* **Webhooks** — Secure order approval and workflow communication
* **JavaScript** — Custom workflow logic and data processing

## 🏗️ Workflow Architecture

The system is divided into multiple automated stages:

```text
Customer
   ↓
Telegram Bot
   ↓
AI Agent
   ↓
Product & Order Data
(Google Sheets)
   ↓
Create Order
   ↓
Generate Order ID
   ↓
Gemini AI
   ↓
Owner Approval Email
   ↓
Secure Webhook
   ↓
Order Approved
   ↓
Update Stock & Order
   ↓
Generate Confirmation Email
   ↓
Customer Confirmation
```

An additional error-handling path monitors the workflow and automatically notifies the customer if something goes wrong.

## 🎯 Project Goal

The goal of this project was to build a **complete automated sales process** that reduces manual work while keeping business data secure.

From the customer's first message to the final confirmation, the system handles **communication, product lookup, order creation, approval, stock management, notifications, and error handling automatically**.

This project demonstrates practical experience with **n8n workflow design, AI agents, API integrations, webhooks, data management, authentication, automation logic, and real-world business processes**.
