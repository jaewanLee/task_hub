# Project Local Setup Guide

This guide provides step-by-step instructions for setting up the full AI-Powered Task Helper Demo project on your local machine. It covers project structure, Task Master setup, GitHub integration, AI model configuration, and all other dependencies. Use this as a reference for onboarding new developers or replicating the environment.

---

## 1. Prerequisites
- **Node.js** (v18+ recommended)
- **npm** (comes with Node.js)
- **Python 3.9+** (for backend)
- **AWS CLI & AWS CDK** (for infrastructure)
- **A GitHub account and repository**
- **(Optional) Figma, Google account, etc.** for integrations

---

## 2. Clone the Repository
```sh
git clone <your-repo-url>
cd <project-root>
```

---

## 3. Project Structure
```
front_end/    # React + Next.js dashboard (function-based components)
back_end/     # FastAPI server (layered architecture, DDD)
infra/        # AWS infrastructure as code (CDK, TypeScript)
README.md     # Project overview and workflow
.taskmaster/  # Task Master config and tasks
.cursor/      # MCP/AI integration config
scripts/      # PRD and automation scripts
```

---

## 4. Install Task Master

**Global install:**
```sh
npm install -g task-master-ai
```

**Or use npx:**
```sh
npx task-master-ai init --name "Your Project Name" --description "Project description" -y
```

---

## 5. Initialize Task Master and AI Models
```sh
task-master init --name "Your Project Name" --description "Project description" -y
task-master models --setup
```
- Select your preferred AI model (e.g., gemini-cli/gemini-2.5-pro for local Gemini CLI)
- Set main, research, and fallback models as needed

---

## 6. Configure .env and MCP for Integrations

### a. GitHub
- Create a GitHub Personal Access Token ([instructions](https://github.com/settings/tokens))
- Add to `.env`:
```
GITHUB_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
GITHUB_REPO=yourusername/yourrepo
```

### b. AI Providers
- Add your Gemini/OpenAI/Anthropic API keys if using cloud models:
```
GEMINI_API_KEY=your-gemini-api-key
```

### c. (Optional) Add to `.cursor/mcp.json` for MCP/AI agent integration:
```json
{
  "env": {
    "GITHUB_TOKEN": "ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "GITHUB_REPO": "yourusername/yourrepo",
    "GEMINI_API_KEY": "your-gemini-api-key"
  }
}
```

---

## 7. Set Up Project Components

### a. Frontend
```sh
cd front_end
npm install
# or yarn install
```

### b. Backend
```sh
cd back_end
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### c. Infrastructure
```sh
cd infra
npm install
cdk bootstrap
```

---

## 8. Create and Parse PRD (Product Requirements Document)
- Draft your PRD in `scripts/prd.txt` (see example in `.taskmaster/templates/example_prd.txt`)
- Parse PRD to generate tasks:
```sh
task-master parse-prd --input=scripts/prd.txt
```

---

## 9. Sync Tasks with GitHub Issues
- If using MCP/AI agent (e.g., Cursor), instruct the agent to create GitHub issues for each task in `.taskmaster/tasks/tasks.json`.
- Alternatively, use a script (Node.js/Python) to automate issue creation via the GitHub API.

---

## 10. Ongoing Workflow
- Use Task Master for planning, breakdown, and tracking.
- Use GitHub Issues for collaboration and progress tracking.
- Use MCP/AI agent for automation, research, and advanced task management.
- Expand tasks, analyze complexity, and update as needed:
  - `task-master analyze-complexity`
  - `task-master expand --all`
  - `task-master next`

---

## 11. Additional Integrations
- **Figma:** Export design assets and integrate into `front_end`.
- **Google Docs:** Set up API access for backend data integration.
- **AWS:** Configure credentials for CDK deployment and GitHub Actions.
- **Context7/Sequential Thinking:** Set up as needed for advanced AI context.

---

## 12. Troubleshooting
- Ensure all API keys and tokens are correct and present in `.env` or config.
- Check that all dependencies are installed (Node.js, Python, AWS CLI, etc.).
- For GitHub integration, verify token permissions and repo name.
- For AI models, ensure the correct provider is selected and available.

---

## 13. References
- [Task Master Documentation](https://www.task-master.dev/)
- [GitHub API Docs](https://docs.github.com/en/rest/issues/issues)
- [Cursor (MCP) Docs](https://docs.cursor.so/)
- [AWS CDK Docs](https://docs.aws.amazon.com/cdk/latest/guide/home.html)
- [Figma API](https://www.figma.com/developers/api)
- [Google Docs API](https://developers.google.com/docs/api)

---

**This guide is intended as a comprehensive onboarding and local setup reference for the AI-Powered Task Helper Demo project.**