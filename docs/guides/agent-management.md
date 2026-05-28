---
layout: default
title: Agent Management
nav_order: 2
parent: Guides
---

# Agent Management Guide

Learn how to create, import, edit, version, and delete agents in Polaris AI.

## Table of Contents

- [Creating Agents](#creating-agents)
- [Importing Agents](#importing-agents)
- [Editing Agent Metadata](#editing-agent-metadata)
- [Working with Versions](#working-with-versions)
- [Exporting & Sharing](#exporting--sharing)
- [Deleting Agents](#deleting-agents)

## Creating Agents

### New Agent from Scratch

1. Navigate to the **Agent List** (home page)
2. Click the **Create/Import** card
3. Choose **Create**
4. Fill in the form:
   - **Name** (required): 3-30 characters, must start with uppercase
   - **Description** (required): 30-256 characters, must start with uppercase
   - **LLM Model** (required): select from available models
5. Click **Save**

The app creates your agent and opens it in the Node view (visual editor).

### What Happens Next

- You can design your agent's workflow using nodes
- Your agent's configuration is auto-saved
- You can switch to **Info** view to edit metadata

## Importing Agents

### Import from JSON Config

If you have an existing agent configuration exported from another instance:

1. Go to **Agent List**
2. Click the **Create/Import** card
3. Choose **Import**
4. Fill in:
   - **Name** (required)
   - **Description** (required)
   - **Version**: Label for this version (e.g., "v1.0", "2025-05-28")
5. Upload your JSON config file
6. Click **Save**

The agent is created with your configuration.

### Exporting for Backup or Migration

1. Open an existing agent
2. Select the version you want to export in the **Info** tab
3. Click **Export**
4. The JSON file downloads to your computer

Keep these exports as backups or to share configurations with teammates.

## Editing Agent Metadata

### Update Name or Description

1. Open an agent
2. Click the **Info** tab
3. Edit the fields:
   - **Name**
   - **Description**
4. Click **Save**

Changes only apply to the currently selected version.

### Toggle Version Visibility (Public/Private)

1. Open the agent **Info** tab
2. Use the **Public/Private toggle** next to the version selector
3. Click **Save**

- **Public**: version can be shared via URL
- **Private**: only accessible within your tenant

## Working with Versions

### Understanding Versions

Each agent can have multiple versions. Versions allow you to:

- Keep historical snapshots
- Test changes without overwriting production
- Maintain A/B testing configurations
- Rollback to previous versions

### Save the Current Version

1. Make changes to your agent in the Node or Info view
2. Click **Save** in the header
3. Confirm the action

The current version is updated.

### Create a New Version (Save As)

1. Click the **Save** button dropdown
2. Choose **Save As**
3. Enter a new version label (e.g., "v2.0-experimental")
4. Confirm

A new version is created based on the current version.

### Switch Between Versions

1. Use the **version dropdown** in the agent header
2. Select the version you want to work on
3. The UI reloads that version's configuration

You can now edit and save this version independently.

### Import Configuration into a Version

To replace a version's configuration with an external JSON:

1. Select the target version in the dropdown
2. Click **Import** in the header
3. Enter a version label for reference
4. Upload JSON file
5. Click **Save**

The current version is updated with the imported configuration.

## Exporting & Sharing

### Export to JSON

1. Select the version you want to export
2. Click **Export**
3. The JSON file downloads

Use this for:
- Backups
- Sharing with teammates
- Version control systems (Git)
- Integration with external systems

### Share via URL

1. Open the agent **Info** tab
2. Toggle the version to **Public**
3. Click the **share button** (copy icon) next to the A2A URL
4. Send the URL to teammates

Recipients can access and view the public configuration.

## Deleting Agents

### Delete an Agent

1. Open the agent
2. Click **Delete** in the header
3. Confirm in the dialog

**Warning**: Deletion is permanent and cannot be undone. All versions are deleted.

---

## Input Rules

| Field | Rules |
|-------|-------|
| Name | 3-30 chars, start with uppercase letter |
| Description | 30-256 chars, start with uppercase letter |
| Version Label | Non-empty, alphanumeric with `.`, `_`, `+`, `-` |

## Common Tasks

### Duplicate an Agent

1. Open the agent you want to copy
2. Export the current version (JSON)
3. Go to Agent List
4. Click Create/Import → Import
5. Provide new name and description
6. Upload the JSON file
7. Save

### Organize Agents by Version

Adopt a versioning strategy:

- `v1.0-stable` – Production version
- `v1.1-rc1` – Release candidate
- `v2.0-dev` – Development branch

---

Next: [Design workflows with the visual editor →](visual-editor)
