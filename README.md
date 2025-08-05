# AI-Powered Task Helper Demo Project

## Project Overview
This project is a demonstration of a full-stack development workflow powered by AI and MCP (Multi-Context Platform). It integrates design, development, infrastructure, and advanced AI task/context management tools to validate a seamless, reproducible process for future real-world projects.

**Key Goals:**
- Test and document a complete development workflow from design (Figma) to deployment (AWS)
- Integrate with GitHub, Figma, AWS CDK, AWS Docs, Google Docs, Task-Master, Context7, and Sequential Thinking
- Serve as a template for future projects

---

## Folder Structure
```
front_end/    # React + Next.js dashboard (function-based components)
back_end/     # FastAPI server (layered architecture, DDD)
infra/        # AWS infrastructure as code (CDK, TypeScript)
README.md     # This file: workflow, environment, and setup instructions
```

---

## Tech Stack & Tools
- **Frontend:** React, Next.js, TypeScript, function-based components
- **Backend:** Python, FastAPI, layered architecture with Domain-Driven Design (DDD)
- **Infrastructure:** AWS CDK (TypeScript preferred)
- **Integrations:**
  - GitHub (version control)
  - Figma (UI design source)
  - AWS Docs (reference)
  - Google Docs (CSV data storage)
  - [Task-Master](https://www.task-master.dev/) (modern task management platform)
  - [Context7](https://github.com/upstash/context7) (project/code context for LLMs and AI editors)
  - [Sequential Thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) (step-by-step logical task planning)

---

## Development Principles
### Frontend
- Use React functional components and hooks
- Emphasize composition and reusability
- TypeScript for type safety

### Backend
- Layered architecture (Domain, Application, Infrastructure, Interfaces)
- Domain-Driven Design (DDD) for clear separation of concerns
- FastAPI for high-performance APIs

### Infrastructure
- AWS CDK in TypeScript (preferred)
- Modular, reproducible, and version-controlled infrastructure

---

## Workflow & Integrations
1. **Design:**
   - UI/UX designed in Figma
   - Handoff to frontend via Figma API or manual export
2. **Frontend Development:**
   - Implement dashboard UI in React + Next.js
   - Consume backend APIs for data
3. **Backend Development:**
   - FastAPI server with DDD and layered architecture
   - Expose RESTful endpoints for frontend
4. **Infrastructure:**
   - Use AWS CDK (TypeScript) to provision VPC, EC2, and other resources
   - Deploy backend and frontend to AWS
5. **Data Storage:**
   - Store demo data as CSV in Google Docs
   - Backend reads/writes to Google Docs as needed
6. **Version Control:**
   - All code managed in GitHub
7. **AI-Powered Task & Context Management:**
   - Use [Task-Master](https://www.task-master.dev/) for planning, tracking, and managing project tasks
   - Use [Context7](https://github.com/upstash/context7) to provide up-to-date project/code context to your AI assistant
   - Use [Sequential Thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) for step-by-step, logical task breakdown and execution

---

## Setup Instructions
1. **Clone the Repository**
   ```sh
   git clone <your-repo-url>
   cd <project-root>
   ```
2. **Install Prerequisites**
   - Node.js (for frontend and infra)
   - Python 3.9+ (for backend)
   - AWS CLI & CDK
   - Access to Figma, Google Docs, and GitHub
   - Task-Master account for task management ([sign up here](https://www.task-master.dev/))
3. **Set Up Frontend**
   ```sh
   cd front_end
   npm install
   # or yarn install
   ```
4. **Set Up Backend**
   ```sh
   cd back_end
   conda env create -f environment.yml  # or use requirements.txt
   conda activate <env-name>
   ```
5. **Set Up Infrastructure**
   ```sh
   cd infra
   npm install
   cdk bootstrap
   ```
6. **Configure Integrations**
   - Set up API keys/tokens for Figma, Google Docs, AWS, and GitHub as needed
   - Set up your project and tasks in Task-Master ([see docs](https://www.task-master.dev/))
   - Install and configure Context7 and Sequential Thinking servers as per their documentation
   - Document integration steps in each folder’s README if required

---

## Contribution & Task Management
- Use issues and pull requests on GitHub for code changes
- Track tasks and progress with [Task-Master](https://www.task-master.dev/)
- Store and retrieve project context with [Context7](https://github.com/upstash/context7)
- Use [Sequential Thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) for step-by-step task planning
- Document decisions and ideas in markdown files as needed

---

## References & Resources
- [React Documentation](https://react.dev/)
- [Next.js Documentation](https://nextjs.org/docs)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [AWS CDK Documentation](https://docs.aws.amazon.com/cdk/latest/guide/home.html)
- [Figma API](https://www.figma.com/developers/api)
- [Google Docs API](https://developers.google.com/docs/api)
- [Domain-Driven Design Reference](https://dddcommunity.org/)
- [Task-Master](https://www.task-master.dev/)
- [Context7](https://github.com/upstash/context7)
- [Sequential Thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)

---

## Notes
- This project is a demo and template for future, production-grade projects.
- For any questions or improvements, feel free to suggest changes or open an issue.