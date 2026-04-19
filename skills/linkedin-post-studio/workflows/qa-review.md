---
title: QA review workflow
output_type: qa-review
last_updated: 2026-04-20
---

# QA review workflow

## When this workflow loads

Triggers on:

- "review my draft at <path>"
- "QA this post"
- "check my LinkedIn post for issues"
- `/linkedin-qa`

## Required references (loaded in this order)

This workflow relies entirely on the always-loaded references. No additional references needed.

`qa-checklist.md` and `anti-ai-constraint.md` are loaded by the orchestrator on every session. Re-declaring them here would be redundant — that is the point of this workflow.

## Required inputs

- **draft** — a file path to an existing draft OR pasted post text. If neither is provided, ask: "Please paste your post text or give me the path to the draft file."

## Generation steps

1. **Take input.** Accept a file path or pasted text.

2. **If input is a file path:** read the file. Extract the post body from the `## Post text` section if one exists; otherwise treat the full file body as the post.

3. **Run every item in `qa-checklist.md`** against the post:
   - Hook (4 items)
   - Structure (5 items)
   - CTA (3 items)
   - Voice (4 items)
   - Distribution (3 items)
   - Ethics and compliance (4 items)

4. **Run `anti-ai-constraint.md` scan:**
   - Banned vocabulary (regex-match)
   - Banned structures (pattern-match)
   - Required elements: specific proper noun or number, at least one slightly awkward sentence, at least one non-best-practice sentence

5. **For each failed item produce:**
   - Item name
   - What specifically failed — quote the offending excerpt
   - Suggested rewrite

6. **If input was a file and user says "apply fixes":** update the draft file with the rewrites, change `status` from `draft` to `reviewed-qa`, update the `updated` date.

7. **If every item passes:** output "All QA checks passed." Offer to promote status to `approved` if `profile.compliance.pre_approval_required` is false, or to `needs-approval` if it is true.

## Output format

**In chat:** Annotated diff-style report grouped by checklist section. Each item: pass or fail, with a specific note and suggested rewrite for failures.

**Written to file:** If applying fixes, update the existing draft file. If input was pasted text, write a new file at `<data_location>/drafts/YYYY-MM-DD-<slug>-qa-report.md` with frontmatter `format: qa-report`.

## Cross-workflow suggestions

- "Apply all suggested fixes to the draft file?"
- "Submit to compliance reviewer if pre_approval_required?"

## Visual companion (v2+)

Not applicable for QA review.
