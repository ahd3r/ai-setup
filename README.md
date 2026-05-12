# opencode setup
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm i -g opencode-ai
```
- [install codex](https://github.com/ahd3r/ai-setup/tree/main#codex-setup) (for codex skill)
- load all dependencies
```bash
# for skills
git clone https://github.com/ahd3r/ai-setup.git ~/repos/ahd3r/ai-setup
git clone https://github.com/obra/superpowers.git ~/repos/obra/superpowers
git clone https://github.com/antonbabenko/terraform-skill.git ~/repos/antonbabenko/terraform-skill
git clone https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering.git ~/repos/muratcankoylan/Agent-Skills-for-Context-Engineering
git clone https://github.com/trailofbits/skills.git ~/repos/trailofbits/skills
git clone https://github.com/skills-directory/skill-codex.git ~/repos/skills-directory/skill-codex
git clone https://github.com/upstash/context7.git ~/repos/upstash/context7
git clone https://github.com/microsoft/skills.git ~/repos/microsoft/skills # also have agents
git clone https://github.com/anthropics/skills.git ~/repos/anthropics/skills
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings # also have agents
git clone https://github.com/openai/skills.git ~/repos/openai/skills
# for agents
git clone https://github.com/ClickHouse/agent-skills.git ~/repos/ClickHouse/agent-skills
git clone https://github.com/hashicorp/agent-skills.git ~/repos/hashicorp/agent-skills
git clone https://github.com/callstackincubator/agent-skills.git ~/repos/callstackincubator/agent-skills
# for mcps
# for commands
```
- configure
  - authenticate with proper account (for personal use case, I use OpenAI, for work, I use Anthropic)
  - choose model (for personal use case, I use GPT 5.5 high, for work, I use Claude Opus 4.7 high)
  - define configuration
```bash
echo '{
  "$schema": "https://opencode.ai/config.json",
  "skills": {
    "paths": [
      "~/repos/ahd3r/ai-setup/skills",
      "~/repos/obra/superpowers/skills",
      "~/repos/antonbabenko/terraform-skill/skills",
      "~/repos/muratcankoylan/Agent-Skills-for-Context-Engineering",
      "~/repos/trailofbits/skills/.codex/skills",
      "~/repos/skills-directory/skill-codex/plugins/skill-codex/skills",
      "~/repos/upstash/context7/skills",
      "~/repos/microsoft/skills/.github/skills",
      "~/repos/microsoft/skills/.github/plugins/deep-wiki/skills",
      "~/repos/anthropics/skills/skills",
      "~/repos/feiskyer/claude-code-settings/skills",
      "~/repos/ClickHouse/agent-skills/skills",
      "~/repos/openai/skills/skills/.curated"
    ]
  },
  "agents": {
    "deep-wiki-architect": {
      "description": "Technical documentation architect that analyzes repositories and generates structured wiki catalogues with onboarding guides",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/plugins/deep-wiki/agents/wiki-architect.md}",
      "permission": {
        "edit": "deny"
      }
    },
    "deep-wiki-researcher": {
      "description": "Expert code analyst conducting systematic deep research with zero tolerance for shallow analysis",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/plugins/deep-wiki/agents/wiki-researcher.md}",
      "permission": {
        "edit": "deny"
      }
    },
    "deep-wiki-writer": {
      "description": "Senior documentation engineer that generates wiki pages with rich Mermaid diagrams, code citations, VitePress-compatible output, and validation",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/plugins/deep-wiki/agents/wiki-writer.md}"
    },
    "microsoft-backend": {
      "description": "FastAPI/Python specialist for CoreAI DIY backend development with Pydantic, Cosmos DB, and Azure services",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/backend.agent.md}"
    },
    "microsoft-frontend": {
      "description": "React/TypeScript specialist for CoreAI DIY frontend development with React Flow, Zustand, and Tailwind CSS",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/frontend.agent.md}"
    },
    "microsoft-infrastructure": {
      "description": "Azure and Bicep specialist for CoreAI DIY infrastructure, deployments, and DevOps",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/infrastructure.agent.md}"
    },
    "microsoft-planner": {
      "description": "Read-only planning specialist that analyzes requirements, explores the codebase, and creates detailed implementation plans before coding begins",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/planner.agent.md}",
      "permission": {
        "edit": "deny"
      }
    },
    "microsoft-presenter": {
      "description": "Specialist for CoreAI DIY presenter mode features, including presentation view, navigation, and teleprompter functionality",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/presenter.agent.md}"
    },
    "microsoft-scaffolder": {
      "description": "Full-stack Azure AI Foundry application scaffolder for React + FastAPI + azd projects",
      "mode": "subagent",
      "prompt": "{file:~/repos/microsoft/skills/.github/agents/scaffolder.agent.md}"
    },
    "deep-reflector": {
      "description": "Comprehensive session analysis and learning capture specialist. Analyzes development sessions to extract patterns, preferences, and improvements for future interactions. Use after significant work sessions to capture learnings.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/deep-reflector.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "glob": "allow",
        "grep": "allow",
        "edit": "ask"
      }
    },
    "github-issue-fixer": {
      "description": "GitHub issue resolution specialist. Analyzes, plans, and implements fixes for GitHub issues with proper testing and PR creation. Use when fixing specific GitHub issues.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/github-issue-fixer.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "glob": "allow",
        "grep": "allow",
        "edit": "allow",
        "bash": {
          "*": "ask",
          "gh *": "allow",
          "git *": "allow"
        }
      },
      "color": "warning"
    },
    "insight-documenter": {
      "description": "Technical breakthrough documentation specialist. Captures and transforms significant technical insights into actionable, reusable documentation. Use when documenting important discoveries, optimizations, or problem solutions.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/insight-documenter.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "edit": "allow",
        "bash": "ask"
      },
      "color": "accent"
    },
    "instruction-reflector": {
      "description": "Analyzes and improves Claude Code instructions in CLAUDE.md. Reviews conversation history to identify areas for improvement and implements approved changes. Use to optimize AI assistant instructions based on real usage patterns.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/instruction-reflector.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "glob": "allow",
        "grep": "allow",
        "edit": "ask"
      },
      "color": "warning"
    },
    "pr-reviewer": {
      "description": "Expert code reviewer for GitHub pull requests. Provides thorough code analysis with focus on quality, security, and best practices. Use when reviewing PRs for code quality and potential issues.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/pr-reviewer.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "glob": "allow",
        "grep": "allow",
        "edit": "deny",
        "bash": {
          "*": "ask",
          "gh *": "allow",
          "git *": "allow"
        }
      },
      "color": "info"
    },
    "ui-engineer": {
      "description": "Expert UI/frontend developer for creating, modifying, or reviewing frontend code, UI components, and user interfaces. Use when building React components, responsive designs, or any frontend development tasks. PROACTIVELY use for UI/UX implementation, component architecture, and frontend best practices.",
      "mode": "subagent",
      "prompt": "{file:~/repos/feiskyer/claude-code-settings/agents/ui-engineer.md}",
      "permission": {
        "read": "allow",
        "list": "allow",
        "glob": "allow",
        "grep": "allow",
        "edit": "allow",
        "bash": "ask",
        "webfetch": "allow"
      }
    }
  },
  "mcp": {
    "azure": {
      "type": "local",
      "command": ["npx", "-y", "@azure/mcp@latest", "server", "start"],
      "enabled": true
    },
    "chrome-devtools": {
      "type": "local",
      "command": ["npx", "chrome-devtools-mcp@latest"],
      "enabled": true
    },
    "context7": {
      "type": "local",
      "command": ["npx", "-y", "@upstash/context7-mcp@latest"],
      "enabled": true
    },
    "eslint": {
      "type": "local",
      "command": ["npx", "eslint", "--mcp"],
      "enabled": true
    },
    "memory": {
      "type": "local",
      "command": ["npx", "-y", "@modelcontextprotocol/server-memory"],
      "environment": {
        "MEMORY_FILE_PATH": "{env:OPENCODE_MEMORY_FILE_PATH}"
      },
      "enabled": true
    },
    "playwright": {
      "type": "local",
      "command": ["npx", "-y", "@playwright/mcp@latest"],
      "enabled": true
    },
    "sequentialthinking": {
      "type": "local",
      "command": ["npx", "-y", "@modelcontextprotocol/server-sequential-thinking"],
      "enabled": true
    },
    "svelte": {
      "type": "remote",
      "url": "https://mcp.svelte.dev/mcp",
      "enabled": true
    },
    "terraform": {
      "type": "local",
      "command": ["docker", "run", "-i", "--rm", "hashicorp/terraform-mcp-server"],
      "enabled": true
    }
  },
  "permission": {
    "edit": "ask",
    "bash": {
      "*": "ask",
      "grep *": "allow",
      "ls *": "allow"
    },
    "webfetch": "ask"
  }
}' > ~/.config/opencode/opencode.json
```

# claude code setup
**I do not use it**
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm install -g @anthropic-ai/claude-code
```

# codex setup
**I use it only as a part of opencode as a second opinion**
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm install -g @openai/codex
```
- auth
```bash
codex login --device-auth
```
- configure
```bash
echo 'model = "gpt-5.5"
model_reasoning_effort = "high"
sandbox = "read-only"

[profiles.readonly]
sandbox = "read-only"

[profiles.dev]
sandbox = "workspace-write"
model_reasoning_effort = "high"' > ~/.codex/config.toml
```
