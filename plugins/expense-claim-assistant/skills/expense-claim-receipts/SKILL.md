---
name: expense-claim-receipts
description: Create or verify monthly expense claim packages, including the month folder, Excel expense claim workbook, numbered receipt PDF, calendar-based descriptions, and a Teams approval draft ready for the user to review and submit. Use for monthly expense claims, receipt PDFs, expense workbooks, and Teams approval drafts.
---

# Expense Claim Receipts

## Quick start

First use: “Set up this expense-claim skill for me, then prepare my [month/year] claim.”

Provide access to the receipt folder, a previous completed claim or company workbook template, and a previous approval request if available. The assistant will discover your filing conventions and save a personal setup. If your session cannot access laptop files, provide the required files through the session's supported file controls or use a session with local file access.

Later uses: “Prepare my [month/year] expense claim.”

The workflow prepares the Excel workbook and numbered receipt PDF, checks Outlook and Google Calendar in Chrome for business-purpose matches, and prepares a Teams approval for you to review and submit. Browser, laptop, and Teams access depend on the tools available in your session. Setup does not install tools or grant access automatically.

## Personal configuration and first-use setup

Load `user-config.md` beside this skill, or the personal configuration supplied in the current project/session. Treat it as private, user-specific configuration. `user-config.example.md` documents the fields and is an unconfigured starting point.

Run onboarding only when configuration is missing or incomplete. Revisit affected fields when the user requests changes or configured resources become unavailable. A complete setup skips onboarding, while each claim still verifies its template and destination and checks current approval precedents.

1. Start with the current workspace, supplied locations, and accessible connected storage. Search likely finance/expense folders for receipt sources, completed claim packages, and templates. Avoid a laptop-wide search by default. If there is no useful starting point or filesystem access, ask for the relevant location or files.
2. Inspect recent completed claims to discover the claimant, organization, folder hierarchy, monthly naming, filenames, currency, language, and description style. Identify the workbook's sheets, entry fields, category lookup, formulas, receipt references, and print settings. Prefer an explicitly supplied template over inferred alternatives. Never reuse another person's identity, approvers, or personal paths as defaults.
3. Inspect the current user's recent approved Teams expense claims for the template, title convention, approval sequence, amount format, and attachment approach. Check Outlook and Google Calendar through Chrome to identify relevant accounts/calendars and timezone. Save unavailable integrations as unavailable or unverified and continue independent work.
4. Infer routine choices from consistent evidence. Ask one concise, bundled question for material ambiguity such as competing templates, unclear claimant identity, destination, currency, or approvers. Leave unresolved values unset. Do not invent settings to mark setup complete.
5. Automatically create or update the user's own `user-config.md` with the discovered settings and the status of each integration. Mark setup complete when the core claimant, template, destination, naming and currency choices are established. Calendar/Teams access may remain unavailable without forcing repeated full onboarding. Mark partial or pending when core settings remain unresolved.
6. Read back the saved configuration and summarize the selected template, destination, naming, calendars, and approval workflow. This shared skill already loads that file, so future runs adapt automatically. Keep reusable workflow instructions in `SKILL.md` and personal adaptations in the config. Do not modify a centrally shared installation for one user. In that case, save the config in the user's private project/session location instead.
7. If persistent writes are unavailable, provide a downloadable configuration file, or copyable Markdown when file generation is unavailable. Explain that the user must keep it with their private project files or supply it in a future session. Claim persistence only after verifying a save. Never rely on assumed cross-chat memory.

Store operational settings, paths, and verification notes only. Exclude passwords, tokens, receipt content, and private event descriptions. When packaging this skill for another user, include only the generic instructions, blank example configuration, and quick-start guide. Exclude `user-config.md`, claims, receipts, and other personal files.

## Workflow

1. Load the personal configuration and perform first-use setup if needed. Resolve the target month/year from the request.
2. Create the target month folder using the configured destination and naming before copying templates, editing Excel, or generating PDFs. If a claim already exists, inspect and update it within the requested scope rather than overwrite user edits.
3. Copy the configured workbook template into the month folder and apply the configured filename. Verify the actual workbook structure before editing. Clear stale claim entries copied from examples, including old descriptions and claimant/approval fields, then populate the current user's verified values. Preserve formulas and formatting.
4. Process the original receipts locally with the document-scan filter below. Number receipts chronologically, including time within the same date, unless the user specifies another order. Build the numbered PDF in the same month folder.
5. Match PDF receipt numbers exactly to workbook references. Use the configured currency and category rules. Do not combine different currencies into one total without an established conversion rule.
6. Check both calendars through Chrome using the matching instructions below and populate supported descriptions.
7. Save and verify the final workbook and PDF in the configured destination.
8. Prepare the Teams approval draft below and leave it ready for the user to review and submit.

## Teams Approval Draft

- Open Teams Approvals using available supported tools or computer/browser control. Inspect Sent requests for an existing claim for the target month before creating one. If it is already submitted, report its status instead of duplicating it. If a matching unsent form is open, complete that form.
- Research recent approved expense claims in Teams to confirm the template, title convention, approval sequence, amount format, and attachment approach. Use expense claims as precedents rather than unrelated payment requests. Use the personal configuration as a starting point, then verify the current template and recent precedents before reusing its approval sequence.
- Create a request with the verified expense-claim template. Fill the target month/year title, approvers, and exact verified workbook total. Preserve the template's configured second-stage recipients and approval logic. Resolve person suggestions to actual selected approvers and verify the resulting names and order.
- Attach the verified target-month supporting documents. Follow the attachment approach found in the user's previous claims. Prefer an accessible month-folder link when that matches the precedent. Otherwise attach the final Excel workbook and numbered receipt PDF individually through the Teams OneDrive picker. Verify filenames, month, and sync state so older versions or removed receipts are excluded. Use existing links/access where available and avoid broadening sharing beyond the intended approvers.
- Preparing this draft and linking the finalized claim documents in Teams are part of this skill's workflow. Keep receipt processing and workbook creation local. Prefer the files already synced in the configured company OneDrive folder. If sync or attachment access fails, retain the completed local package and populated form and report the exact remaining attachment step.
- Stop before `Send` or any action that submits the approval or notifies approvers. The user reviews and submits the request themselves. If the interface offers an explicit save-draft action, use it and verify the saved draft. Otherwise leave the populated form open and call it an open, unsent form, with a reminder to review before closing or navigating away. Do not claim it is persistently saved without evidence. Preserve a browser tab used for the handoff when the browser tooling requires it.
- Verify the visible title, total, approvers, and completed attachments, then tell the user where the form is open and that it is ready for review and submission. If Teams is inaccessible, report that the draft could not be completed and provide the prepared title, amount, approvers supported by the available precedents, and document paths for manual entry.

## Calendar Matching for Expense Descriptions

- Use Google Chrome browser control to inspect both Outlook Calendar and Google Calendar. Prefer existing signed-in tabs, or open the calendar websites in Chrome. Calendar connectors, local calendar databases, and native calendar apps do not substitute for this requested browser check.
- Read the actual calendar events on each receipt date, including their start/end times, titles, locations, and relevant descriptions. Check relevant visible work/shared calendars as well as the main calendar. Use the configured receipt/local timezone and account for any different timezone displayed by either calendar.
- Compare the receipt's transaction time and, for taxis, pickup/drop-off times with events before and after it. Consider travel time, event location, receipt location when available, and the type of expense. A taxi at 14:00 followed by an in-person meeting at 15:00 is a plausible match when the timing and available context are consistent. A taxi shortly after a meeting may similarly relate to leaving that meeting.
- A clear, plausible match is enough to populate the description without asking the user to confirm each receipt. Write a concise purpose such as `Taxi to meeting with [name] at [venue]`. If the connection is inferred from timing rather than explicitly recorded, use `Likely taxi to ...` and identify inferred matches in the final response. Only include names, venues, origins, destinations, or purposes supported by the receipt or calendar.
- For meals or coffee, use a matching meeting or event when the time and context support it. Do not assume a personal appointment, canceled event, or online meeting explains a business expense. Do not assign the nearest event automatically when multiple events compete or the timing/location is inconsistent. Treat duplicate events across the two calendars as one event.
- If one calendar is inaccessible, continue checking the other. If neither calendar can be checked, complete the claim with the description cells blank. Also leave a description blank when no sufficiently supported match is found, the receipt time is unreadable and the remaining context is insufficient, or the match is ambiguous. Do not fill these cells with `I don't know` or another placeholder.
- Preserve descriptions already supplied or edited by the user. Clear stale descriptions copied from the template before filling new claim rows. Continue preparing the workbook and receipt PDF when calendar access fails, and report the access limitation and blank descriptions in the final response.

## Rules

- Preserve the Excel workbook formatting, formulas, print settings, sheets, and structure.
- Do not overwrite the template folder or original receipt sources unless the user explicitly asks.
- Process receipts and create/edit workbooks locally. Use the configured company OneDrive folder and Teams approval attachments only for the approval-draft workflow above. Do not upload claim files to other external processing services.
- Do not guess unreadable dates, amounts, or vendors; mark these uncertain fields as `I don't know`. For expense descriptions, follow the calendar matching rules above and leave unsupported descriptions blank.
- Keep receipt pages upright, readable, tightly cropped, and not clipped.
- The required finish is a printer/flatbed scan: isolate the paper on white, remove the surrounding table and dark edge shadows, correct skew/perspective where safely possible, and suppress paper shading. A grayscale photo with visible table or a heavy dark outline is not sufficient. Preserve actual printed content; do not invent missing or folded-away text.
- Apply a document-scan filter to every receipt picture before embedding it: neutralize color casts, brighten and even out the paper background, and improve ink contrast. Preserve faint text, stamps, and all original details; avoid hard thresholds that erase faded thermal printing. Never recreate or alter receipt content. Keep original photos unchanged and process locally.
- Keep this workflow compact; do not create helper scripts, extra docs, or temporary project folders unless the user asks. The personal configuration and a requested shareable skill package are permitted setup deliverables.

## Verification

- Reopen the saved workbook from disk and confirm it loads without repair warnings.
- Confirm workbook totals and receipt/reference numbers match the included receipts.
- Verify populated descriptions against the receipt times and calendar evidence, distinguish inferred matches, and confirm unmatched descriptions are blank and user-authored descriptions are preserved.
- Open or render-check the PDF and confirm page count, order, headers, orientation, readability, and cropping.
- Compare filtered receipts with their original photos, checking dates, amounts, and faint text for lost strokes or clipped details; reduce filter strength if needed.
- Confirm the final month folder contains the final Excel workbook and final numbered receipts PDF.
- Verify the Teams draft matches the final workbook total and target month, has the intended approval sequence and supporting attachments, and remains unsent. Distinguish a verified saved draft from a form merely left open.

## Final Response

Report:

- The final month folder path.
- The final Excel workbook path.
- The final receipt PDF path.
- Receipt count and total amount when available.
- Any unreadable or uncertain fields.
- Which calendars were checked, any access limitations, descriptions inferred from calendar matches, and receipt numbers whose descriptions remain blank.
- Teams draft status and location, title, amount, approvers, attachments, and any remaining manual steps. Clearly state that the user must review and submit it themselves.
