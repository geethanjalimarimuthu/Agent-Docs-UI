---
layout: default
title: Best Practices
nav_order: 5
parent: Guides
---

# Best Practices

Tips for building scalable, maintainable, and effective agents.

## Agent Design

### Start Simple

Begin with a single assistant agent and one model.

```
Model → Assistant Agent (with system message & tools)
```

Then gradually add complexity:

- Multiple agents
- Orchestration strategies
- Approval workflows
- External integrations

### Use Clear Naming

Adopt consistent naming across your organization:

✅ **Good**
- `customer-support-v1-prod`
- `document-analyzer-v2-beta`
- `email-classifier-v1`

❌ **Avoid**
- `Agent1`, `test`, `new_agent`
- `my-agent`, `temp`

### Write Effective System Messages

System messages guide agent behavior.

**Template:**

```
You are a [ROLE].
Your primary goal is to [OBJECTIVE].

You have access to these tools:
- [Tool 1]: [What it does]
- [Tool 2]: [What it does]

When responding:
1. [Behavior 1]
2. [Behavior 2]
3. [Constraint 1]

Example: [Show expected output]
```

**Example:**

```
You are a customer support specialist for an e-commerce platform.
Your goal is to resolve customer issues quickly and politely.

You have access to:
- order_lookup: Find customer orders by ID
- refund_processor: Process refunds up to $500
- escalate_to_human: Transfer to human agent

When responding:
1. Be empathetic and professional
2. Always verify customer identity before accessing orders
3. Offer refunds only if clearly justified
4. Never promise compensation beyond policy limits
5. Escalate complex cases to humans

Example:
Customer: "I received a damaged item"
You: "I'm sorry to hear that. Let me look up your order..."
```

## Version Management

### Adopt a Versioning Strategy

Use semantic versioning or date-based schemes:

- **Semantic**: `v1.0`, `v1.1-rc1`, `v2.0-beta`
- **Date-based**: `2025-05-28-prod`, `2025-05-28-staging`

### Tag Production Versions

Always mark production versions as **Public** and clearly labeled:

- `v1.0-prod` (public)
- `v1.1-staging` (private, for testing)
- `v2.0-experimental` (private, early development)

### Export Before Major Changes

Before making significant changes:

1. Export current version as JSON
2. Store in Git or team drive
3. Create new version in app
4. Make changes
5. Test thoroughly

If new version fails, you can import the old JSON backup.

## Model Configuration

### Regional Models

Register models for different regions/performance needs:

```
Models:
├── OpenAI-GPT4-US-East
├── OpenAI-GPT4-EU
├── Claude-Haiku-Cost-Optimized
└── Bedrock-Custom-Tuned
```

### Rotation & Secrets

- **API Keys**: Rotate quarterly
- **Service Accounts**: Use separate accounts for different environments
- **Credentials**: Never commit to Git; use secure secret management

Best practice: Use a secrets manager (Vault, AWS Secrets Manager, etc.)

## Tool Integration (MCP Servers)

### Test MCP Connections

Before relying on an MCP in production:

1. Register the MCP
2. Refresh tools and verify they load
3. Manually test tool calls in a test agent
4. Verify error handling and timeouts
5. Document any quirks or limitations

### Monitor Tool Availability

Track which MCPs are:
- ✅ Online and tested
- ⚠️ Available but untested
- ❌ Down or deprecated

Maintain a team doc listing all MCPs and their status.

### Handle Tool Failures

Design agents to handle missing/failed tools:

```
If tool "search_database" fails:
→ Try alternative tool
→ Use cached results if available
→ Gracefully degrade functionality
→ Escalate to human if critical
```

## Multi-Tenant Considerations

### Tenant Isolation

- Agents are isolated per tenant
- Models are shared at organization level but limited by tenant
- External agents should not cross tenant boundaries

### Admin Checklist

As a tenant admin:

- [ ] Register required models monthly
- [ ] Maintain up-to-date MCP integrations
- [ ] Review External Agents quarterly
- [ ] Document integrations for your team
- [ ] Audit agent activity and permissions
- [ ] Update API keys/secrets on schedule

## Security

### API Key Management

❌ **Never**:
- Hardcode API keys in agent config
- Share keys via email
- Commit keys to Git

✅ **Do**:
- Use environment variables or secrets manager
- Rotate keys every 90 days
- Grant least-privilege permissions
- Audit key usage

### Access Control

- Use **Public** versions only for shareable, read-only configs
- Keep sensitive workflows in **Private** versions
- Review tenant permissions regularly

### Network Security

- Register only HTTPS MCP servers
- Verify certificate validity
- Use firewalls to restrict outbound agent calls
- Monitor unusual API usage patterns

## Performance

### Agent Response Times

- Simple agents (1-2 tool calls): Target < 5 seconds
- Complex agents (multiple chains): Target < 30 seconds
- User-facing agents: Aim for < 3 seconds for UX

### Cost Optimization

Compare model costs:

| Model | Cost/1K tokens | Use Case |
|-------|----------------|----------|
| GPT-3.5 | $0.002 | High-volume, simple tasks |
| Claude Haiku | $0.003 | Cost-sensitive tasks |
| GPT-4 | $0.03 | Complex reasoning |
| Bedrock Custom | Variable | Long-term ROI projects |

### Caching Strategies

- Cache tool responses when appropriate
- Reuse model configs across agents
- Batch similar requests

## Documentation

### Document Your Agents

For each agent, maintain:

- **Purpose**: What problem does it solve?
- **Owner**: Who maintains it?
- **Dependencies**: Which models, tools, external agents?
- **Versions**: Which is production?
- **SLA**: Expected uptime/performance?
- **Fallbacks**: What happens if it fails?

### Example Agent Specification

```markdown
## Customer Support Agent v1.0

### Purpose
Resolve common customer issues (order lookup, refunds, returns)

### Owner
Support Team <support@company.com>

### Dependencies
- Model: OpenAI GPT-4
- MCPs: order_management, refund_service
- External Agents: human_escalation_agent

### Production Version
v1.0-prod (public share link available)

### Performance SLA
- Response time: < 10 seconds
- Availability: 99.5%
- Escalation to human: < 2 minutes if needed

### Fallback
If MCP tools unavailable, escalate to human support queue.
```

---

## Quick Checklist: Before Going to Production

- [ ] Agent has clear purpose and owner
- [ ] All required models are registered and tested
- [ ] All MCP tools are verified and documented
- [ ] System message is clear and specific
- [ ] Version is tagged as production
- [ ] Version is exported as JSON backup
- [ ] Error handling is in place
- [ ] Performance metrics are acceptable
- [ ] Team is trained on usage
- [ ] Monitoring/alerts are configured

---

Next: [FAQ & Troubleshooting →](../faq)
