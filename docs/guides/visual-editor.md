---
layout: default
title: Visual Editor & Workflows
nav_order: 3
parent: Guides
---

# Visual Editor & Workflows

Use the Node view to visually design your agent workflows.

## Table of Contents

- [Overview](#overview)
- [Node Types](#node-types)
- [Creating Workflows](#creating-workflows)
- [Best Practices](#best-practices)

## Overview

The **Visual Editor** (Node Tab) is a graph-based interface for composing agent systems.

- **Nodes** represent components (models, agents, tools, users)
- **Edges** represent connections and data flow
- **Drag & drop** to add and arrange nodes
- **Double-click** to edit node properties

## Node Types

### Team Node

The root orchestrator that coordinates other agents.

- **Purpose**: Delegates tasks to other agents
- **Configuration**: Strategy (parallel, sequence, plan, select), system message
- **Connections**: Links to other agents and tools

### Language Model Node

Represents an LLM provider (OpenAI, Claude, Bedrock, etc.).

- **Purpose**: Powers agent reasoning
- **Configuration**: Model selection, temperature, parameters
- **Connections**: Used by Assistant and Actor-Critic agents

### Assistant Agent Node

A single AI agent with tools and system instructions.

- **Purpose**: Executes tasks with specific tools
- **Configuration**: System message, temperature, tool selection, handoffs
- **Connections**: Can use models and MCP tools

### Actor-Critic Node

Implements approval workflows where an Actor performs tasks and a Critic reviews.

- **Purpose**: Quality control and compliance checking
- **Configuration**: Actor, Critic, approval terms, max iterations
- **Connections**: References other agents and models

### Group of Agents Node

Orchestrates multiple agents with a specific strategy.

- **Purpose**: Coordinate teams of agents
- **Configuration**: Strategy, model, system message, max iterations
- **Agents**: Links to multiple assistant agents

### External Agent Node

Represents an agent from another system.

- **Purpose**: Integration with external AI systems
- **Configuration**: Provider, name, description
- **Connections**: Called by Team or Group nodes

### MCP Tool Node

Provides tools from registered MCP servers.

- **Purpose**: Extend agent capabilities
- **Configuration**: Tool selection, parameters
- **Connections**: Available to Assistant and Actor-Critic agents

### User Node

Represents human interaction points.

- **Purpose**: Define where human approval/input is needed
- **Configuration**: Optional metadata
- **Connections**: In approval workflows

## Creating Workflows

### Basic Workflow: Single Assistant Agent

1. Open the **Node** tab
2. Add a **Language Model** node
3. Add an **Assistant Agent** node
4. Add an **MCP Tool** node (optional)
5. Connect:
   - Assistant Agent → Language Model
   - Assistant Agent → MCP Tool (if tools needed)
6. Configure the Assistant Agent with tools and system message
7. Click **Save**

### Approval Workflow: Actor-Critic

1. Add an **Actor-Critic** node
2. Add two **Assistant Agent** nodes (one for Actor, one for Critic)
3. Add a **Language Model** node
4. Add **User** node for approval decisions
5. Connect:
   - Actor-Critic → Model
   - Actor-Critic → Actor Agent
   - Actor-Critic → Critic Agent
   - Critic Agent → User (for final approval)
6. Configure approval thresholds and max iterations
7. Save

### Multi-Agent Workflow: Group of Agents

1. Add a **Team** node
2. Add multiple **Assistant Agent** nodes
3. Add a **Language Model** node
4. Add **Group of Agents** node
5. Connect:
   - Team → Group of Agents
   - Group of Agents → Individual Agents
   - Individual Agents → Language Model
   - Individual Agents → MCP Tools (as needed)
6. Configure Group strategy (parallel, sequence, plan, select)
7. Save

## Editing Node Properties

### Double-Click a Node

Click any node to see/edit its configuration panel.

Common properties:

- **Name**: Display name in the graph
- **Description**: Purpose and behavior
- **Model**: Select LLM provider
- **Tools**: Choose available MCP tools
- **System Message**: Custom prompt/instructions
- **Temperature**: Reasoning balance (0-1)
- **Max Iterations**: Limit on agent loops

### Remove a Node

Right-click a node and select **Delete**, or select and press **Delete** key.

Connections automatically clean up.

### Connect Nodes

1. Click a node's output port (typically right side)
2. Drag to another node's input port (typically left side)
3. Release to create the connection

If invalid, the connection will not complete.

## Best Practices

### Organize by Function

Group related nodes logically:

- Models on the left
- Agents in the middle
- Tools on the right

### Use Clear Node Names

Name nodes so their purpose is obvious:

- ✅ `GPT-4 Model`
- ✅ `Customer Support Agent`
- ❌ `Node1`, `Agent`, `Tool`

### Document System Messages

Include context in Agent system messages:

```
You are a customer support specialist. 
Your goal is to resolve issues quickly and politely.
Use available tools to check account status and process refunds.
```

### Test Before Saving

1. Review all node connections
2. Verify required fields are filled
3. Check for disconnected nodes
4. Save as a new version first

### Use External Agents for Integration

Instead of duplicating logic, call existing agents via External Agent nodes.

Benefits:
- DRY principle (Don't Repeat Yourself)
- Easier maintenance
- Centralized updates

### Version Your Workflows

Save significant workflow changes as new versions:

- `v1.0-simple` – Basic single-agent setup
- `v1.1-tools` – Added MCP tool integration
- `v2.0-approval` – Added Actor-Critic workflow

---

Next: [Configure settings & integrations →](settings)
