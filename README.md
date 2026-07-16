MY EMAIL AGENT

This repository contains an n8n workflow export for an AI-powered email assistant. The workflow allows a user to chat with an AI agent that can help draft email content and, when requested, send the email through Gmail.

## What this workflow does

The workflow is designed to:

- Receive chat messages through an n8n chat trigger
- Use an AI agent to understand the user request
- Draft or refine email content based on the conversation
- Send emails through Gmail using a Gmail tool

## Workflow overview

The workflow includes the following nodes:

1. When chat message received
   - This is the entry point for the workflow.
   - It acts as a chat trigger so the agent can be interacted with through n8n.

2. AI Agent
   - This node coordinates the conversation and decides when to use the Gmail tool.
   - It is configured with a system prompt that explains the agent’s role as a helpful email assistant.

3. OpenAI Chat Model
   - This node connects the agent to OpenAI.
   - The workflow is currently set to use the model named "gpt-5.2".

4. Simple Memory
   - This provides short-term memory for the conversation so the agent can maintain context.

5. Send a message in Gmail
   - This is the tool that sends the composed email.
   - It uses Gmail OAuth credentials to connect to the user’s Gmail account.

## Prerequisites

Before importing and using this workflow, you will need:

- An n8n instance (self-hosted or n8n Cloud)
- An OpenAI API credential configured in n8n
- A Gmail OAuth2 credential configured in n8n
- Access to an OpenAI model supported by your account (the workflow currently points to "gpt-5.2")
- The LangChain-related n8n nodes available in your n8n environment

## How to set it up

### 1. Import the workflow

- In your n8n dashboard, go to Workflows.
- Click Import from File.
- Select the workflow JSON file in this repository.
- Import it into your n8n instance.

### 2. Configure the credentials

The workflow already references two credentials:

- OpenAI API credential named "Kodekloud"
- Gmail OAuth2 credential named "Gmail OAuth2 API"

If your credential names are different in your n8n instance, update the node settings so the workflow uses your own credentials.

### 3. Activate the workflow

- Open the imported workflow.
- Check that all nodes are connected properly.
- Activate the workflow.

### 4. Test the chat trigger

Once the workflow is active, use the chat trigger to start a conversation with the AI agent. You can then ask it to:

- Draft a professional email
- Rewrite an existing email
- Help compose a follow-up message
- Send an email through Gmail

## Example prompts

You can try prompts like:

- "Draft a polite follow-up email to a client about a missed deadline"
- "Write a short thank-you email to a colleague"
- "Send an email to example@email.com with the subject 'Project Update' and a brief message"

## Important notes

- The Gmail tool expects the AI to generate the recipient address, subject, and message content before sending.
- The workflow uses a short memory window, so it is best suited for short, focused conversations.
- If the workflow does not work immediately, the most common issues are:
  - Missing or incorrect credentials
  - The OpenAI model is not available in your account
  - Gmail OAuth authorization has not been completed

## Repository contents

- My Email Agent workflow JSON export
- This README file

