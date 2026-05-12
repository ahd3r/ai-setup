# opencode setup
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm i -g opencode-ai
```
- load all dependencies
```bash
# for skills
git clone https://github.com/ahd3r/ai-setup.git ~/repos/ahd3r/ai-setup
git clone https://github.com/obra/superpowers.git ~/repos/obra/superpowers
git clone https://github.com/trailofbits/skills.git ~/repos/trailofbits/skills
git clone https://github.com/skills-directory/skill-codex.git ~/repos/skills-directory/skill-codex
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings
# for mcps
# for agents
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
      "~/repos/trailofbits/skills/.codex/skills",
      "~/repos/skills-directory/skill-codex/plugins/skill-codex/skills",
      "~/repos/obra/superpowers/skills",
      "~/repos/feiskyer/claude-code-settings/skills",
      "~/repos/ahd3r/ai-setup/skills"
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
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm install -g @anthropic-ai/claude-code
```
- configure
```bash
```

# codex setup
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm install -g @openai/codex
```
- configure
```bash
```
