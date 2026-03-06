# AI-Powered-Email-Classification-Automated-Response-System
This project is a sophisticated n8n workflow designed to automate customer service by classifying incoming Gmail messages and generating context-aware drafts using OpenAI's GPT-4.

# Project Overview
This project is an advanced n8n automation workflow designed to streamline customer service operations. It automatically monitors a Gmail inbox, analyzes incoming messages using OpenAI (GPT-4), and intelligently branches into different operational paths based on the email content (Classification).

The goal is to reduce human response time by automatically preparing draft replies for common inquiries and order requests.

# Key Features
Automated Triggering: The system listens for new emails in real-time via the Gmail API.

Intelligent Classification: Uses LLMs to distinguish between an Order (purchase request) and an Inquiry (support/question).

Dynamic Routing: A logical switch directs the workflow to different response templates based on the AI's decision.

Contextual Draft Generation: The AI generates a professional response draft tailored to the customer's specific message, ready for human review.

# Technical Implementation
The architecture consists of several integrated layers:

Ingestion Layer: Gmail Trigger node captures the snippet and payload of incoming mail.

Intelligence Layer: A Basic LLM Chain connected to GPT-4 processes the natural language.

Logic Layer: A Switch node routes the data based on the AI-generated label.

Action Layer: Gmail "Create Draft" nodes generate the final output in the user's account.

# Challenges & Engineering Solutions
During development, a significant technical hurdle was encountered with the standard n8n Text Classifier node:

The Issue: A Failed to parse: Expected object, received array error occurred because the AI output didn't match the node's strict JSON Schema requirements.

The Fix: I engineered a more robust solution by replacing the classifier with a Basic LLM Chain and a Switch Node. This provided granular control over the prompt and ensured stable data parsing, making the system 100% reliable.

# Tech Stack
n8n: Workflow Orchestration.

OpenAI GPT-4: Large Language Model for text analysis and generation.

Google Workspace API: For Gmail integration.
