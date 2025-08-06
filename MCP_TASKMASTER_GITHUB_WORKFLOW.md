# MCP Task Master + GitHub Integration Workflow

This guide covers the essential steps to set up Task Master with MCP integration and sync tasks to GitHub Issues. This is a focused workflow for AI-powered project management.

---

## Prerequisites
- Node.js 18+
- npm
- GitHub account
- GitHub repository for your project

---

## Step 1: Install Task Master

```bash
npm install -g task-master-ai
```

Verify installation:
```bash
task-master --version
```

---

## Step 2: Initialize Task Master in Your Project

Navigate to your project directory and run:

```bash
task-master init
```

This will:
- Create `.taskmaster/` directory
- Generate `config.json` with default settings
- Set up the project structure

**Optional flags:**
```bash
task-master init --name "My Project" --description "Project description" --yes
```

---

## Step 3: Configure AI Models (Optional)

If you want to customize AI models:

```bash
task-master models --setup
```

Or set specific models:
```bash
task-master models --set-main gemini-2.5-pro --set-research gemini-2.5-pro
```

---

## Step 4: Create a Product Requirements Document (PRD)

Create a file named `prd.txt` in your project root:

```txt
Product Requirements Document (PRD)

Project Name: Your Project Name

Overview:
Brief description of your project goals and scope.

1. Goals
- Primary objective 1
- Primary objective 2

2. Features
- Feature 1: Description
- Feature 2: Description

3. Technical Requirements
- Frontend: React/Next.js
- Backend: FastAPI/Python
- Infrastructure: AWS CDK
- Data: Google Docs CSV

4. Success Criteria
- Criterion 1
- Criterion 2
```

---

## Step 5: Parse PRD to Generate Tasks

```bash
task-master parse-prd prd.txt
```

This will:
- Generate tasks in `.taskmaster/tasks/tasks.json`
- Create a structured task list based on your PRD

**Optional flags:**
```bash
task-master parse-prd prd.txt --num-tasks 10 --force
```

---

## Step 6: Set Up GitHub Repository

1. **Create a new repository on GitHub**
   - Go to https://github.com/new
   - Name your repository
   - Make it public or private as needed

2. **Connect your local project:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit with Task Master setup"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   git push -u origin main
   ```

---

## Step 7: Generate GitHub Personal Access Token

1. **Go to GitHub Settings:**
   - Visit: https://github.com/settings/tokens
   - Click "Generate new token (classic)"

2. **Configure token:**
   - **Note:** "Task Master Integration"
   - **Expiration:** Choose as needed (or "No expiration")
   - **Scopes:** Select these permissions:
     - `repo` (Full control of private repositories)
     - `public_repo` (if using public repos)
     - `workflow` (for GitHub Actions if needed)

3. **Copy the token** (you won't see it again!)

---

## Step 8: Configure Environment Variables

Create a `.env` file in your project root:

```env
GITHUB_TOKEN=your_github_token_here
GITHUB_REPO=YOUR_USERNAME/YOUR_REPO_NAME
```

**Important:** Replace `YOUR_USERNAME/YOUR_REPO_NAME` with your actual GitHub username and repository name.

---

## Step 9: Use MCP to Create GitHub Issues

Since Task Master doesn't have a built-in GitHub sync command, you can use MCP (Model Context Protocol) to create issues from your tasks.

### Using MCP with Cursor

If you're using Cursor with MCP GitHub integration:

1. **Ensure MCP GitHub is configured** in your `.cursor/mcp.json`:
   ```json
   {
     "mcpServers": {
       "github": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-github"]
       }
     },
     "env": {
       "GITHUB_TOKEN": "your_github_token_here"
     }
   }
   ```

2. **Ask your AI assistant** (like me) to create GitHub issues from your tasks:
   ```
   "Please create GitHub issues for all tasks in my .taskmaster/tasks/tasks.json file"
   ```

---

## Step 10: Verify and Manage

1. **Check your GitHub repository** - you should see new issues created
2. **Review and adjust** issues as needed
3. **Use Task Master commands** to manage tasks:
   ```bash
   task-master list                    # View all tasks
   task-master next                    # Get next task
   task-master show 1                  # Show specific task
   task-master set-status --id 1 --status done  # Mark as complete
   ```

---

## Workflow Summary

1. ✅ Install Task Master
2. ✅ Initialize project
3. ✅ Create PRD
4. ✅ Parse PRD to generate tasks
5. ✅ Set up GitHub repository
6. ✅ Generate GitHub token
7. ✅ Configure environment variables
8. ✅ Use MCP to create GitHub issues
9. ✅ Verify and manage tasks

---

## Troubleshooting

**Task Master not found:**
```bash
npm install -g task-master-ai
```

**GitHub token issues:**
- Verify token has correct permissions
- Check token hasn't expired
- Ensure GITHUB_REPO format is correct (username/repo-name)

**MCP connection issues:**
- Verify `.cursor/mcp.json` configuration
- Check environment variables are set
- Restart Cursor if needed

---

## References

- [Task Master Documentation](https://www.task-master.dev/)
- [GitHub Personal Access Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- [MCP GitHub Server](https://github.com/modelcontextprotocol/servers/tree/main/src/github) 