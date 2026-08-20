---
name: write-like-a-human
description: >
  Write or rewrite articles and social posts so they sound like a specific
  human author instead of generic AI prose. Use when the user asks to draft,
  rewrite, humanize, audit, score, or learn a voice for blog/article,
  LinkedIn, Facebook, Reddit, Instagram, or X content. Detect structural AI
  patterns, apply a selected or mirrored voice, enforce channel rules, and
  audit the final text without inventing facts.
license: MIT
compatibility: Designed for ChatGPT Skills; no external tools required.
metadata:
  author: Bhaskar Pandey
  platform: ChatGPT
  version: "1.0.0-chatgpt"
---

# Write Like a Human

Produce text that reads like a specific, opinionated person wrote it, not a
language model. This applies whether writing from scratch, rewriting a draft,
auditing prose, or learning the user's voice.

North star: **LLMs regress to the statistical mean. Humans are weird,
specific, and inconsistent.** The fundamental AI tell is text that emerges
from nowhere, addressed to no one, with no stake in its claims. If the reader
cannot picture a specific person behind the words, it is not done.

## Activation and inputs

This is the ChatGPT variant of the skill. Do not require a slash command,
terminal path, or CLI flag. Infer intent from the user's normal-language
request. The user may still use `write`, `rewrite`, `detect`, or `onboard` as
mode labels, and may provide shortcuts such as `--channel`, `--voice`,
`--profile`, `--no-profile`, or `--score`. Treat those as optional hints.

Do not use this skill to misrepresent authorship where disclosure is required,
such as academic submissions, contractual work, or platforms with applicable
AI-content policies. The purpose is better writing, not deceptive provenance.

## Modes

Infer the mode from the request.

| Mode | Trigger | What happens |
|------|---------|--------------|
| `write` | User gives a topic, brief, outline, or notes | Full pipeline: brief -> voice -> channel -> draft -> edit passes -> audit -> deliver |
| `rewrite` | User supplies an existing draft | Detect patterns -> edit passes -> audit -> deliver rewrite |
| `detect` | User asks for a review, score, or audit only | Pattern report + 0-100 score. No rewrite. |
| `onboard` | User wants the skill to learn their writing style | Analyze 1-5 samples -> distill a named voice profile -> apply it now -> return a reusable profile file. Procedure in `references/onboarding.md`. |

If the user asks for a score or includes `--score`, prepend a
`[Score: NN/100]` line using the rubric in Step 6.

Voice shortcuts that skip the voice question in Step 2:

- `--profile NAME`: use that bundled or attached profile.
- `--voice NAME`: use a named voice.
- `--no-profile`: ignore bundled profiles for this run.

## Step 0: Load references

Before touching the text, read the supporting files in this skill package:

- `references/banned-vocabulary.md`: tiered banned words and phrases with human alternatives.
- `references/ai-patterns.md`: structural pattern catalog, statistical signals, and false-positive guidance.
- `references/voices.md`: named voices and the mirror-voice procedure.
- `references/channels.md`: channel rules for blog, LinkedIn, Facebook, Reddit, Instagram, and X.
- `references/onboarding.md`: read only for `onboard` mode or when applying a saved profile.

If a supporting file is unavailable, do not pretend it was loaded. Continue
with the available instructions and state the limitation only when it affects
the result.

## Step 1: Detect the channel

Classify the content or brief as **blog/article, LinkedIn, Facebook, Reddit,
Instagram, or X**. Use the detection cues in `references/channels.md`. State
the detection in one short line unless the user requested only the finished
artifact. If ambiguous, default to blog/article and make that assumption clear.

## Step 2: Pick the voice

Follow this order.

1. **Did the user specify a profile, voice, tone, or no-profile preference?**
   Obey it. Map a plain-language tone request to the closest named voice when
   the mapping is clear. Do not ask again.
2. **Check for reusable profiles.** Look for valid profile files under
   `profiles/*.md`, profile text attached to the conversation, or a profile
   pasted inline. Ignore non-profile documentation files.
   - **Exactly one profile exists:** ask once whether to apply it, use a named
     voice, or use the default. If the user asked for immediate output, apply
     the profile and state that choice in the change summary.
   - **Multiple profiles exist:** ask once which profile to use. If the user's
     channel or requested register clearly matches one profile, use it and
     state the assumption.
   - **No profiles exist:** proceed to 3. When asking about voice, mention once
     that `onboard` can build a reusable profile from 1-5 samples.
3. **Did the user provide writing samples in this conversation?** Use the
   **mirror** voice. Build a private working profile of rhythm, word choices,
   openers, punctuation, and verbal habits using `references/voices.md`.
   Apply it without describing the private analysis. Samples of writing the
   user dislikes are also useful; avoid what feels wrong to them.
4. **Did the request already imply a usable tone?** Map it and proceed.
5. **Still unclear?** Ask once, briefly, using the named voices in
   `references/voices.md` plus the mirror option.
6. **User seems impatient or says "just make it human"?** Default to
   **clear-thinker** and proceed.

When a reusable profile is applied, load it and treat it as the mirror-voice
specification for Pass 3.

A profile generated during `onboard` is available in the current conversation,
but it is not automatically written back into the installed ChatGPT skill.
Only claim cross-chat persistence after the user has added the returned file
to the skill or attached it again.

## Step 3: Draft (write mode only)

Write the piece with the human rules present from the first sentence:

- **Open with the substance.** Use a specific story, number, observation, or claim. Never start with setup language, a dictionary definition, or "In this article."
- **Make one idea advance to the next.** Paragraph N+1 must depend on something concrete in paragraph N. If two paragraphs can trade places without damage, merge, reorder, or cut them.
- **Ground abstract claims.** Use a number, name, date, firsthand detail, or concrete consequence. If the brief lacks the detail, do not invent it. Insert a placeholder such as `[ADD: the actual number from your experience]` and flag it after the draft.
- **Take a position.** Educational, review, and opinion content needs a visible point of view. Avoid hedged neutral summaries.
- **End without a bow.** Close on the strongest specific point, a real open question, or an unresolved thought. Never recap the piece or end with "the future looks bright."

Then run the draft through Steps 4-6 exactly as if it were a rewrite. Assume
your own first draft contains AI patterns.

## Step 4: Three edit passes

Run these passes in order.

### Pass 1: Kill the AI vocabulary

Sweep against `references/banned-vocabulary.md`. Replace Tier 1 words on sight.
Use each Tier 2 word no more than once and only where natural. More than two
formal Tier 3 transitions in a short section is a tell; replace them with plain
connectors or remove the transition. Prefer restructuring over mechanical
synonym swaps.

### Pass 2: Break the AI structures

Sweep against `references/ai-patterns.md`. Structures matter more than words.
Highest-priority fixes:

- Parallel negation ("Not X, but Y") -> direct positive statement
- Rule of three / tricolons -> the natural number of items
- Em and en dashes -> zero in the final text; use a period, comma, colon, parentheses, or a rewrite
- Rhetorical question + answer -> lead with the answer
- Superficial `-ing` tails -> cut or promote to a sourced sentence
- Significance inflation -> state what the thing is or does
- Copula avoidance ("serves as", "boasts") -> "is" or "has"
- Infomercial hooks ("The kicker?", "Here's the thing:") -> delete and make the point
- Whether-closers and treadmill restatements -> cut sentences that add nothing
- Uniform paragraph shapes and tidy endings -> let at least 30% of paragraphs simply stop

**Watch for secondary convergence.** Do not replace every removed cliché with
the same new cliché. Vary the construction or remove the connector.

### Pass 3: Add human texture

Apply the selected voice, then add what the cleaned draft lacks:

- **Burstiness.** Mix short (3-8 words), medium, and long (25-40 words) sentences. Never use three or more consecutive sentences of similar length. Fragments can work.
- **Perplexity.** Prefer specific, less predictable wording over the first generic phrase that comes to mind.
- **Specifics over abstractions.** "We burned through $40k and had nothing to show for it" beats "the initiative faced challenges."
- **Opinions.** React to facts instead of only reporting them. Mixed feelings are acceptable.
- **Soul techniques, used sparingly.** Pick two or three per piece: a callback, one self-correction, one parenthetical aside, a mid-thought opener, or honest uncertainty. Do not use all of them.
- **Start some sentences with And or But.**
- **Leave one thought slightly unresolved.**

## Step 5: Apply channel rules

Apply the detected channel's rules from `references/channels.md`: length,
formatting, hook mechanics, and platform-specific engagement-bait bans. For
LinkedIn, run the Hook vs. Value calibration. A hook that attracts the click
but delivers a generic payoff fails.

## Step 6: Self-audit and quality gate

1. Produce the working draft or rewrite.
2. Run one short internal audit: **What still makes this read as AI-generated?**
3. Revise to remove the residual tells.
4. Run every check below before delivery.

- [ ] Zero Tier 1 banned words; each Tier 2 word appears at most once
- [ ] No more than two formal transitions in the piece
- [ ] Zero em or en dashes
- [ ] Zero parallel negations, tricolons, or rhetorical question-and-answer pairs
- [ ] No significance inflation, promotional gloss, or vague attributions such as "experts say"
- [ ] Sentence lengths visibly vary; no three-sentence same-length runs
- [ ] At least 30% of paragraphs end without a tidy conclusion
- [ ] Paragraphs cannot be reshuffled without breaking the argument
- [ ] At least one concrete, hard-to-fabricate detail, or a flagged placeholder
- [ ] The author's opinion is visible somewhere
- [ ] Channel rules are applied; no engagement bait
- [ ] No invented facts, sources, quotes, statistics, or experiences
- [ ] The text reads aloud like a person talking; the reader can picture the author

Do not reveal private chain-of-thought or the hidden working audit. Provide the
finished output and the requested report only.

**Scoring rubric** when the user asks for a score or mode is `detect`:

`score = 4 x patterns_hit + 25 x (1 - burstiness_normalized) + 15 x banned_vocab_ratio`, clamped to 0-100.

0-20 pristine human | 21-40 mostly human | 41-60 mixed | 61-80 AI-leaning | 81-100 pure AI smell.

Treat this as a heuristic writing score, not proof of whether AI authored the
text. Do not claim that any detector can establish authorship with certainty.

## What to protect

- **Meaning and substance.** Rewrite delivery, not the author's argument. If the original has five points, preserve all five.
- **Intelligence level.** Human does not mean simplified or less precise.
- **Real human prose.** Check the false-positive list in `references/ai-patterns.md`. Flag clusters of tells, not isolated words or punctuation.
- **Facts.** Never invent examples, numbers, quotes, sources, or personal experiences. Use placeholders for missing specifics.
- **Against over-correction.** Forced slang, fake vulnerability, and theatrical humanity are worse than clean AI prose. Editing should be invisible.

## Output

- `write` / `rewrite`: deliver the final text, followed by a two-line change summary covering the patterns removed, voice applied, and any placeholders the user must fill. Omit the summary when the user explicitly requests only the finished artifact.
- `detect`: deliver a pattern report table with pattern, quoted text, and fix; include the score and a prioritized top-three fix list.
- `onboard`: apply the generated profile in the current conversation, then return the complete profile as `profiles/<name>.md`. Create an attachable Markdown file when the current surface supports file creation; otherwise use one fenced Markdown block. State clearly that the profile is not persistent until the user adds it to the installed skill through the Skills editor or attaches it in a future chat.

---

## Attribution

This skill merges and adapts, under MIT licenses, work from
[blader/humanizer](https://github.com/blader/humanizer),
[lguz/humanize-writing-skill](https://github.com/lguz/humanize-writing-skill),
[Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill),
[brandonwise/humanizer](https://github.com/brandonwise/humanizer), and
"The Humanizer" (private skill by Bhaskar Pandey). Pattern research ultimately
traces to [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by WikiProject AI Cleanup.

Repository: https://github.com/thebpandey/write-like-a-human
