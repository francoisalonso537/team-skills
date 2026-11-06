# Expense Claim Receipts — team quick start

1. Add this skill to a session or project that supports custom skills. If your interface uses project instructions instead, provide SKILL.md as instructions and keep the example configuration available. Import options depend on your environment.
2. Say “Set up this expense-claim skill for me, then prepare my [month/year] claim.” Provide access to your receipts and company template or a completed claim, plus a prior approval example if available.
3. The assistant discovers your setup and creates your private user-config.md. Keep that file in your own copy or private project. For future sessions, supply it with the skill when persistence is unavailable.
4. On later uses, say “Prepare my [month/year] expense claim.” Review the workbook, PDF, inferred descriptions, and Teams form, then submit the approval yourself.

Local laptop access, Chrome control, Excel/PDF processing, and Teams access require compatible tools in your session. Installing these instructions does not provide those capabilities. If calendar access is unavailable, unsupported descriptions stay blank. If Teams cannot be operated, the assistant provides the fields and attachment locations for manual entry.

Included files are SKILL.md, user-config.example.md, agents/openai.yaml, and this guide. The package contains no personal configuration, company template, receipts, or account credentials. Use your organization's own template. Keep processing local and use your approved company storage for claim attachments.

To share onward, distribute this clean package, excluding your personal user-config.md and all claim documents.
