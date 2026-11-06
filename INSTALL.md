# Assistant installation instructions

Use these instructions only after the user asks to install this repository.

1. Check whether this session has local filesystem and command execution access. If it does not, explain that the user needs a desktop Work/Codex session with local access. Never claim a web-only installation succeeded.
2. Inspect the repository manifest and skill before installation. Install only Expense Claim Assistant. Do not run scripts from the repository; it contains instructions only.
3. If `codex` is available, inspect `codex plugin marketplace add --help` and `codex plugin add --help` to confirm supported syntax. Add this repository by its actual HTTPS Git URL, then run `codex plugin add expense-claim-assistant@francois-team-skills --json`. Use the actual URL supplied by the user; never substitute a different publisher. Check existing marketplace sources first to avoid replacing a different source with the same name.
4. If plugin installation is unavailable but the host provides the skill-installer skill, use that skill to install `plugins/expense-claim-assistant/skills/expense-claim-receipts` from this repository. Preserve any existing private configuration; do not overwrite an existing installation without inspecting it.
5. If neither supported installation route exists, report the precise limitation. Do not ask a nontechnical user to edit configuration files or pretend conversational instructions are an installed skill.
6. Verify installed status and read back the installed SKILL.md and blank example configuration. Do not modify other plugins or personal settings. Tell the user if a new turn or app restart is needed for discovery; do not claim a fresh-session test unless performed.
7. Start onboarding only after the skill is available. Store the user's configuration in a durable private location outside the repository and plugin cache, and provide its location to the user. Never commit or upload it. Ask for the receipt location and company template only when they cannot be identified from user-provided context. Browser/calendar/Teams capabilities are optional and installation does not grant them.

Approvals remain unsent for the user to review and submit.
