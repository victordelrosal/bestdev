# flux

> Your dynamic productivity system in constant flow - Now cloud-based! ☁️

## ⚠️ **CRITICAL: READ [DATA_LOSS_WARNING.md](./DATA_LOSS_WARNING.md) BEFORE MAKING ANY CODE CHANGES**

flux is a cloud-based web application that serves as your personal command center, combining note-taking, task management, project tracking, and AI-powered assistance into a unified, beautiful interface.

## ✨ Features

### 🎯 Core Functionality
- **📌 Sticky Notes** - Quick capture with drag-and-drop organization
- **📊 Quick Todos** - Fast task lists with checkmarks and drag-to-reorder
- **📝 Zen Writing** - Distraction-free markdown editor with TipTap
- **🤖 AI Chat** - Ensemble mode with Claude, ChatGPT, and Gemini
- **🎮 Mini Games** - Built-in games for break time
- **📺 Old TV** - Browse curated YouTube channels

### ☁️ Cloud-Based Architecture
- **🔄 Real-time Sync** - Supabase cloud sync across devices
- **💾 Instant Backup** - localStorage for offline access
- **🌐 Browser-Based** - No installation required
- **⚡ Fast & Responsive** - Next.js for optimal performance

## 🚀 Quick Start

### Prerequisites
- Node.js 20+
- Supabase account (for cloud sync)

### Installation

```bash
# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Add your Supabase credentials to .env.local

# Run development server
npm run dev

# Open http://localhost:3000
```

### Production Build

```bash
# Build for production
npm run build

# Start production server
npm run start
```

## 📖 Usage

### First Launch

1. **Open flux** in your browser (http://localhost:3000 or your deployment URL)
2. **Sign in** with your Supabase account
3. Start creating sticky notes, todos, or writing!

### Key Features

#### Cloud Sync
- All your data automatically syncs to Supabase
- localStorage backup for instant offline access
- Real-time updates across devices

#### Sticky Notes
- Click anywhere to create a new sticky note
- Drag to reposition
- Color coding and alarms
- Hydrate/dehydrate to manage screen space

#### Quick Todos
- Create lists with checkmarks
- Drag items to reorder
- First line is the list name (bold & underlined in edit mode)
- Click anywhere outside to auto-save

## 🛠️ Development

### Build Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Next.js development server |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |

### Project Structure

```
flux/
├── app/                    # Next.js app directory
│   ├── components/         # React components
│   │   ├── views/         # Main view components
│   │   ├── ZenEditor/     # Markdown editor
│   │   └── Core.tsx       # App core
│   ├── lib/               # Utilities & storage
│   │   ├── supabase*.ts   # Supabase integration
│   │   └── *Adapter.ts    # Storage adapters
│   └── hooks/             # Custom React hooks
├── public/                 # Static assets
└── package.json           # Dependencies

```

### Architecture

**Storage Layer:**
- Supabase (cloud sync)
- localStorage (instant backup)
- Real-time subscriptions for live updates

**Components:**
- Next.js 15 with App Router
- React 19 with hooks
- TipTap for rich text editing
- Tailwind CSS for styling

## 🤝 Contributing

Contributions are welcome! Please open an issue or PR.

## 📝 License

MIT License - see LICENSE file for details

## 🙏 Acknowledgments

- Built with Next.js, React, and Supabase
- Inspired by the need for a unified productivity system
- Designed for flow state and minimal friction

---

**flux** - Your productivity system in constant flow ☁️🚀
