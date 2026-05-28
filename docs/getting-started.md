---
layout: default
title: Getting Started
nav_order: 1
---

# Getting Started

Welcome! This guide will walk you through signing in, understanding the interface, and completing your first agent creation.

## Table of Contents

- [Sign In](#sign-in)
- [Understanding the Interface](#understanding-the-interface)
- [Key Concepts](#key-concepts)
- [Your First Agent](#your-first-agent)

## Sign In

1. Open the Polaris AI application URL provided to you.
2. You will be directed to the **sign-in page** if not already authenticated.
3. Enter your credentials and complete any multi-factor authentication if required.
4. After successful sign-in, you land on the **Agent List** page.

If you don't have an account or encounter login issues, contact your administrator.

## Understanding the Interface

### Header Navigation

At the top of every page, you'll find:

| Element | Purpose |
|---------|---------|
| **Tenant Selector** | Switch between workspaces/tenants (left side) |
| **Help Menu** | Access API docs and documentation links |
| **Settings ⚙️** | Configure models, external agents, MCP servers |
| **Theme Toggle 🌙** | Switch between light and dark mode |
| **User Menu 👤** | View your profile and sign out |

### Main Areas

```
┌─────────────────────────────────────────────────┐
│  Polaris AI / [Tenant] / Help / Settings  👤    │
├─────────────────────────────────────────────────┤
│                                                 │
│  Agent List / Agent Detail / Settings Pages    │
│                                                 │
│  • Search & Filter                              │
│  • Create / Import / Edit / Delete              │
│  • Version Management                           │
│  • Export / Import Configs                      │
│                                                 │
└─────────────────────────────────────────────────┘
```

## Key Concepts

### Agents

An **Agent** is a team of AI models and tools orchestrated to accomplish tasks.

- Each agent has a name and description
- Agents can contain multiple versions

### Versions

**Versions** are snapshots of an agent's configuration at a point in time.

- Save and Save As to create new versions
- Each version can be marked public or private
- Export/import version configs as JSON

### Models

**Models** are language model (LLM) providers like OpenAI, Claude, AWS Bedrock, etc.

- Administrators register models in Settings
- Agents reference registered models
- Each model has provider-specific configuration

### External Agents

**External Agents** are agents from other systems that your agents can interact with.

- Registered by URL and name in Settings
- Used within agent workflows

### MCP Servers

**Model Context Protocol (MCP) servers** provide tools and capabilities to agents.

- Registered with endpoint, description, and parameters
- Tools are discovered and displayed for use

## Your First Agent

### Step 1: Go to Agent List

- Click the app home or Polaris AI logo at any time

### Step 2: Create an Agent

1. On the first card, click **Create**.
2. Fill in the form:
   - **Name**: "My First Agent" (3-30 chars, start with capital letter)
   - **Description**: "A friendly agent for learning" (30-256 chars, start with capital letter)
   - **Model**: Select an available LLM (e.g., OpenAI, Claude)
3. Click **Save**.

The app opens your agent in the Node view.

### Step 3: Review & Configure

- Click the **Info** tab to review metadata
- Click the **Node** tab to design workflows
- Click **Save** to persist changes

### Step 4: Version It

1. Click **Save** to save the current version
2. Click **Save As** to create a new version snapshot

Congratulations! You have created your first agent.

## Next Steps

- [Create and manage agents →](guides/agent-management)
- [Design workflows in the visual editor →](guides/visual-editor)
- [Explore settings →](guides/settings)

---

**Stuck?** See [FAQ & Troubleshooting](../faq)
