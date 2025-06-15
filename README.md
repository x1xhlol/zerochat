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
- Direct integration with multiple AI providers (OpenRouter, Groq, etc.)
- User-controlled API key management
- Secure code execution sandbox (Python, JavaScript, HTML) via E2B
- Email Verification & Two-Factor Authentication (2FA)
- Chat Sharing & Forking
- Chat Archiving, Renaming, and Deletion

**📱 Mobile-First Experience**
- PWA-ready for native app installation
- Touch-optimized interface
- Perfect responsive design for all screen sizes

## ✨ Features

### 🤖 **Multi-Model AI Support**
- **OpenRouter Integration** - Access OpenAI, Anthropic, Gemini, xAI, Groq, Deepseek, and over 30+ models.
- **User-Controlled API Keys** - No vendor lock-in, use your own keys securely stored.

### 💻 **Secure Code Execution**
- **E2B Sandbox** - Execute Python, JavaScript, and render HTML previews in a secure, isolated environment.
- **Real-time Output Streaming** - See code execution results as they happen.
- **Session Management** - Robust E2B session handling with automatic cleanup via Vercel Cron.

### 🔄 **Real-Time Experience**
- **Live Chat Sync** - Messages appear instantly across devices using Redis Pub/Sub and Server-Sent Events.
- **Typing Indicators** - Know when AI or other users are responding.
- **Stream Resumption** - Designed to handle connection drops gracefully (feature in progress).
- **Presence Indicators** - Real-time connection status.

### 📁 **Advanced Organization**
- **Project Management** - Group conversations with custom colors.
- **Chat Management** - Archive, rename, and delete chats directly from the sidebar.
- **Smart Search** - Find any conversation instantly.
- **Pin Important Chats** - Keep key conversations at the top.
- **Export Everything** - Download your complete chat history.

### 🔐 **Security & Authentication**
- **Email Verification** - Secure sign-up process using Resend for email delivery.
- **Two-Factor Authentication (2FA)** - Enhance account security with email-based 2FA.
- **Encrypted API Keys** - User-provided API keys are encrypted at rest.
- **Secure Session Management** - Robust session handling using Redis.

### 🔗 **Sharing & Collaboration**
- **Shareable Chat Links** - Create public links to share specific chat sessions.
- **Forkable Chats** - Allow others to fork shared chats into their own workspace.

### 📱 **Mobile-First Design**
- **PWA Ready** - Install as a native app on supported devices.
- **Touch Optimized** - Interface designed for easy touch interaction.
- **Responsive Breakpoints** - Looks great on any screen size, from mobile to desktop.
- **iOS Safe Areas** - Native feel on all devices.

### 🎨 **Beautiful UI/UX**
- **Glass Morphism Inspired** - Modern, translucent design elements for a polished look.
- **Dark/Light Mode** - Automatic theme switching based on system preference.
- **Accessibility First** - WCAG compliant design, screen reader friendly.

## 🚀 Quick Start

### One-Click Deploy

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/x1xhlol/zerochat)

*Note: You will need to set up environment variables on Vercel.*

### Manual Setup

```bash
# Clone the repository
git clone https://github.com/x1xhlol/zerochat.git
cd zerochat

# Install dependencies
npm install

# Set up environment variables (see below)
cp .env.example .env.local
# Edit .env.local with your actual values

# Start development server
npm run dev
```

### Environment Configuration (`.env.local`)

```env
# Required for Core Functionality
REDIS_URL="your_upstash_redis_url_or_other_redis_instance"
BLOB_READ_WRITE_TOKEN="your_vercel_blob_read_write_token" # For file uploads/profile pictures
ENCRYPTION_SECRET="generate_a_strong_32_byte_secret_key" # Used for encrypting API keys. Use `openssl rand -hex 32`

# Required for Code Execution
E2B_API_KEY="your_e2b_api_key"

# Required for Email Verification & 2FA
RESEND_API_KEY="your_resend_api_key" # From Resend.com, ensure domain is verified
NEXT_PUBLIC_APP_URL="http://localhost:3000" # Change to your deployed URL in production

# Required for Scheduled Cleanup (Vercel Cron or other)
CLEANUP_API_TOKEN="generate_a_secure_random_string" # Protects the /api/cleanup/sessions endpoint

# Optional AI Provider API Keys (users can also set these in their profile)
# These act as default fallbacks if a user hasn't set their own.
OPENROUTER_API_KEY=""
GROQ_API_KEY=""
# ANTHROPIC_API_KEY=""
# OPENAI_API_KEY=""
# ... any other models supported via OpenRouter or directly

# KV_URL=""
# KV_REST_API_URL=""
# KV_REST_API_TOKEN=""
# KV_REST_API_READ_ONLY_TOKEN=""
```

**Important:**
- For `ENCRYPTION_SECRET`, generate a secure key using a command like `openssl rand -hex 32`.
- For `RESEND_API_KEY`, you need an account with [Resend](https://resend.com) and a verified domain for sending emails.
- `NEXT_PUBLIC_APP_URL` should be your application's base URL. It's used for constructing verification links in emails.
- `CLEANUP_API_TOKEN` is a secret token you define to secure the session cleanup cron job endpoint.

## 🏗️ Architecture

Zero Chat is built with modern, scalable technologies:

- **Frontend**: Next.js 15 (App Router), TypeScript, Tailwind CSS, shadcn/ui.
- **Backend**: Next.js API Routes, Server Actions.
- **Database/Cache**: Redis (Upstash recommended) for session management, chat history, real-time sync.
- **AI Integration**: Vercel AI SDK, OpenRouter for broad model access.
- **Code Execution**: E2B for secure, sandboxed execution of Python, JavaScript, and HTML.
- **File Storage**: Vercel Blob for profile pictures and potential future file attachments.
- **Real-time Communication**: Redis Pub/Sub and Server-Sent Events (SSE).
- **Authentication**: Custom credential-based authentication with email verification (Resend) and 2FA.
- **Scheduled Jobs**: Vercel Cron for E2B session cleanup.

## 🔧 Self-Hosting Options

### Vercel + Upstash (Recommended)
- **Frontend & Backend**: Deploy to Vercel.
- **Redis**: Use Upstash Redis (free tier available).
- **Blob Storage**: Vercel Blob (included with Vercel).
- **Email**: Resend (free tier available).
- **Code Execution**: E2B (free tier available).
- **Cron Jobs**: Vercel Cron (included with Vercel).
This setup offers a highly scalable, serverless architecture with minimal configuration.

### Traditional VPS
- **Application**: Run the Next.js app using Node.js (e.g., via Docker).
- **Redis**: Self-host a Redis instance or use a managed cloud Redis.
- **Blob Storage**: Use any S3-compatible storage service (e.g., MinIO, AWS S3). You'll need to adapt file upload logic.
- **Email**: Integrate with any email provider via Resend or adapt to another (e.g., SMTP).
- **Code Execution**: E2B cloud is still recommended for security. Self-hosting a secure code execution sandbox is complex.
- **Cron Jobs**: Use system cron or a similar scheduler to call the cleanup API endpoint.

## 🤝 Contributing

We welcome contributions! Zero Chat is built by developers, for developers.

### Development Setup
```bash
# Ensure you have Node.js (v18+ recommended) and npm/yarn/pnpm
git clone https://github.com/x1xhlol/zerochat.git
cd zerochat
npm install # or yarn install / pnpm install

# Set up your .env.local file as described above
# (For local dev, you might skip some optional keys or use mock values for non-critical services)

npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### Contributing Guidelines
1. **Fork the repository.**
2. **Create a feature branch** (`git checkout -b feature/your-amazing-feature`).
3. **Make your changes.** Ensure code is well-formatted (run `npm run lint` and `npm run format`).
4. **Test your changes thoroughly.** Add unit or integration tests where appropriate.
5. **Submit a pull request** to the `main` branch with a clear description of your changes.

### Roadmap
- [ ] Voice messages and transcription
- [ ] Team workspaces and advanced collaboration features
- [ ] Local AI model support (e.g., Ollama integration)
- [ ] Internationalization (i18n) / Multi-language support
- [ ] Enhanced file management within code execution sandbox

## 🛡️ Privacy & Security

- **Data Ownership**: Your conversations and data stay on your infrastructure (Redis, Vercel Blob).
- **API Key Security**: User-provided AI API keys are encrypted at rest using `ENCRYPTION_SECRET`.
- **Secure Sessions**: Robust session management with HTTP-only cookies and Redis.
- **No Default Telemetry**: Zero Chat does not send telemetry or analytics to external services by default.
- **GDPR & Data Rights**: Built-in features for data export and account deletion.
- **Content Security Policy (CSP)**: Configured for enhanced security (review `next.config.mjs`).
- **Rate Limiting**: Implemented on sensitive API endpoints.

## 📄 License

MIT License - see [LICENSE.md](LICENSE.md) for details.

## 🙏 Acknowledgments

- **Theo Browne (t3dotgg)** for inspiring the creation of an open-source alternative to t3.chat.
- All contributors and the open-source community.

---

**Zero Chat** - Own your AI conversations. Built by developers, for developers.

[⭐ Star on GitHub](https://github.com/x1xhlol/zerochat) | [🚀 Deploy Now](https://vercel.com/new/clone?repository-url=https://github.com/x1xhlol/zerochat)
