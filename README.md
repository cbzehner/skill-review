# Review

Run focused reviews by lens: code, architecture, complexity, security, design, docs, spec fit, or release readiness. Findings come first, with evidence tied to files and lines.

## Use It For

- Reviewing a branch, diff, plan, or artifact
- Applying a specific role such as security or accessibility
- Catching behavioral risk before a change ships

## Install

Clone the repo and run the installer:

```bash
git clone https://github.com/cbzehner/skill-review.git
cd skill-review
./install.sh all
```

Install targets:

- `./install.sh claude` installs to `~/.claude/skills/review`
- `./install.sh codex` installs to `~/.codex/skills/review`
- `./install.sh agents` installs to `~/.agents/skills/review`
- `./install.sh opencode` installs to `~/.config/opencode/skills/review`
- `./install.sh all --copy` copies files instead of symlinking

Manual install works too: symlink or copy `skills/review` into your agent's skills directory.

## Agent Support

This repo uses the plain `skills/review/SKILL.md` layout. Claude Code and Codex also get small plugin manifests at `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json`.

Other agents can read the same `SKILL.md` file. If a host does not support a frontmatter field or tool name, ignore that field and follow the workflow text.

## Layout

```text
.claude-plugin/plugin.json
.codex-plugin/plugin.json
install.sh
skills/review/SKILL.md
README.md
LICENSE
```

## Public Notes

These repos are public. Keep private repo names, secrets, customer data, raw logs, cookies, and absolute filesystem paths out of examples.

## Credits

- The `--as deep` lens (call-path reading, provenance tracing, and the Ref / Surface / Bug / Cause / Provenance / Best-fix / Refactor / Proof / Risk template) is adapted from Peter Steinberger's [`github-deep-review`](https://github.com/steipete/agent-scripts/tree/main/skills/github-deep-review) skill.

## License

MIT
