---
layout: default
title: FAQ & Troubleshooting
nav_order: 6
---

# FAQ & Troubleshooting

Common questions and solutions.

## Account & Access

### Q: I see "Unauthorized" – what do I do?

**A:** Your session may have expired.

1. Sign out (user menu → Sign Out)
2. Sign in again
3. If problem persists, contact your IT administrator

### Q: I don't have access to certain settings

**A:** You may lack admin permissions.

**Admin-only features:**
- Register/edit/delete models
- Register/edit/delete external agents
- Register/edit/delete MCP servers

Contact your tenant administrator to grant permissions.

### Q: My tenant is missing – where is it?

**A:** Your user account may not be assigned to that tenant.

1. Contact your administrator
2. Request to be added to the tenant group
3. Wait for access to be provisioned
4. Sign out and sign in again

## Agent Management

### Q: Can I rename an agent after creation?

**A:** Yes, in the **Info** tab.

1. Open the agent
2. Go to **Info** tab
3. Edit the **Name** field
4. Click **Save**

### Q: How do I undo a change?

**A:** Import a previous version's JSON.

1. Export current version (backup)
2. Create a new version (Save As)
3. Import the old JSON into that new version
4. You now have the old configuration back

### Q: Can I copy/duplicate an agent?

**A:** Yes, export then import.

1. Export the agent (JSON)
2. Go to **Agent List**
3. Click Create/Import → Import
4. Upload the JSON with a new name
5. Save

### Q: What happens if I delete an agent?

**A:** All versions are deleted permanently. You cannot undo this.

**Always export first** if you think you might need it later.

### Q: Can agents talk to each other?

**A:** Yes, via **External Agents**.

1. Register the target agent as an External Agent in Settings
2. Add an External Agent node in the source agent's workflow
3. Configure which operations are allowed

## Versions

### Q: Why should I use versions?

**A:** Versions let you:
- Test changes without affecting production
- Keep historical snapshots
- Roll back if needed
- Maintain multiple configurations (prod/staging/dev)

### Q: How do I mark a version for production?

**A:** Use clear naming and toggle visibility:

1. Go to **Info** tab
2. Version dropdown: select/rename to `v1.0-prod`
3. Toggle to **Public** (if it should be shared)
4. Click **Save**

### Q: Can I delete a single version?

**A:** Not from the UI currently. You must export other versions, delete the entire agent, then reimport them.

Alternative: Create a new version and mark the old one private.

## Models

### Q: My model isn't available when creating an agent

**A:** Common causes:

1. **Not registered** – Ask admin to add the model in Settings
2. **Not allowed for your tenant** – Check Allowed Tenants setting
3. **Not active** – Model may be disabled; contact admin

### Q: I get "Invalid API Key" error

**A:** Check:

1. API key is correct in Settings
2. API key hasn't expired
3. API key has correct permissions
4. Model provider service is online

Contact your admin or the model provider's support.

### Q: Can I use a local model?

**A:** Yes, if you have VLLM set up.

1. Admin registers VLLM model with your server URL
2. When creating agents, select the VLLM option
3. Configure base URL and API key

## MCP Tools

### Q: Tools are not showing up when I refresh

**A:** Troubleshoot:

1. **Verify URL**: Double-check MCP server address
2. **Check configuration**: Ensure all parameters are filled (API key, etc.)
3. **Test connectivity**: Try accessing the URL directly from browser
4. **Server status**: Is the MCP service online?

Contact MCP owner if service is down.

### Q: Can I use the same MCP tool in multiple agents?

**A:** Yes. Register the MCP once in Settings, then reference it in multiple agents.

Changes to the MCP config affect all agents using it.

### Q: How do I know which tools are available?

**A:** In MCP Server registration Step 3:

1. Click **Refresh Tools**
2. View the tool list
3. Read tool descriptions and parameters

## External Agents

### Q: Can I test an external agent connection?

**A:** Manually test the URL:

1. Copy the external agent URL
2. Use curl or Postman to test connectivity
3. Verify the service responds

If it doesn't work, check:
- URL is correct
- Service is online
- Network/firewall allows the connection

### Q: What format should external agent URLs be?

**A:** Must be a valid HTTP/HTTPS endpoint:

✅ `https://agents.company.com/customer-support`  
✅ `https://external-ai.partner.io/api/v1/agent`  
❌ `http://localhost:8000` (only if accessible from UI server)

## Workflows (Visual Editor)

### Q: I can't connect two nodes

**A:** Verify:

1. Both nodes are in the editor
2. You're dragging from output → input ports
3. Connection type is compatible
4. No cycles created (if not allowed)

Try right-clicking nodes to see available ports.

### Q: How do I know if my workflow is valid?

**A:** When you click **Save**:

- ✅ All validations pass → Agent saves successfully
- ❌ Missing required fields → Error message shows what to fix

Fix errors and save again.

### Q: Can I export the workflow diagram?

**A:** Currently, you export the **JSON config** which contains the workflow.

Diagram visualization tools can parse the JSON, or you can take a screenshot of the Node view.

## User Interface

### Q: How do I switch between light and dark mode?

**A:** Click the theme toggle icon in the top-right header (sun/moon icon).

Preference is saved automatically.

### Q: How do I switch tenants?

**A:** Click the tenant name in the header.

Select a different tenant from the dropdown list.

### Q: What if I see a loading spinner for too long?

**A:** 

1. Wait a few seconds (API may be slow)
2. If it hangs > 30 seconds, refresh the page
3. If issue persists, contact support with timestamp + tenant name

## Advanced Topics

### Q: Can I integrate Polaris AI with my CI/CD pipeline?

**A:** Yes, via **Export/Import JSON**.

1. Export agent version as JSON
2. Store in Git repository
3. In your pipeline, import the JSON into Polaris AI
4. Trigger agent updates programmatically (requires API)

For API details, see [API Reference](api).

### Q: How do I version control my agents?

**A:** Use Git + export/import:

```bash
# Export agent version
Export JSON → agents/customer-support/v1.0.json

# Commit to Git
git add agents/customer-support/v1.0.json
git commit -m "Add customer support agent v1.0"

# Later: reimport from Git
Import JSON from agents/customer-support/v1.0.json
```

### Q: Can I automate agent testing?

**A:** Not directly in the UI, but:

1. Export agent JSON
2. Integrate with your test framework
3. Call agent APIs programmatically
4. Assert on outputs

See [API Reference](api) for endpoint details.

## Still Need Help?

- 📖 Browse the full [documentation](/)
- 💬 Check [Best Practices](guides/best-practices) for design tips
- 📧 Email support: dl-atospolarisaisupport@atos.net
- 🔗 Check with your tenant administrator

---

**Last Updated:** May 2026
