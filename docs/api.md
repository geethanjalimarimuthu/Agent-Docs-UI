---
layout: default
title: API Reference
nav_order: 7
---

# API Reference

Backend API endpoints reference for developers integrating with Polaris AI.

## Base URL

```
http://localhost:8000
```

Or your deployed backend instance.

## Authentication

All endpoints require authentication (typically via session cookies or tokens).

- `GET /me` – Get current user and check authentication
- If not authenticated, backend redirects to sign-in

## Agents

### List Agents

```
GET /api/{tenant}/agents?search={query}&limit={limit}&skip={skip}
```

**Parameters:**
- `tenant` – Tenant ID
- `search` – Optional search term
- `limit` – Number of results (default: 12)
- `skip` – Offset for pagination

**Response:**
```json
[
  {
    "id": "agent-001",
    "name": "Customer Support Agent",
    "description": "...",
    "versions": [
      {
        "id": "v-001",
        "version": "v1.0-prod",
        "isPublic": true
      }
    ]
  }
]
```

### Get Agent Details

```
GET /api/agents/{id}/info
```

**Response:**
```json
{
  "id": "agent-001",
  "name": "Customer Support Agent",
  "description": "...",
  "versions": [
    {
      "id": "v-001",
      "version": "v1.0",
      "config": { /* TeamConfig */ },
      "is_public": true,
      "url": "https://..."
    }
  ]
}
```

### Create Agent

```
POST /api/agents
```

**Body:**
```json
{
  "name": "New Agent",
  "description": "Description here",
  "config": { /* TeamConfig */ }
}
```

### Update Agent

```
POST /api/agents/{id}
```

**Body:**
```json
{
  "name": "Updated Name",
  "description": "Updated description",
  "config": { /* TeamConfig */ }
}
```

### Delete Agent

```
DELETE /api/agents/{id}
```

## Models

### List Models

```
GET /api/models?search={query}&limit={limit}&tenant={tenant}
```

**Response:**
```json
[
  {
    "id": "model-001",
    "name": "OpenAI GPT-4",
    "provider": "openai",
    "config": { /* Model config */ }
  }
]
```

### Save/Update Model

```
POST /api/models
```

**Body:**
```json
{
  "type": "openai",
  "api_key": "sk-...",
  "settings": {
    "endpoint": "https://..."
  }
}
```

### Delete Model

```
DELETE /api/models/{id}
```

## External Agents

### List External Agents

```
GET /api/{tenant}/external-agents?search={query}&skip={skip}&limit={limit}
```

### Save External Agent

```
POST /api/{tenant}/a2a-agents
```

**Body:**
```json
{
  "name": "External Agent",
  "description": "...",
  "url": "https://..."
}
```

### Delete External Agent

```
DELETE /api/{tenant}/a2a-agents/{id}
```

## MCP Servers

### List MCP Servers

```
GET /api/mcps?search={query}&skip={skip}&limit={limit}
```

### Get MCP Details

```
GET /api/mcps/{provider}
```

**Response:**
```json
{
  "provider": "weather-mcp",
  "name": "Weather Service",
  "description": "...",
  "url": "https://",
  "tools": [
    {
      "name": "get_weather",
      "description": "...",
      "schema": { /* JSON Schema */ }
    }
  ],
  "params": [],
  "mapping": true
}
```

### Register MCP Server

```
POST /api/mcps
```

**Body:**
```json
{
  "provider": "custom-mcp",
  "name": "Custom MCP",
  "description": "...",
  "url": "https://",
  "params": [
    {
      "key": "api_key",
      "value": "...",
      "type": "header"
    }
  ]
}
```

### Delete MCP Server

```
DELETE /api/mcps/{provider}
```

## Sessions

### List Sessions for Agent

```
GET /api/agents/{id}/sessions?limit={limit}
```

### Get Session Details

```
GET /api/sessions/{sessionId}
```

### Update Session

```
POST /api/sessions/{sessionId}
```

**Body:**
```json
{
  "name": "New session name"
}
```

### Delete Session

```
DELETE /api/sessions/{sessionId}
```

## File Management

### Get Agent Files

```
GET /api/agents/files
```

**Response:**
```json
[
  {
    "name": "config.json",
    "fullPath": "/configs/config.json",
    "ls": []
  }
]
```

### Download File

```
GET /api/agents/files?path={filePath}
```

### Upload File

```
POST /api/agents/files
```

**Form Data:**
- `file` – File to upload

### Delete File

```
DELETE /api/agents/files?path={filePath}
```

## User Info

### Get Current User

```
GET /me
```

**Response:**
```json
{
  "links": {
    "doc_url": "https://...",
    "knowledge": "https://...",
    "solutions": "https://..."
  },
  "user": {
    "name": "John Doe",
    "email": "john@example.com",
    "claims": ["tenant_admin", "user"],
    "groups": ["Default", "Sales"]
  }
}
```

## Response Formats

### Success Response

```json
{
  "ok": true,
  "value": { /* Data */ }
}
```

### Error Response

```json
{
  "ok": false,
  "error": {
    "code": 400,
    "message": "Invalid request"
  }
}
```

## Data Models

### TeamConfig

```json
{
  "strategy": "parallel|sequence|plan|select",
  "system_message": "Optional system message",
  "model": "openai-gpt4",
  "agents": ["agent-id-1", "agent-id-2"],
  "max_iterations": 10,
  "components": {
    "model-1": { /* Model */ },
    "agent-1": { /* Agent */ },
    "tool-1": { /* MCP */ }
  }
}
```

### Agent Types

**Assistant Agent:**
```json
{
  "type": "assistant",
  "description": "...",
  "system_message": "You are...",
  "tools": [
    {
      "provider": "mcp-name",
      "tool": "tool-name"
    }
  ],
  "model": "openai-gpt4",
  "temperature": 0.7,
  "handoffs": [],
  "meta": { "position": { "x": 100, "y": 100 } }
}
```

**Actor-Critic:**
```json
{
  "type": "actor-critic",
  "description": "...",
  "actor": "assistant-agent-1",
  "critic": "assistant-agent-2",
  "approval_term": "...",
  "max_iterations": 5,
  "model": "openai-gpt4",
  "temperature": 0.5,
  "meta": { "position": { "x": 200, "y": 100 } }
}
```

**Group of Agents:**
```json
{
  "type": "goa",
  "description": "...",
  "strategy": "parallel",
  "agents": ["agent-1", "agent-2"],
  "model": "openai-gpt4",
  "max_iterations": 3,
  "meta": { "position": { "x": 300, "y": 100 } }
}
```

## Rate Limiting

Endpoints may have rate limits. If you receive `429 Too Many Requests`, wait before retrying.

## CORS

API endpoints support CORS from:
- `http://localhost:5173` (dev)
- Configured production origins

## Pagination

List endpoints support pagination via:
- `limit` – Results per page
- `skip` – Offset (number of results to skip)

Example: Get results 21-30:
```
?limit=10&skip=20
```

## Filtering & Search

List endpoints typically support:
- `search` – Text search across name/description
- `sort` – Sort field (if supported)
- `order` – asc/desc

## Errors

Common error codes:

| Code | Meaning |
|------|---------|
| 400 | Bad request (invalid parameters) |
| 401 | Unauthorized (not authenticated) |
| 403 | Forbidden (no permission) |
| 404 | Not found |
| 500 | Server error |

---

## Need More?

- Check [manager.ts](https://github.com/IN-ATOS-AARA/atos-ai-agents-ui/blob/main/src/manager.ts) for request/response examples
- See [Best Practices](guides/best-practices.md) for integration tips
- Contact support: dl-atospolarisaisupport@atos.net
