# opencode setup
- install
```bash
curl -fsSL https://opencode.ai/install | bash
```
- install codex
- configure
```bash
mkdir ~/repos
git clone https://github.com/ahd3r/ai-setup.git ~/repos/ahd3r
echo "{
}" > ~/.config/opencode/opencode.json
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
