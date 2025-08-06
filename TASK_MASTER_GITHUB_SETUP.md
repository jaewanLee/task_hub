# Task Master + GitHub Integration Setup Guide

This guide explains, in detail, how to set up Task Master for AI-powered project management, connect it to GitHub using MCP, and sync your Task Master tasks with GitHub Issues. Follow these steps to replicate the workflow on your own local environment.

---

## 1. Prerequisites
- **Node.js** (v18+ recommended)
- **npm** (comes with Node.js)
- **A GitHub account**
- **A GitHub repository** for your project
- **(Optional) Python, AWS CLI, etc.** for your project stack

---

## 2. Install Task Master

You can install Task Master globally or use npx for one-off commands.

**Global install:**
```sh
npm install -g task-master-ai
```

**Or use npx (no install needed):**
```sh
npx task-master-ai init --name "Your Project Name" --description "Project description" -y
```

---

## 3. Initialize Your Project

In your project directory, run:
```sh
task-master init --name "Your Project Name" --description "Project description" -y
```
This sets up the `.taskmaster` folder and config files.

---

## 4. Configure AI Models

Run the interactive setup:
```sh
task-master models --setup
```
- Select your preferred AI model (e.g., gemini-cli/gemini-2.5-pro for local Gemini CLI)
- Set main, research, and fallback models as needed

---

## 5. Connect to GitHub via MCP

### a. Create a GitHub Personal Access Token (PAT)
1. Go to [GitHub Tokens](https://github.com/settings/tokens)
2. Click **"Generate new token"** (classic or fine-grained)
3. Give it a name and set expiration
4. **Select scopes:**
   - `repo` (for private repos)
   - `public_repo` (for public repos)
   - `issues`
5. Generate and copy the token

### b. Add GitHub Credentials to .env
Create a `.env` file in your project root:
```
GITHUB_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
GITHUB_REPO=yourusername/yourrepo
```

### c. (Optional) Add to MCP config
If using Cursor or another MCP client, add to `.cursor/mcp.json`:
```json
{
  "env": {
    "GITHUB_TOKEN": "ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "GITHUB_REPO": "yourusername/yourrepo"
  }
}
```

---

## 6. Create a Product Requirements Document (PRD)

Draft your PRD in plain text or markdown (e.g., `scripts/prd.txt`).
Example:
```
Project Name: My AI Project
Overview: ...
Goals: ...
Features: ...
```

---

## 7. Generate Tasks from PRD

Parse your PRD to generate tasks:
```sh
task-master parse-prd --input=scripts/prd.txt
```
This creates `.taskmaster/tasks/tasks.json` with your project tasks.

---

## 8. Sync Task Master Tasks to GitHub Issues

Task Master does not have a built-in `github sync` command. Instead, use the MCP GitHub integration (as in Cursor) or a script to create issues from your tasks.json.

### a. Using MCP (Cursor/AI Agent)
- If you are using Cursor or another MCP-enabled agent, you can instruct the agent to create GitHub issues for each task in `.taskmaster/tasks/tasks.json`.
- The agent will use the GitHub MCP connection and your token to create issues directly in your repo.

### b. Using a Script (Manual Option)
- Use a Node.js or Python script to read `.taskmaster/tasks/tasks.json` and create issues via the GitHub API.
- Example Node.js script is available in this project (see `create_github_issues.js`).

---

## 9. Verify Issues in GitHub

Go to your GitHub repository’s **Issues** tab. You should see all your project tasks as issues, with details and subtasks as checklists.

---

## 10. Ongoing Workflow
- Use Task Master for planning, breakdown, and tracking.
- Use GitHub Issues for team collaboration, assignment, and progress tracking.
- As you update tasks in Task Master, you can repeat the sync process to keep GitHub Issues up to date.
- Use MCP/AI agent to automate as much as possible.

---

## 11. Troubleshooting
- Ensure your `.env` or MCP config has the correct GitHub token and repo.
- Your token must have the correct permissions (repo, issues).
- If using a script, ensure dependencies (node-fetch, dotenv) are installed.
- If issues are not created, check for API errors or permission issues.

---

## 12. References
- [Task Master Documentation](https://www.task-master.dev/)
- [GitHub API Docs](https://docs.github.com/en/rest/issues/issues)
- [Cursor (MCP) Docs](https://docs.cursor.so/)

---

**This guide was generated as a reference for setting up Task Master with GitHub integration, based on a real project workflow.**