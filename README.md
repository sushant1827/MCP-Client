# MCP-Client

This repository contains an n8n workflow that integrates a chat interface with an AI agent powered by OpenAI's GPT-4o-mini model, using a Message Control Protocol (MCP) client for communication.

<img width="560" alt="image" src="https://github.com/user-attachments/assets/b44671b6-a096-42c2-af70-aab0004c402a" />

## Overview

The MCP Client workflow enables real-time communication between a chat interface and an AI agent, allowing for intelligent conversation flows and automated responses. The workflow is built using n8n, a node-based workflow automation platform.

## Components

The workflow consists of the following nodes:

1. **When chat message received** - A webhook trigger that initiates the workflow when a chat message is received.
2. **AI Agent** - Processes the incoming messages and generates intelligent responses using the configured language model.
3. **OpenAI Chat Model** - Utilizes OpenAI's GPT-4o-mini model to power the AI agent's responses.
4. **MCP Client** - Handles the communication protocol for message transport, connecting to an SSE endpoint at `http://localhost:5678/mcp/test1/sse`.

## Architecture

```
┌───────────────────────┐        ┌───────────────┐
│                       │        │               │
│  When chat message    ├───────►│   AI Agent    │
│      received         │        │               │
│                       │        └───────┬───────┘
└───────────────────────┘                │
                                         │
                                         │
┌───────────────────────┐        ┌───────▼───────┐
│                       │        │               │
│   OpenAI Chat Model   ├───────►│   MCP Client  │
│    (GPT-4o-mini)      │        │               │
│                       │        └───────────────┘
└───────────────────────┘
```

## Setup Requirements

1. An n8n instance
2. OpenAI API credentials
3. An accessible SSE endpoint for the MCP Client

## Configuration

1. Import the workflow JSON into your n8n instance
2. Configure your OpenAI API credentials
3. Verify or update the SSE endpoint URL in the MCP Client node settings
4. Activate the workflow

## Usage

Once configured and activated, the workflow will:

1. Listen for incoming chat messages through the webhook
2. Process the messages using the AI Agent and OpenAI language model
3. Communicate responses back through the MCP protocol

## Development

To modify or extend this workflow:

1. Access your n8n editor
2. Locate the MCP Client workflow
3. Make your desired changes to the node configurations
4. Save and activate your updated workflow
