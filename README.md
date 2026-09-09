# Persona AI

> An AI-powered conversational application that lets you interact with AI personas inspired by characters from *How I Met Your Mother*.

Persona AI allows users to choose between different personalities and have conversations while the AI maintains the selected character's conversational style, personality, and perspective.

The project was built to explore **LLM-powered persona design, system prompts, REST APIs, and full-stack AI application architecture**.

---

## Features

* AI-powered conversational interface
* Multiple AI personas
* Ted persona
* Marshall persona
* Persona-specific system prompts
* Character-consistent responses
* Real-time chat experience
* React frontend
* Express.js backend
* OpenAI API integration
* REST API architecture
* Environment-based API key configuration
* Separation between frontend and backend

---

## How It Works

The application separates the user interface from the AI logic.

```text
                    User
                     │
                     ▼
              ┌──────────────┐
              │ React Client │
              └──────┬───────┘
                     │
                     │ HTTP Request
                     ▼
              ┌──────────────┐
              │ Express API  │
              └──────┬───────┘
                     │
                     ▼
             ┌─────────────────┐
             │ Persona Selector│
             └────────┬────────┘
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
        Ted Persona      Marshall Persona
             │                 │
             └────────┬────────┘
                      │
                      ▼
               System Prompt
                      │
                      ▼
                OpenAI Model
                      │
                      ▼
               AI Response
                      │
                      ▼
                React Client
```

The frontend sends the selected persona and user's message to the backend. The backend uses the corresponding system prompt to establish the AI's personality before sending the request to the OpenAI API.

---

# Architecture

The application consists of two main parts:

### Client

The React client is responsible for:

* Persona selection
* Chat interface
* User input
* Displaying conversation messages
* Communicating with the backend API

### Server

The Express server is responsible for:

* Receiving chat requests
* Selecting the appropriate persona
* Applying the persona-specific system prompt
* Communicating with OpenAI
* Returning the generated response to the client

This separation keeps the OpenAI API key on the server instead of exposing it to the browser.

---

# Tech Stack

## Frontend

* React
* Vite
* JavaScript
* CSS
* Fetch API

## Backend

* Node.js
* Express.js
* OpenAI SDK
* dotenv
* CORS

## AI

* OpenAI API
* System prompts
* Persona-based prompting

---

# Project Structure

```text
Persona-ai/
│
├── client/
│   ├── public/
│   │
│   ├── src/
│   │   ├── components/
│   │   ├── assets/
│   │   └── ...
│   │
│   ├── package.json
│   ├── vite.config.js
│   └── index.html
│
├── server/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   └── ...
│   │
│   ├── package.json
│   └── ...
│
└── README.md
```

---

# API

## Chat Endpoint

```text
POST /api/v1/chat/chats/chatMessages
```

### Request Body

```json
{
  "personaId": "ted",
  "message": "I'm confused about what I should do with my career."
}
```

The `personaId` determines which personality/system prompt is used.

Supported personas:

```text
ted
marshall
```

---

# Persona System

The core idea of the project is that the model isn't simply asked to "act like" a character in every user message.

Instead, the backend establishes the persona through a dedicated **system prompt**.

Conceptually:

```text
System Prompt
      +
User Message
      │
      ▼
   LLM
      │
      ▼
Persona-consistent response
```

This allows the application to maintain a more consistent personality throughout the conversation.

---

# Example

### Ted

```text
User:
I'm not sure whether I should follow my passion or choose
something more practical.

AI:
Sometimes the hardest part isn't figuring out what you want.
It's figuring out whether you're afraid of wanting it...
```

### Marshall

```text
User:
I'm not sure whether I should follow my passion or choose
something more practical.

AI:
Look, buddy, I think you have to ask yourself what kind
of life you actually want to wake up to every morning...
```

The exact response depends on the model and prompt configuration.

---

# Installation

## Prerequisites

Make sure you have:

* Node.js
* npm
* An OpenAI API key

---

## Clone the Repository

```bash
git clone https://github.com/Rabi-anando-sarkar/Persona-ai.git

cd Persona-ai
```

---

# Backend Setup

Navigate to the server:

```bash
cd server
```

Install dependencies:

```bash
npm install
```

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key
PORT=8000
CORS_ORIGIN=http://localhost:5173
```

Start the development server:

```bash
npm run dev
```

---

# Frontend Setup

Open another terminal:

```bash
cd client
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL provided by Vite.

---

# Environment Variables

### Server

```env
OPENAI_API_KEY=your_openai_api_key
PORT=8000
CORS_ORIGIN=http://localhost:5173
```

### Important

Never commit your `.env` file or expose your OpenAI API key in frontend code.

The API key should remain exclusively on the backend.

Add the following to `.gitignore`:

```gitignore
.env
.env.local
```

---

# Design Goals

The main goal of Persona AI was to explore how **system prompting can control the behavior and personality of an LLM**.

Instead of building another generic chatbot, this project focuses on:

* Persona consistency
* System prompts
* Backend-controlled AI behavior
* Clean frontend/backend separation
* API-based LLM integration
* Building an actual AI product around an LLM

---

# What I Learned

Through this project, I explored:

* OpenAI API integration
* OpenAI SDK
* System prompts
* Persona-based prompting
* REST API design
* Express.js controllers and routes
* Frontend/backend communication
* CORS configuration
* Environment variables
* API key security
* Building conversational AI interfaces
* Structuring an AI application as a full-stack project

---

# Future Improvements

Possible improvements include:

* Add conversation memory
* Persist chat history
* Add more personas
* Add persona-specific UI themes
* Add streaming responses
* Add authentication
* Add database-backed conversations
* Add message timestamps
* Add conversation history/sidebar
* Add model selection
* Add response regeneration
* Add production deployment
* Add rate limiting and usage controls

---

# Disclaimer

The personas in this project are inspired by fictional characters from *How I Met Your Mother* and are intended for demonstration and educational purposes.

This project is not affiliated with or endorsed by the creators, producers, or rights holders of the show.

---

# Author

**Rabi-anando-sarkar**

GitHub:
https://github.com/Rabi-anando-sarkar

---

## Project

**Persona AI**

Built to explore practical LLM application development, persona prompting, and full-stack AI engineering.
