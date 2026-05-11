# opencode setup
- install
```bash
curl -fsSL https://opencode.ai/install | bash
```
- install codex
- configure
```bash
git clone https://github.com/ahd3r/ai-setup.git ~/repos/ahd3r/ai-setup
git clone https://github.com/skills-directory/skill-codex.git ~/repos/skills-directory/skill-codex
git clone https://github.com/obra/superpowers.git ~/repos/obra/superpowers
git clone https://github.com/trailofbits/skills.git ~/repos/trailofbits/skills
git clone https://github.com/feiskyer/claude-code-settings.git ~/repos/feiskyer/claude-code-settings
echo "{
  "$schema": "https://opencode.ai/config.json",
  "skills": {
    "paths": [
      "~/repos/trailofbits/skills/plugins/agentic-actions-auditor/skills",
      "~/repos/trailofbits/skills/plugins/ask-questions-if-underspecified/skills",
      "~/repos/trailofbits/skills/plugins/audit-context-building/skills",
      "~/repos/trailofbits/skills/plugins/building-secure-contracts/skills",
      "~/repos/trailofbits/skills/plugins/burpsuite-project-parser/skills",
      "~/repos/trailofbits/skills/plugins/c-review/skills",
      "~/repos/trailofbits/skills/plugins/claude-in-chrome-troubleshooting/skills",
      "~/repos/trailofbits/skills/plugins/constant-time-analysis/skills",
      "~/repos/trailofbits/skills/plugins/culture-index/skills",
      "~/repos/trailofbits/skills/plugins/debug-buttercup/skills",
      "~/repos/trailofbits/skills/plugins/devcontainer-setup/skills",
      "~/repos/trailofbits/skills/plugins/differential-review/skills",
      "~/repos/trailofbits/skills/plugins/dimensional-analysis/skills",
      "~/repos/trailofbits/skills/plugins/dwarf-expert/skills",
      "~/repos/trailofbits/skills/plugins/entry-point-analyzer/skills",
      "~/repos/trailofbits/skills/plugins/firebase-apk-scanner/skills",
      "~/repos/trailofbits/skills/plugins/fp-check/skills",
      "~/repos/trailofbits/skills/plugins/git-cleanup/skills",
      "~/repos/trailofbits/skills/plugins/insecure-defaults/skills",
      "~/repos/trailofbits/skills/plugins/let-fate-decide/skills",
      "~/repos/trailofbits/skills/plugins/modern-python/skills",
      "~/repos/trailofbits/skills/plugins/mutation-testing/skills",
      "~/repos/trailofbits/skills/plugins/property-based-testing/skills",
      "~/repos/trailofbits/skills/plugins/seatbelt-sandboxer/skills",
      "~/repos/trailofbits/skills/plugins/second-opinion/skills",
      "~/repos/trailofbits/skills/plugins/semgrep-rule-creator/skills",
      "~/repos/trailofbits/skills/plugins/semgrep-rule-variant-creator/skills",
      "~/repos/trailofbits/skills/plugins/sharp-edges/skills",
      "~/repos/trailofbits/skills/plugins/skill-improver/skills",
      "~/repos/trailofbits/skills/plugins/spec-to-code-compliance/skills",
      "~/repos/trailofbits/skills/plugins/static-analysis/skills",
      "~/repos/trailofbits/skills/plugins/supply-chain-risk-auditor/skills",
      "~/repos/trailofbits/skills/plugins/testing-handbook-skills/skills",
      "~/repos/trailofbits/skills/plugins/trailmark/skills",
      "~/repos/trailofbits/skills/plugins/variant-analysis/skills",
      "~/repos/trailofbits/skills/plugins/workflow-skill-design/skills",
      "~/repos/trailofbits/skills/plugins/yara-authoring/skills",
      "~/repos/trailofbits/skills/plugins/zeroize-audit/skills",
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
