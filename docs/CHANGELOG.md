---
layout: default
title: Changelog
nav_order: 9
---

# Changelog

All notable changes to Polaris AI Agents UI are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] – 2025-05-28

### Added

- ✨ **Agent Management**
  - Create, import, edit, and delete agents
  - Full version control (save, save as, export, import)
  - Public/private version visibility toggle
  - A2A URL sharing for agents

- 🎯 **Visual Node Editor**
  - Graph-based workflow designer
  - Support for 8 node types (Team, Model, Assistant, Actor-Critic, Group of Agents, External Agent, MCP Tool, User)
  - Drag-and-drop interface
  - Configuration panels for each node type

- ⚙️ **Settings & Administration**
  - Model provider registration (OpenAI, Claude, AWS Bedrock, Google AI, Azure, VLLM)
  - External A2A agent registration
  - MCP server registration with 3-step wizard
  - Tool discovery and verification

- 👥 **Multi-Tenant Support**
  - Tenant switching from header
  - Tenant-specific models and settings
  - Role-based access (User, Admin)
  - Tenant persistence across sessions

- 🔍 **Agent Discovery**
  - Full-text search across agents
  - Infinite scrolling agent list
  - Version chips with public indicators
  - Pagination in all list views

- 📱 **User Experience**
  - Responsive design (mobile, tablet, desktop)
  - Light/dark theme toggle
  - Toast notifications (info, warning, error)
  - Accessibility features (ARIA labels, keyboard navigation)

- 📚 **Documentation**
  - Comprehensive user manual
  - Getting started guide
  - Task-based workflow guides
  - Best practices documentation
  - FAQ and troubleshooting
  - API reference
  - Quick reference cheat sheet

- 🏗️ **Developer Experience**
  - React 19 + TypeScript
  - Vite build tool
  - ESLint + Prettier integration
  - Storybook for components
  - Vitest + Playwright for testing
  - GitHub Pages documentation

### Features by Component

#### Agent Editor

- Switch between 3 views: Info, Chat, Node
- Edit agent metadata (name, description)
- Version selector and management
- Save, Save As, Delete, Export, Import actions
- Copy A2A share URL

#### Node Editor

- 8 configurable node types
- Drag-to-connect edges
- Zoom and pan controls
- Node property panels
- Real-time configuration validation

#### Models Management

- List and search models
- Add/edit/delete model providers
- Provider-specific configuration forms
- Tenant assignment controls
- Sort and pagination

#### External Agents

- Register A2A agents
- Edit agent details
- Delete agents
- Search and filter
- URL validation

#### MCP Servers

- 3-step registration wizard
  - Step 1: Basic details
  - Step 2: Configuration parameters
  - Step 3: Tool discovery
- Tool listing and inspection
- Parameter management (query/header)
- Refresh tools on demand

### Infrastructure

- Vite development server with hot reload
- Production build optimization
- GitHub Pages documentation hosting
- Jekyll theme integration
- Environment-based API proxying

### Known Limitations

- Chat side panels (files, sessions) not active in current build
- Single browser tab active session per user
- Backend dependency required for full functionality

---

## [Unreleased]

### Planned

- [ ] Chat interface with message history
- [ ] File upload/management for agents
- [ ] Session recording and replay
- [ ] Agent activity logging and audit trail
- [ ] Advanced workflow builder with branching logic
- [ ] Model performance analytics
- [ ] Team collaboration features
- [ ] Custom node types
- [ ] Webhook integrations

---

## Version History

| Version | Release Date | Status |
|---------|--------------|--------|
| 1.0.0 | 2025-05-28 | ✅ Released |
| 0.9.0 | 2025-05-15 | Beta |
| 0.8.0 | 2025-05-01 | Alpha |

---

## Upgrade Guide

### From v0.9 to v1.0

No breaking changes. All v0.9 agents are compatible.

**Upgrade Steps:**

1. Pull latest code: `git pull origin main`
2. Install dependencies: `npm install`
3. Rebuild if deployed: `npm run build`
4. Restart the application

### From v0.8 to v0.9+

Configuration format may have changed. Recommend:

1. Export all agents from v0.8 as JSON
2. Upgrade to v1.0
3. Import agents using the import wizard

---

## Reporting Issues

Found a bug or have feedback? 

- 🐛 [Report Bug](https://github.com/IN-ATOS-AARA/atos-ai-agents-ui/issues/new?labels=bug)
- 💡 [Suggest Feature](https://github.com/IN-ATOS-AARA/atos-ai-agents-ui/issues/new?labels=enhancement)
- 📧 Email: dl-atospolarisaisupport@atos.net

---

## Credits

Built by the Atos Polaris AI team. See [CONTRIBUTING.md](CONTRIBUTING.md) for contributors and license information.
