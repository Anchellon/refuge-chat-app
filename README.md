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

## 🔌 API Endpoints

### POST /api/chat
Send a message and receive an LLM-generated response.

**Request:**
```json
{
  "message": "What shelters are available nearby?",
  "history": []
}
```

**Response:**
```json
{
  "response": "Here are the shelters in your area...",
  "timestamp": "2024-01-01T12:00:00Z"
}
```

### GET /api/health
Health check endpoint to verify the API is running.

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2024-01-01T12:00:00Z"
}
```

## 🧪 Development

### Frontend Development
```bash
cd refuge-chat-frontend
npm run dev          # Start dev server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

### Backend Development
```bash
cd refuge-chat-api
npm run dev          # Start with hot reload (nodemon)
npm start            # Start production server
npm test             # Run tests (if configured)
npm run lint         # Run ESLint
```

## ⚙️ Environment Variables

### Frontend (.env)
```env
VITE_API_URL=http://localhost:8000
```

### Backend (.env)
```env
PORT=8000
OLLAMA_HOST=http://localhost:11434
NODE_ENV=development
```

## 🐳 Docker Support (Optional)

Create a `docker-compose.yml` in the root:
```yaml
version: '3.8'

services:
  frontend:
    build: ./refuge-chat-frontend
    ports:
      - "5173:5173"
    environment:
      - VITE_API_URL=http://localhost:8000
    depends_on:
      - backend

  backend:
    build: ./refuge-chat-api
    ports:
      - "8000:8000"
    environment:
      - OLLAMA_HOST=http://host.docker.internal:11434
      - PORT=8000
    depends_on:
      - ollama

  ollama:
    image: ollama/ollama
    ports:
      - "11434:11434"
    volumes:
      - ollama:/root/.ollama

volumes:
  ollama:
```

## 🚀 Quick Start (All Services)
```bash
# Terminal 1: Start Ollama
ollama serve

# Terminal 2: Start Backend
cd refuge-chat-api
npm install
npm run dev

# Terminal 3: Start Frontend
cd refuge-chat-frontend
npm install
npm run dev
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 🔍 Troubleshooting

### Ollama Connection Issues
- Ensure Ollama is running: `ollama serve`
- Verify the model is downloaded: `ollama list`
- Check Ollama is accessible: `curl http://localhost:11434/api/tags`

### Backend Not Starting
- Check Node.js version: `node --version` (should be 18+)
- Verify dependencies are installed: `npm install`
- Check port 8000 is not in use: `lsof -i :8000` (macOS/Linux)

### Frontend Can't Connect to Backend
- Verify backend is running on the correct port
- Check `VITE_API_URL` in frontend `.env` file
- Check for CORS issues in browser console

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with [shadcn/ui](https://ui.shadcn.com/)
- Powered by [Ollama](https://ollama.com/)
- LLM: [Llama 2](https://ai.meta.com/llama/)

## 📞 Support

For issues and questions, please open an issue in the GitHub repository.
