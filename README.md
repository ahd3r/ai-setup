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
git clone https://github.com/microsoft/skills.git ~/repos/microsoft/skills # also have agents and mcps
git clone https://github.com/anthropics/skills.git ~/repos/anthropics/skills
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings # also have agents and mcps
git clone https://github.com/openai/skills.git ~/repos/openai/skills # also have mcps
git clone https://github.com/alirezarezvani/claude-skills.git ~/repos/alirezarezvani/claude-skills
git clone https://github.com/wshobson/agents.git ~/repos/wshobson/agents # also have agents
# for agents
git clone https://github.com/ClickHouse/agent-skills.git ~/repos/ClickHouse/agent-skills
git clone https://github.com/hashicorp/agent-skills.git ~/repos/hashicorp/agent-skills
# for mcps
# for commands
```
- configure
  - authenticate with proper account (for personal use case, I use OpenAI, for work, I use Anthropic)
  - choose model (for personal use case, I use GPT 5.5 high, for work, I use Claude Opus 4.7 high)
  - define configuration
```bash
opencode run "add ~/repos/ahd3r/ai-setup/skills to opencode skills.paths"
opencode run "Install all from ~/repos/obra/superpowers to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/antonbabenko/terraform-skill to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/muratcankoylan/Agent-Skills-for-Context-Engineering to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/trailofbits/skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/skills-directory/skill-codex to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/upstash/context7 to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/microsoft/skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/anthropics/skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/feiskyer/claude-code-settings to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/openai/skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/alirezarezvani/claude-skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/wshobson/agents to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/ClickHouse/agent-skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
opencode run "Install all from ~/repos/hashicorp/agent-skills to opencode.json config, include skills, mcps and agents. Exclude skill, mcp or agent, if already presented"
echo '{
  "$schema": "https://opencode.ai/config.json",
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
- remove unnecessary MCPs servers from opencode.json

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
