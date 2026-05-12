# opencode setup
- install
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
npm i -g opencode-ai
```
- configure skills
```bash
git clone https://github.com/ahd3r/ai-setup.git ~/repos/ahd3r/ai-setup
git clone https://github.com/skills-directory/skill-codex.git ~/repos/skills-directory/skill-codex
git clone https://github.com/obra/superpowers.git ~/repos/obra/superpowers
git clone https://github.com/trailofbits/skills.git ~/repos/trailofbits/skills
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings
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
- configure mcps
- configure agents
- configure commands
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
