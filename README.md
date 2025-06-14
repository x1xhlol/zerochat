# Zero Chat

**The Open Source Alternative to t3.chat** 🚀

A modern, self-hostable AI chat application with real-time messaging, multiple AI model support, and beautiful responsive design. Built with Next.js 15 and designed for developers who want full control over their AI chat experience.



**🔓 Open Source & Self-Hostable**
- Full MIT license - modify, distribute, and use commercially
- Deploy on your own infrastructure with complete data ownership
- No vendor lock-in or platform dependencies

**🎛️ Advanced Features**
- Real-time chat synchronization across devices
- Color-coded project organization system
- Direct integration with multiple AI providers
- User-controlled API key management

**📱 Mobile-First Experience**
- PWA-ready for native app installation
- Touch-optimized interface with swipe gestures
- Perfect responsive design for all screen sizes

## ✨ Features

### 🤖 **Multi-Model AI Support**
- **OpenRouter Integration** - Access OpenAI, Anthropic, Gemini, Grok, Groq and Deepseek, with over 30+ models
- **User-Controlled API Keys** - No vendor lock-in, use your own keys

### 🔄 **Real-Time Experience**
- **Live Chat Sync** - See messages appear instantly across devices
- **Typing Indicators** - Know when AI or other users are responding
- **Stream Resumption** - Never lose a response, even on connection drops
- **Presence Indicators** - Real-time connection status

### 📁 **Advanced Organization**
- **Project Management** - Group conversations with custom colors
- **Smart Search** - Find any conversation instantly
- **Pin Important Chats** - Keep key conversations at the top
- **Export Everything** - Download your complete chat history

### 📱 **Mobile-First Design**
- **PWA Ready** - Install as a native app
- **Touch Optimized** 
- **Responsive Breakpoints** - Perfect on any screen size
- **iOS Safe Areas** - Native feel on all devices

### 🎨 **Beautiful UI/UX**
- **Glass Morphism** - Modern, translucent design elements
- **Dark/Light Mode** - Automatic theme switching
- **Smooth Animations** - 60fps interactions and transitions
- **Accessibility First** - WCAG compliant, screen reader friendly

## 🚀 Quick Start

### One-Click Deploy

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/x1xhlol/zerochat)

### Manual Setup

```bash
# Clone the repository
git clone https://github.com/x1xhlol/zerochat.git
cd zerochat

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local

# Start development server
npm run dev
```

### Environment Configuration

```env
# Required
REDIS_URL=your_redis_url
BLOB_READ_WRITE_TOKEN=your_vercel_blob_token

# Optional defaults (users can override in settings)
GROQ_API_KEY=your_groq_key
```

## 🏗️ Architecture

Zero Chat is built with modern, scalable technologies:

- **Frontend**: Next.js 15 with App Router, TypeScript, Tailwind CSS
- **Backend**: Next.js API routes with Redis for real-time data
- **AI Integration**: AI SDK with OpenRouter for unified model access
- **Storage**: Vercel Blob for file attachments
- **Real-time**: Redis Pub/Sub with Server-Sent Events
- **Authentication**: Custom session management with Redis

## 🔧 Self-Hosting Options

### Vercel + Upstash (Recommended)
- Deploy frontend to Vercel
- Use Upstash Redis for data layer
- Vercel Blob for file storage
- Zero configuration required


### Traditional VPS
- Any Node.js hosting provider
- Redis instance (local or cloud)
- S3-compatible storage for files

## 🤝 Contributing

We welcome contributions! Zero Chat is built by developers, for developers.

### Development Setup
```bash
git clone https://github.com/x1xhlol/zerochat.git
cd zerochat
npm install
npm run dev
```

### Contributing Guidelines
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes with tests
4. Submit a pull request

### Roadmap
- [ ] Voice messages and transcription
- [ ] Team workspaces and collaboration
- [ ] Advanced prompt templates
- [ ] Local model support (Ollama)
- [ ] Multi-language support

## 🛡️ Privacy & Security

- **Data Ownership**: Your conversations stay on your infrastructure
- **API Key Security**: Keys are encrypted and user-controlled
- **Session Management**: Secure Redis-based sessions
- **No Tracking**: Zero telemetry or analytics by default
- **GDPR Compliant**: Built-in data export and deletion

## 📄 License

MIT License - see [LICENSE](LICENSE.md) for details.

## 🙏 Acknowledgments

- **Theo Browne** for inspiring me with t3.chat to build an open source alternative
- **Vercel** for the AI SDK and hosting platform
- **OpenRouter** for unified AI model access
- **shadcn/ui** for the beautiful component library

---

**Zero Chat** - Own your AI conversations. Built by developers, for developers.

[⭐ Star on GitHub](https://github.com/x1xhlol/zerochat) | [🚀 Deploy Now](https://vercel.com/new/clone?repository-url=https://github.com/x1xhlol/zerochat)
