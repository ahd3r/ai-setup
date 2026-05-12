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
git clone https://github.com/microsoft/skills.git ~/repos/microsoft/skills
git clone https://github.com/anthropics/skills.git ~/repos/anthropics/skills
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings
git clone https://github.com/ClickHouse/agent-skills.git ~/repos/ClickHouse/agent-skills
git clone https://github.com/openai/skills.git ~/repos/openai/skills
# for agents
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
      "~/repos/muratcankoylan/Agent-Skills-for-Context-Engineering/skills",
      "~/repos/trailofbits/skills/.codex/skills",
      "~/repos/skills-directory/skill-codex/plugins/skill-codex/skills",
      "~/repos/upstash/context7/skills",
      "~/repos/microsoft/skills/.github/skills",
      "~/repos/anthropics/skills/skills",
      "~/repos/feiskyer/claude-code-settings/skills",
      "~/repos/ClickHouse/agent-skills/skills",
      "~/repos/openai/skills/skills/.curated"
    ]
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
