# Refuge Chat

A modern chat application that helps people experiencing or about to experience homelessness by providing natural language access to resources and information. The system consists of a React frontend and a Node.js/Express backend, powered by local LLM inference.

## 🏗️ Architecture

This monorepo contains two main components:

- **refuge-chat-frontend**: React-based chat interface
- **refuge-chat-api**: Node.js/Express backend with LLM integration

## 🚀 Features

- **Natural Language Queries**: Ask questions about resources in plain English
- **Real-time Chat Interface**: Modern, responsive chat UI with message history
- **Local LLM Processing**: Privacy-focused, runs entirely on your machine
- **Type-Safe**: Built with TypeScript for reliability and better developer experience
- **RESTful API**: Express backend with structured endpoints
- **Accessible UI**: Built with shadcn/ui components for accessibility out of the box
- **Dark Mode Support**: Automatic theme support through shadcn/ui

## 🛠️ Tech Stack

### Frontend
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **Routing**: React Router DOM
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui (Radix UI primitives)
- **Icons**: Lucide React

### Backend
- **Runtime**: Node.js
- **Framework**: Express
- **LLM Runtime**: Ollama with Llama 2
- **Language**: TypeScript/JavaScript

## 📋 Prerequisites

- **Node.js** 18+ 
- **npm** or yarn
- **Ollama** (for LLM inference)

## 🔧 Installation

### 1. Clone the Repository with Submodules
```bash
git clone --recursive <your-repo-url>
cd refuge-chat

# If you already cloned without --recursive:
git submodule update --init --recursive
```

### 2. Install Ollama and Llama 2

**Install Ollama:**

- **macOS/Linux:**
```bash
  curl -fsSL https://ollama.com/install.sh | sh
```

- **Windows:** Download from [ollama.com](https://ollama.com/download)

**Pull Llama 2 model:**
```bash
ollama pull llama2
```

Verify installation:
```bash
ollama list
```

**Start Ollama service:**
```bash
ollama serve
```

The Ollama API will be available at `http://localhost:11434`

### 3. Set Up the Backend
```bash
cd refuge-chat-api

# Install dependencies
npm install

# Create environment file (if needed)
cp .env.example .env

# Start the backend server
npm start
# or for development with hot reload:
npm run dev
```

The API will be available at: http://localhost:8000 (or your configured port)

### 4. Set Up the Frontend
```bash
cd refuge-chat-frontend

# Install dependencies
npm install

# Create environment file (if needed)
cp .env.example .env
# Update VITE_API_URL=http://localhost:8000

# Start the development server
npm run dev
```

The frontend will be available at: http://localhost:5173




## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with [shadcn/ui](https://ui.shadcn.com/)
- Powered by [Ollama](https://ollama.com/)
- LLM: [Llama 2](https://ai.meta.com/llama/)

## 📞 Support

For issues and questions, please open an issue in the GitHub repository.
