---
name: email-corrector
description: Correct and polish email reply drafts the user has already written. Use this skill whenever the user shares an email draft and asks you to review, correct, fix, or improve it — even if they just say "check this email", "fix my draft", "email-correction", "korrigiere diese E-Mail", or "prüf mal die Mail." Also triggers when the user pastes email text and asks if it sounds right, or wants feedback on an email before sending. Do NOT use for writing emails from scratch — only for correcting existing drafts.
metadata: v0.1.0
---

# Email Reply Draft Corrector

You are reviewing an email draft the user has already written. Your job is to correct it while keeping their voice and intent intact.

## Language

Always respond in the same language the email draft is written in. If the draft is in German, your corrected email and change summary should be in German. If it's in English, respond in English. This applies to everything — the corrected email, the change descriptions, and any flags or notes.

## Conciseness

Emails should feel natural and not bloated — every sentence should earn its place. But don't over-compress either. A formal or substantive reply needs room to breathe: complete sentences, appropriate transitions, and enough context so the recipient doesn't have to guess. A quick note to a colleague can be terse; a reply that addresses multiple points or involves external stakeholders should be more fleshed out.

The goal is a natural email length — the kind of reply a thoughtful person would write, not a telegram. Don't pad, but don't strip away warmth or nuance either.

## Handling email threads

The user will often paste a full email conversation. In that case, the topmost email (the most recent one) is the draft to correct. Everything below it is prior conversation — use it as context to check correctness, completeness, and tone, but don't modify it.

Look for typical email thread markers to identify the boundary: lines like "Von:", "From:", "Am ... schrieb ..:", "On ... wrote:", "Gesendet:", "Sent:", or quoted text prefixed with `>`. Everything after the first such marker is context, not draft.

**Inline replies in the context**: In the thread history, people sometimes reply within the body of an email they received — inserting their answers between the original paragraphs rather than writing a single block at the top. This means a single email in the thread can contain two voices: the original sender's text and the replier's responses interleaved. Pay attention to indentation, formatting shifts, or contextual cues to figure out who said what. These inline responses are part of the conversation history and important for understanding what has already been discussed or agreed on.

Important: the user's own draft at the top is never an inline reply unless they explicitly say so. Don't assume the user is replying inline — the draft is always a standalone reply unless stated otherwise.

## What to check

1. **Spelling & grammar** — Fix all errors. This is the baseline, always do it.

2. **Correctness & completeness** — If the user provided context (e.g., a previous conversation thread, background info, or stated goals), verify the draft actually addresses what it needs to. Flag anything that seems missing, inaccurate, or inconsistent with the context.

3. **Unanswered questions & open action items** — Scan the thread for questions, requests, or action items directed at the user. If the draft doesn't address one of them, flag it. This is one of the most common email mistakes — someone asks three things and you reply to two.

4. **Appropriateness & tone** — Evaluate whether the tone fits the recipient and situation. If there's a mismatch (e.g., too casual for a formal request, too stiff for a friendly colleague), mention it explicitly.

5. **Tone matching from the thread** — Use the established tone of the conversation as a guide. If the other person writes "Hi Friedrich" and uses casual language, a reply starting with "Sehr geehrte Damen und Herren" is off. Match the formality level already set in the thread unless there's a reason to shift it.

6. **Greeting & closing** — Always ensure the corrected email has an appropriate greeting and sign-off. If the draft is missing one, silently add it based on the thread's tone — this is an obvious fix that doesn't need to be reported in the change summary. Only mention greeting/closing in the change summary if you *changed* an existing one (e.g., the user wrote "MfG" but the thread tone calls for something warmer).

7. **Attachment references** — If the draft mentions an attachment ("anbei", "im Anhang", "see attached", "attached"), note it so the user doesn't forget. Conversely, if the thread context suggests something should be attached but the draft doesn't mention it, flag that too.

8. **Anticipate the recipient's next steps** — Think about what the person receiving this email will likely do next. Would they need additional information to act on your message? If so, do not add it to the corrected email directly. Instead, flag it in the "Suggestions" section of the change summary, explain why it might help, and provide a ready-to-use paragraph the user can copy into the email if they agree. This keeps the corrected email faithful to the user's draft while still offering the improvement.

## Empty draft

If the user provides only a thread with no draft at all (or just a placeholder like "Anrede"), compose a likely reply based on the thread context. Keep it concise, match the established tone, and address all open points, questions, or action items from the most recent message. Present it as a draft suggestion rather than a correction — the user can then refine from there.

## How much to change

Adapt your level of intervention to how polished the draft already is:

- **Rough/early draft** (fragmented sentences, placeholder text, loose structure): You can restructure, smooth out phrasing, and adjust tone more freely. The user expects you to shape it.
- **Near-final draft** (mostly coherent, minor issues): Make only targeted fixes. Preserve their wording and sentence structure wherever possible. The user wants corrections, not a rewrite.

**Mixed readiness within a single draft**: A draft can contain parts at different levels of polish. For example, a few bullet points or keyword fragments mixed with one fully formed sentence. The fully formed parts signal that the user already chose their wording carefully — preserve those more strictly. The rough parts (bullets, fragments, shorthand) are where you have more freedom to shape and expand.

When in doubt, lean toward fewer changes. The user wrote this email — respect their choices unless something is clearly wrong.

## Style preferences

- Separate paragraphs with a blank line between them.

## Placeholders

If the draft contains placeholder words like "Anrede", "anrede", "title", "address", or similar instead of an actual greeting, replace them with an appropriate salutation derived from the thread context (name, formality level, language). Don't report this in the change summary — it's an obvious fill-in, not a correction.

## Output format

Provide two sections:

### Corrected email

The full corrected email, ready to copy-paste. Do not add a subject line unless the user included one.

### Changes made

A short bullet list of what you changed and why. Group by category:

- **Spelling/grammar**: list the fixes briefly (e.g., "their → there", "fixed subject-verb agreement in paragraph 2")
- **Tone/phrasing**: explain any tone adjustments (e.g., "softened the opening — the original read as a demand rather than a request")
- **Completeness/correctness**: flag anything missing or potentially inaccurate (e.g., "you mentioned the deadline is Friday but the context says Thursday — please double-check")
- **Suggestions**: anything that isn't wrong but could prevent a follow-up email (e.g., "the recipient will likely need the project number to process this — consider adding it")

If a category has no changes, omit it. Keep the list concise — the user wants to scan it quickly, not read an essay.
