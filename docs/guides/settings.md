---
layout: default
title: Settings & Administration
nav_order: 4
parent: Guides
---

# Settings & Administration

Configure models, external agents, and MCP servers for your tenant.

## Table of Contents

- [Accessing Settings](#accessing-settings)
- [Models](#models)
- [External Agents](#external-agents)
- [MCP Servers](#mcp-servers)

## Accessing Settings

1. Click the **Settings ⚙️** icon in the top-right header
2. You'll see three tabs:
   - **Models**
   - **External Agents**
   - **MCP Servers**

Note: Admin access required for most setting operations.

## Models

Model providers are the LLM backends your agents use (OpenAI, Claude, AWS Bedrock, etc.).

### Add a New Model

1. Go to **Settings → Models**
2. Click **Create** button
3. Select **Model Type**:
   - OpenAI
   - Anthropic (Claude)
   - AWS Bedrock
   - Google AI
   - Azure AI Foundry
   - VLLM (local)

4. **Configure provider-specific fields**:

| Provider | Required Fields |
|----------|-----------------|
| **OpenAI** | Endpoint, API Key, Org ID (optional) |
| **Anthropic** | Base URL, API Key |
| **AWS Bedrock** | AWS Region, Access Key, Secret Key |
| **Google AI** | Project, Location, API Key |
| **Azure AI Foundry** | Endpoint, Deployment, API Key, API Version |
| **VLLM** | Base URL, API Key |

5. **Select Allowed Tenants**: Which workspaces can use this model
6. Click **Save**

The model is now available for agent creation.

### Edit an Existing Model

1. Go to **Models**
2. Find the model in the list
3. Click **Edit**
4. Modify fields as needed
5. Click **Save**

Note: Some fields (like type) cannot be changed after creation.

### Delete a Model

1. Go to **Models**
2. Find the model
3. Click **Delete**
4. Confirm

The model is removed. Agents using this model will need reassignment.

### Organize Your Models

Best practice:

- Create multiple model configs for different regions/tiers
- Label clearly: `OpenAI-GPT4-Prod`, `Claude-Dev`, `Bedrock-US-East`
- Rotate API keys periodically
- Document in team wiki

## External Agents

External agents are AI agents from other systems that your agents can call.

### Register an External Agent

1. Go to **Settings → External Agents**
2. Click **Register** button
3. Fill in:
   - **Name**: Friendly name
   - **Description**: What this agent does
   - **URL**: Where to reach this agent (must be HTTPS)
4. Click **Save**

The agent is now available in your agent workspace.

### Edit an External Agent

1. Go to **External Agents**
2. Click **Edit** on the agent
3. Update details
4. Click **Save**

### Delete an External Agent

1. Go to **External Agents**
2. Click **Delete**
3. Confirm

The agent is removed and can no longer be referenced.

### Testing Connection

After registering, verify connectivity:

1. Note the agent URL
2. Test the endpoint from your network (using curl, Postman, etc.)
3. Confirm the service responds
4. If issues, check firewall/network access with your IT team

## MCP Servers

MCP (Model Context Protocol) servers provide tools and capabilities to your agents.

### What are MCP Tools?

Tools are functions agents can call:

- Web search
- File operations
- Database queries
- API calls
- Custom integrations

### Register an MCP Server

The registration wizard has 3 steps:

#### Step 1: Basic Details

1. Go to **Settings → MCP Servers**
2. Click **Register** button
3. Fill in:
   - **Name**: e.g., "Weather Service"
   - **Description**: Purpose of this MCP
   - **URL**: Server endpoint (HTTPS)
4. Click **Next**

#### Step 2: Configuration Parameters

If your MCP requires authentication or custom config:

1. Click **Add Configuration** (+)
2. Enter:
   - **Key**: Parameter name (e.g., `api_key`)
   - **Value**: Parameter value (e.g., your API key)
   - **Type**: Query Param or Header Param
3. Repeat for all parameters
4. Click **Save**

#### Step 3: Tools Discovery

1. Click **Refresh Tools** button
2. Wait for the server to respond
3. Review available tools listed

You'll see:
- Tool name
- Description
- Parameters and types

If no tools appear, check:
- MCP URL is correct
- Configuration parameters are complete
- MCP server is online and reachable

### Edit an MCP Server

1. Go to **MCP Servers**
2. Click **Edit**
3. Update details or parameters
4. Click **Save**
5. Click **Refresh Tools** if you changed the configuration

### Delete an MCP Server

1. Go to **MCP Servers**
2. Click **Delete**
3. Confirm

The MCP is removed. Agents using these tools will lose access.

### Example: Register a Weather MCP

1. **Name**: OpenWeather Tools
2. **Description**: Real-time weather data and forecasts
3. **URL**: https://weather-mcp.mycompany.com
4. **Configuration**:
   - Key: `api_key`, Value: `your_openweather_key`, Type: `Header Param`
   - Key: `units`, Value: `metric`, Type: `Query Param`
5. Click through to Tools step
6. See tools like: `get_current_weather`, `get_forecast`

---

## Input Validation

| Field | Rules |
|-------|-------|
| **Model Name** | Required, typically includes provider and version |
| **Agent Name** | Required, alphanumeric with underscores |
| **Agent URL** | Must start with `https://` or `http://` |
| **MCP URL** | Must start with `https://` or `http://` |
| **API Keys** | Keep confidential, store securely |

## Troubleshooting Settings

### Model Not Appearing When Creating Agent

- Confirm model's **Allowed Tenants** includes your current tenant
- Refresh the browser
- Check user permissions (may require admin)

### MCP Tools Not Loading

- Verify **URL** is reachable from your network
- Check all required **Configuration parameters** are filled
- Confirm MCP server is running
- Try **Refresh Tools** again

### External Agent Connection Fails

- Verify agent **URL** is correct and reachable
- Confirm network/firewall allows outbound connections
- Contact the agent owner if service is down

---

Next: [Best practices guide →](best-practices)
