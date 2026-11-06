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

## Shared team standard

Receipt scanning, chronological numbering, workbook format, and Teams approval process are the same for every team member. Do not redesign or independently infer these standards during onboarding. Apply the scan filter, calendar rules, and verification requirements below uniformly.

- Use the team's existing expense workbook, preserving its layout, formatting, formulas, category lookup, and print settings. The established sheet is `Exp Claim Form`, with lookup sheet `Table`; period cells are C5/C6, and entry columns are B receipt reference, C date, D category, E description, F account-code formula, G currency, H amount. The original template uses rows 9–23 and totals H24/H41. Inspect actual rows and formulas because inserted/deleted rows can move totals; these coordinates are a baseline, not permission to overwrite a different cell.
- Use KRW and concise English descriptions for this team unless the user explicitly provides a different applicable rule. Keep receipt references sequential and aligned between the workbook and PDF.
- Use the shared Teams `[EC] Expense claim` template owned by `TEC Seoul Forms Admin`. Preserve its standard approval chain: first-stage approver, followed by the configured two-person second stage requiring one approval. Resolve the current named recipients from the live team template or a verified team precedent; do not invent recipients or treat every colleague as having a different approval process. Do not publish staff identities or private approval records in this repository.
- Use `Total Amount Paid` for the verified KRW total, attach the final workbook/PDF or the accessible month-folder link according to the shared workflow, and always leave the approval unsent.
- A colleague's completed claim can confirm that their local file is the shared template; it must not silently redefine team standards. If a local workbook or approval template materially conflicts with this baseline, report the mismatch and ask for the correct team template instead of adapting the workflow to the mismatch.

## Personal configuration and first-use setup

Only storage locations and naming conventions vary as workflow preferences. Claimant identity and signed-in accounts must still belong to the current user; never copy another colleague's identity into a claim.

Load the user's private `user-config.md` from the current session/project or an established private configuration location. Existing adjacent personal configs remain supported for standalone installations. For a shared plugin, keep configuration outside the public repository and versioned plugin cache so updates do not erase it. Use `user-config.example.md` as a starting point; shared standard fields are reference information, not choices to rediscover.

Run onboarding only when locations or naming are missing or invalid:

1. Start with the current workspace, supplied paths, and accessible storage. Locate the user's receipt folder, expense-claim destination, and copy of the team's existing workbook. Search likely finance/expense locations; avoid a laptop-wide search by default. If access is unavailable, ask for the locations or required files.
2. Inspect existing folder and filename patterns. Confirm that the located workbook matches the shared team standard. Do not ask the user to choose scanning, numbering, spreadsheet layout, currency, or approval stages.
3. Present the proposed receipt source, claim destination, template location, month-folder pattern, workbook filename, and receipt-PDF filename together. Ask one concise question to confirm or correct these on first use. While awaiting that answer, continue read-only inspection. Do not create or move claim files into an unconfirmed destination. Explicit locations/naming already provided by the user count as confirmation.
4. Establish the current claimant and relevant signed-in Chrome/Teams accounts from available user-specific evidence, asking only if ambiguous. Check integration availability without requiring it to finish setup. Calendar or Teams unavailability does not trigger repeated onboarding.
5. Save the confirmed locations/naming and claimant/account context in private configuration. Preserve any existing personal setup. Do not rewrite shared `SKILL.md` for one person. Read the configuration back and report its location; claim persistence only after verifying a save. If persistent storage is unavailable, explain the limitation and provide a private configuration file for later use.
6. On later runs, reuse this setup, verify that paths/template still exist, and ask again only for missing, changed, or conflicting settings. Verify the current shared Teams template before drafting; research past claims only to resolve missing shared details or a mismatch, not to invent a separate approval workflow for each user.

Store operational settings only; exclude credentials, receipt contents, and private calendar descriptions. Never commit personal configuration, company workbooks, receipts, or approval records to the public repository.

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
- Apply the shared team approval template and process. When the live template leaves details unresolved, research recent approved expense claims to confirm those shared details, title convention, amount format, and attachment approach. Use expense claims as precedents rather than unrelated payment requests. Use the personal configuration as a starting point, then verify the current template and recent precedents before reusing its approval sequence.
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
