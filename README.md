# Polaris AI Agents UI

[![License](https://img.shields.io/badge/license-Proprietary-blue.svg)]()
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)]()

Build and manage AI agents with visual workflows.

## 📚 Documentation

👉 **[Read the Full Documentation](docs/index.md)**

Quick links:
- [Getting Started](docs/getting-started.md)
- [Agent Management Guide](docs/guides/agent-management.md)
- [Visual Editor & Workflows](docs/guides/visual-editor.md)
- [Settings & Administration](docs/guides/settings.md)
- [Best Practices](docs/guides/best-practices.md)
- [FAQ & Troubleshooting](docs/faq.md)

## What is Polaris AI?

Polaris AI Agents UI is an enterprise platform for:

✨ **Create AI Agents** – Intuitive interface to design agent teams  
🔄 **Version & Manage** – Save, version, and revert configurations  
📊 **Visual Workflows** – Design agent orchestration with a graph editor  
🧠 **Model Integration** – Connect OpenAI, Claude, AWS Bedrock, and more  
🔗 **External Agents** – Integrate agents from other systems  
🛠️ **MCP Tools** – Register and use Model Context Protocol servers  
👥 **Multi-Tenant** – Organize agents per workspace/tenant

## Getting Started

### Quick Start (Development)

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Prerequisites

- Node.js 20+
- npm 10+
- Backend service running at `http://localhost:8000`
- Modern browser (Chrome, Firefox, Safari, Edge)

## Features

| Feature | Description |
|---------|-------------|
| 🤖 Agent Builder | Create agents with system messages, tools, and models |
| 📋 Version Control | Save, export, import, and manage agent versions |
| 🎯 Visual Editor | Graph-based node editor for workflow design |
| 🏗️ Multi-Node Support | Team, Assistant, Actor-Critic, Group of Agents, External Agent nodes |
| 📦 Model Registry | Register and manage LLM providers |
| 🔌 MCP Integration | Connect Model Context Protocol servers |
| 👤 External Agents | Reference agents from external systems |
| 🏢 Multi-Tenant | Organize agents per workspace |
| 🔐 Role-Based Access | Admin and user permission levels |

## Available Scripts

```bash
npm run dev           # Start development server
npm run build         # Production build
npm run preview       # Preview production build
npm run lint          # Run ESLint
npm run paraglide:build # Compile i18n translations
npm run dev:storybook # Start Storybook for component development
```

## Project Structure

```
atos-ai-agents-ui/
├── docs/                 # GitHub Pages documentation
│   ├── index.md
│   ├── getting-started.md
│   ├── faq.md
│   ├── guides/
│   │   ├── agent-management.md
│   │   ├── visual-editor.md
│   │   ├── settings.md
│   │   └── best-practices.md
│   └── _config.yml
├── src/
│   ├── components/       # React components
│   ├── views/           # Page views
│   ├── manager.ts       # API manager
│   ├── provider.tsx     # Context provider
│   ├── main.tsx         # Entry point
│   └── index.css
├── public/              # Static assets
├── vite.config.ts       # Vite configuration
├── tsconfig.json        # TypeScript config
├── eslint.config.js     # ESLint config
├── package.json
└── README.md
```

## Technology Stack

- **Frontend**: React 19 + TypeScript
- **Build**: Vite 7
- **Routing**: React Router 7
- **UI**: Tailwind CSS + DaisyUI
- **Icons**: React Icons
- **State**: Zustand
- **i18n**: Paraglide.js
- **Graphs**: XYFlow (React Flow)
- **Testing**: Vitest + Playwright
- **Storybook**: Component development & documentation

## Development

### Environment Setup

```bash
# Clone the repository
git clone https://github.com/IN-ATOS-AARA/atos-ai-agents-ui.git
cd atos-ai-agents-ui

# Install dependencies
npm install

# Configure environment (if needed)
# The app proxies to http://localhost:8000 by default

# Start development server
npm run dev
```

### Backend Integration

The app expects these backend endpoints (proxied by Vite):

- `GET /api/agents` – List agents
- `POST /api/agents` – Create agent
- `GET /api/models` – List models
- `GET /me` – Current user info
- And more (see [manager.ts](src/manager.ts))

### Code Style

ESLint configuration is in `eslint.config.js`. Run:

```bash
npm run lint
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Deployment

### GitHub Pages

Documentation is automatically hosted via GitHub Pages using Jekyll.

To enable:

1. Go to repository **Settings → Pages**
2. Set source to `docs/` folder
3. Choose theme (currently using `just-the-docs`)

Documentation will be available at: `https://username.github.io/atos-ai-agents-ui/`

### Production Build

```bash
npm run build
```

Outputs to `dist/` folder. Deploy to your hosting platform.

## Contributing

1. Create a feature branch
2. Make changes
3. Update documentation if needed
4. Submit pull request

## Support

- 📖 [Read the documentation](docs/index.md)
- 🐛 [Report issues](https://github.com/IN-ATOS-AARA/atos-ai-agents-ui/issues)
- 📧 Email: dl-atospolarisaisupport@atos.net
- 💬 Contact your administrator

## License

Proprietary – Atos 2025

## Acknowledgments

Built with:

- [React](https://react.dev)
- [Vite](https://vitejs.dev)
- [Tailwind CSS](https://tailwindcss.com)
- [Just the Docs](https://just-the-docs.github.io/just-the-docs/) Jekyll theme

---

**Version:** 1.0.0  
**Last Updated:** May 2026
