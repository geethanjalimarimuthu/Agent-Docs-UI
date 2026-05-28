---
layout: default
title: Quick Reference
nav_order: 8
---

# Quick Reference Cheat Sheet

Copy-paste quick reference for common tasks.

## Essential URLs

```
App Home:     http://localhost:5173
API Docs:     http://localhost:5173/api/docs
GitHub Repo:  https://github.com/IN-ATOS-AARA/atos-ai-agents-ui
```

## Common Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Save Agent | Ctrl+S / Cmd+S |
| Delete Node | Delete / Backspace |
| Copy URL | Ctrl+C / Cmd+C |
| Switch Theme | Click Moon/Sun icon |

## Form Validation Patterns

### Agent Name

```
✅ "Customer Support Bot"
✅ "DocumentProcessor"
❌ "my agent" (lowercase start)
❌ "AI" (too short)
```

**Rule:** 3-30 chars, start with uppercase

### Agent Description

```
✅ "Handles customer inquiries and processes refunds"
✅ "Analyzes documents and extracts key information."
❌ "handles inquiries" (lowercase start)
❌ "Short description" (too short)
```

**Rule:** 30-256 chars, start with uppercase

### Version Label

```
✅ "v1.0"
✅ "2025-05-28"
✅ "v2.0-rc1"
❌ "latest" (reserved)
```

**Rule:** Alphanumeric with `.`, `_`, `+`, `-`

### URLs

```
✅ "https://api.company.com/agents"
✅ "https://mcp.service.io"
❌ "localhost:8000" (must use HTTPS in production)
❌ "api.company.com" (missing protocol)
```

**Rule:** Must start with `http://` or `https://`

## API Quick Commands

### Get Agents (curl)

```bash
curl -X GET "http://localhost:8000/api/default/agents" \
  -H "Content-Type: application/json" \
  -c cookies.txt
```

### Create Agent (curl)

```bash
curl -X POST "http://localhost:8000/api/agents" \
  -H "Content-Type: application/json" \
  -b cookies.txt \
  -d '{
    "name": "My Agent",
    "description": "An example agent",
    "config": {
      "strategy": "sequence",
      "model": "openai-gpt4",
      "agents": [],
      "components": {}
    }
  }'
```

### Export Agent (save to file)

```bash
# In browser console:
const json = JSON.stringify(currentVersion.config, null, 2);
const blob = new Blob([json], {type: 'application/json'});
const url = URL.createObjectURL(blob);
const a = document.createElement('a');
a.href = url;
a.download = 'agent.json';
a.click();
```

## Role-Based Permissions

### Regular User

- ✅ Create/edit agents
- ✅ View own workspace
- ✅ Use registered models/tools
- ❌ Manage models
- ❌ Manage MCP servers
- ❌ View other workspaces

### Admin

- ✅ All user permissions
- ✅ Register models
- ✅ Register external agents
- ✅ Register MCP servers
- ✅ Manage tenant settings
- ✅ View audit logs (if available)

## Common Troubleshooting Commands

### Check Backend Connectivity

```bash
# Test API endpoint
curl -v http://localhost:8000/me

# Expected: 200 OK or 401 Unauthorized
# (401 means service is up, you're just not authenticated)
```

### Test MCP Server

```bash
# Test MCP connectivity
curl -v https://your-mcp-server.com

# Check response status and headers
```

### Check Browser Console for Errors

```javascript
// Open DevTools (F12)
// Go to Console tab
// Look for error messages
// Copy full error and share with support
```

### Clear Local Storage

```javascript
// Clear tenant preference
localStorage.removeItem('HOSTNAME.TENANT');

// Clear all storage
localStorage.clear();
```

## Workflow Node Connections

### Quick Recipe: Basic Agent

```
Model → Assistant Agent
```

### Quick Recipe: Approval Workflow

```
Actor-Critic → Actor Agent → Model
         ↓
      Critic Agent → Model
```

### Quick Recipe: Multi-Agent Team

```
Team → Group of Agents → [Agent1, Agent2, Agent3] → Model
                      ↓
                   MCP Tools
```

## File Sizes & Limits

| Item | Limit |
|------|-------|
| Agent Name | 30 chars |
| Description | 256 chars |
| System Message | ~4000 chars |
| Agent Config JSON | 10 MB |
| API Keys | 256 chars |

## Support Checklist

When contacting support, include:

- [ ] Tenant name
- [ ] Agent name / ID
- [ ] Error message (screenshot)
- [ ] Browser type/version
- [ ] Timestamp of issue
- [ ] Steps to reproduce
- [ ] Screenshot of issue

Format: `tenant=Default, agent=customer-support-v1, error=Save failed, browser=Chrome 125, time=2025-05-28 14:30:00 UTC`

## Useful Links

| Link | Purpose |
|------|---------|
| [Docs Home](/) | All documentation |
| [Getting Started](getting-started.md) | First-time setup |
| [Agent Management](guides/agent-management.md) | CRUD operations |
| [Visual Editor](guides/visual-editor.md) | Workflow design |
| [Settings](guides/settings.md) | Configuration |
| [Best Practices](guides/best-practices.md) | Design tips |
| [FAQ](faq.md) | Troubleshooting |
| [API Reference](api.md) | Endpoints |

---

## Model Provider API Key Formats

### OpenAI

```
sk-...
Length: 48+ chars
Format: sk-proj-... or sk-...
```

### Anthropic

```
sk-ant-...
Length: 40+ chars
```

### AWS Bedrock

```
AWS_ACCESS_KEY_ID: AKIA...
AWS_SECRET_ACCESS_KEY: (secret)
Format: AWS IAM credentials
```

### Google AI

```
AIza...
Length: 39+ chars
```

### Azure

```
Format varies by service
Usually in form: endpoint + api-key
```

---

**Need more help?** See [FAQ & Troubleshooting](faq.md)
