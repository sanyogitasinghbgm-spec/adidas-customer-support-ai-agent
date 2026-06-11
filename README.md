# 🤖 Alex — AI-Powered WhatsApp Customer Support Agent

An end-to-end AI Agent for WhatsApp customer support, replicating a real-world enterprise workflow. Alex dynamically calls tools, queries a live database, auto-generates support tickets, and responds to customers in real time via WhatsApp — 24/7, no human intervention needed.

---

## 🎯 What It Does

A customer messages on WhatsApp, and Alex instantly:
- Answers return policy and FAQ queries
- Tracks live order status by order ID
- Fetches real-time product and inventory data
- Creates support tickets with an assigned agent automatically

---

## ⚙️ Architecture

```
WhatsApp → Twilio → n8n Trigger → Return Policy Node → AI Agent (Groq) → Airtable Tools → Response back to WhatsApp
```

---

## 🚀 Key Features

- **Return Policy Queries** — Static context injection so the agent never hallucinates
- **Live Order Tracking** — Fetches real-time order status by order ID from Airtable
- **Inventory Queries** — Checks live product and pricing data
- **Auto Ticket Creation** — Creates support tickets with a default assigned agent
- **Production Webhook** — Fully automated, no manual execution needed
- **Natural Conversation Flow** — Professional tone via prompt engineering

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow orchestration and AI Agent configuration |
| Twilio | WhatsApp channel integration |
| Airtable | Live backend database (Inventory, Orders, Tickets) |
| Groq + OpenAI GPT OSS 120B | LLM powering the AI Agent |
| Webhook | Production-ready real-time message routing |

---

## 🗄️ Airtable Database Structure

**Inventory Table**
- Product ID, Name, Price, Color, Category

**Orders Table**
- Order ID, Product ID, Customer Name, Status (Pending/Cancelled/Delivered)

**Tickets Table**
- Ticket ID, Issue Description, Customer Name, Status, Assigned Agent

---

## 🔧 Setup Guide

### 1. Prerequisites
- n8n account (cloud or self-hosted)
- Twilio account with WhatsApp Sandbox enabled
- Airtable account
- Groq API key (free at console.groq.com)

### 2. Twilio Setup
1. Go to Twilio Console → Messaging → Try WhatsApp
2. Note your **Account SID** and **Auth Token**
3. Join the sandbox by sending `join <your-code>` to the Twilio sandbox number

### 3. Airtable Setup
1. Create a base with 3 tables: `Inventory`, `Orders`, `Tickets`
2. Add fields as per the structure above
3. Go to **Developer Hub** → Generate an API key
4. Note your **Base ID** from the URL

### 4. n8n Workflow Setup
1. Import `workflow.json` into your n8n instance
2. Configure credentials:
   - **Twilio** — Add Account SID + Auth Token
   - **Airtable** — Add API Key
   - **Groq** — Add API Key
3. Update the **Return Policy Node** with your actual return policy text
4. Update the **Twilio Webhook URL** in Twilio Sandbox Settings with your n8n webhook URL
5. Set workflow to **Published/Active**

### 5. Test It
Send a WhatsApp message to your Twilio sandbox number and Alex will respond!

---

## 💬 Sample Conversations

**Return Policy Query**
```
User: What is your return policy?
Alex: Our return policy allows returns within 5 days of purchase. Items must be unused and in original packaging...
```

**Order Tracking**
```
User: What is the status of my order ID 5?
Alex: Order ID 5 is currently cancelled. Please contact support if you need further assistance.
```

**Ticket Creation**
```
User: I'm facing an issue with my shoe size.
Alex: I'm sorry to hear that! Could you please share your full name so I can log this for our team?
User: Sanyogita Singh
Alex: Thanks! I've submitted this to our team. They'll get back to you shortly.
```

---

## 📸 Screenshots

> Add screenshots here:
> - n8n full workflow

<img width="480" height="223" alt="image" src="https://github.com/user-attachments/assets/b30f7076-e31e-44c9-9609-0186573f1478" />

> - WhatsApp conversation
 
<img width="429" height="480" alt="image" src="https://github.com/user-attachments/assets/49fd2cb2-2c54-49b7-aef4-50ffa6ecc0fc" />

> - Airtable database

<img width="800" height="283" alt="image" src="https://github.com/user-attachments/assets/9f010346-e2a9-4b03-9ab0-309092f60c18" />

> - Live ticket creation

<img width="480" height="186" alt="image" src="https://github.com/user-attachments/assets/cf0d463b-6de1-4c6f-b9bc-2a25b356ae3c" />

---

## 🤝 Connect

Feel free to fork, customize, and expand this for your own business use case!
