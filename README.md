# write-like-a-human

A Claude Code skill that writes or rewrites text so it reads like a specific
person wrote it — not a language model.

Give it a topic and it drafts a finished piece. Paste a draft and it rewrites
it. Paste anything and ask `detect` and it scores how much it smells like AI
(0–100) and tells you exactly why.

---

## Why this exists

Large language models regress to the statistical mean. Ask ten of them to
write about the same thing and you get ten versions of the same beige paragraph:
the same transition words, the same rule-of-three lists, the same em-dashes,
the same “it’s not just X, it’s Y.” Readers have learned to feel it, even when
they can’t name it. And once a reader clocks *“a machine wrote this,”* they stop
trusting the words.

You can’t fix that by asking an AI to “make it sound human” — it just swaps one
set of clichés for another. Fixing it takes a **checklist of the specific tells**
and a disciplined pass to remove each one, then replace the flatness with the
things machines don’t do on their own: specific detail, an actual opinion,
uneven rhythm, a point of view a real person would stake.

That checklist is what this skill is.

## See it work

> Illustrative before/after examples. The skill never invents facts — where a
> real draft lacks specifics, it inserts a `[bracketed placeholder]` for you to
> fill, instead of making something up.

**A blog paragraph**

> **Before (AI):** In today’s fast-paced real estate landscape, cold-calling
> has become an increasingly pivotal tool for investors seeking to unlock new
> opportunities. However, it’s important to note that this approach is not
> without its challenges. By leveraging a strategic mindset and embracing
> innovative outreach, investors can navigate these complexities and ultimately
> drive meaningful results.

> **After (human):** I made about 4,000 cold calls last year and closed two
> deals from them. Two. The math finally caught up with me: my mailers closed
> nine in the same stretch, at a fraction of the hours. So I stopped calling.
> Not because calling doesn’t work — because it wasn’t working for *me*, and I’d
> been too stubborn to read my own spreadsheet.

*What changed:* killed the banned vocabulary (`pivotal`, `leverage`, `navigate`,
`in today’s fast-paced`, `it’s important to note`), dropped the “not without its
challenges” hedge, added concrete numbers, and let a real opinion show.

**A LinkedIn post**

> **Before (AI):** Excited to share that our team has successfully launched a
> new initiative! 🚀 This is a testament to our collective dedication and
> unwavering commitment to excellence. Grateful for the journey. Onwards and
> upwards!

> **After (human):** We shipped it. It took four months longer than I told
> everyone it would, and two features I swore were essential got cut in week
> three. Nobody has missed them. Turns out I was wrong about what mattered,
> which is the most useful thing I learned all quarter.

**Detect mode**

```
/write-like-a-human detect "<paste text>" --score
```

```
[Score: 78/100 — AI-leaning]
Top fixes:
1. "testament to" + "unwavering commitment" — significance inflation (×2)
2. Every sentence is the same length — no burstiness
3. No specific, checkable detail anywhere
```

## How it works

The skill runs your text (or your brief) through a fixed pipeline. Each stage
does one job, in order — the same way a careful human editor would, not all at
once:

1. **Detect the channel.** Blog, LinkedIn, Facebook, Reddit, Instagram, or X.
   Each has different length limits, formatting, and hook rules.
2. **Pick the voice.** Use a named voice, mirror writing samples you paste, or
   apply a saved profile of *your* style (see below).
3. **Draft** (write mode only) with the human rules baked in from sentence one —
   open with substance, ground every claim, take a position, end without a bow.
4. **Three edit passes**, in order:
   - **Vocabulary** — remove the tier-ranked AI words and phrases.
   - **Structure** — break the AI shapes (parallel negation, rule-of-three,
     em-dashes, rhetorical-question-then-answer, tidy endings on every paragraph).
   - **Texture** — add back what’s missing: varied sentence length, sharper word
     choices, specifics, opinions, the occasional aside.
5. **Channel rules** — apply the platform’s norms and kill engagement bait.
6. **Self-audit loop** — the skill asks itself *“what still reads as AI here?”*,
   fixes those, then runs a hard quality checklist before handing anything back.

The reference material (the banned-word tiers, the pattern catalog, the voice
profiles) loads only when a stage needs it, so the skill stays lightweight until
it’s working.

## Learns your voice

Run `onboard` with 1–5 samples of your own writing and the skill distills them
into a named **voice profile** saved under `profiles/`. On later runs it offers
that profile and writes in your style. You can keep several — say a `dev-blog`
voice and a `linkedin` voice — and pick per run.

Profiles are gitignored by default: they encode your personal style and
shouldn’t be pushed to a public repo. In Claude.ai (where files don’t persist
between chats), `onboard` outputs the profile as a block you save and paste back
later.

## What it covers

- **Modes:** `write` (topic/brief in, finished piece out), `rewrite` (fix a
  draft), `detect` (audit + 0–100 score, no rewrite), `onboard` (learn your voice).
- **Channels:** articles/blog, LinkedIn, Facebook, Reddit, Instagram, X.
- **Content types:** educational, instructional, guides, opinion, journal,
  experience, reviews, critical writing.
- **Never invents facts.** Missing specifics become bracketed placeholders you
  fill in, flagged at the end.

## Install (Claude Code, manual-only skill)

Unzip so the folder lands at `~/.claude/skills/write-like-a-human/`:

```bash
# macOS / Linux
unzip write-like-a-human.zip -d ~/.claude/skills/
```

```powershell
# Windows (PowerShell)
Expand-Archive write-like-a-human.zip "$HOME\.claude\skills\"
```

The skill ships with `disable-model-invocation: true`, so Claude won’t auto-run
it. You invoke it explicitly:

```
/write-like-a-human write "a LinkedIn post about why I stopped cold-calling for land deals" --voice sharp-opinionated
/write-like-a-human rewrite "<paste draft>" --channel reddit
/write-like-a-human detect "<paste text>" --score
/write-like-a-human onboard --profile dev-blog        (then paste 1–5 samples)
/write-like-a-human write "release notes intro" --profile dev-blog
```

If your Claude Code build refuses the slash command because of the
`disable-model-invocation` flag (a known bug in some versions), say *“use the
write-like-a-human skill on this”* instead. To let Claude trigger it
automatically, delete the `disable-model-invocation: true` line from `SKILL.md`.

## File structure

```
write-like-a-human/
├── SKILL.md                     # the workflow: modes, passes, audit, quality gate
├── README.md                    # this file
├── .gitignore                   # keeps profiles/ (personal voice data) out of git
├── profiles/                    # your saved voice profiles land here (gitignored)
└── references/
    ├── banned-vocabulary.md     # 3-tier banned words + phrases, with human alternatives
    ├── ai-patterns.md           # structural pattern catalog + false positives + signals
    ├── voices.md                # 5 named voice profiles + mirror-voice procedure
    ├── channels.md              # per-channel rules: blog, LinkedIn, FB, Reddit, IG, X
    └── onboarding.md            # onboard mode: sample intake, profile format, update rules
```

## What came from where

Built by merging the strongest methods from five open humanizer skills into one
write-and-rewrite pipeline:

| Source | What this skill took |
|--------|----------------------|
| [blader/humanizer](https://github.com/blader/humanizer) (MIT) | Wikipedia-derived pattern catalog with before/after examples; the draft → “what still reads as AI?” → final self-audit loop; false-positive guidance; hard em-dash ban |
| [lguz/humanize-writing-skill](https://github.com/lguz/humanize-writing-skill) (MIT) | The three-pass edit structure; tiered banned-vocabulary dictionary; named voice profiles + mirror voice; the pre-delivery quality checklist |
| [Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill) (MIT) | Mode interface (detect/rewrite, flags); 0–100 scoring rubric; burstiness/perplexity principles; soul-injection techniques; emerging 2026 patterns |
| [brandonwise/humanizer](https://github.com/brandonwise/humanizer) (MIT) | Statistical-signals table (burstiness, type-token ratio, trigram repetition); expanded vocabulary tiers; the “if you wouldn’t say it in conversation, don’t write it” rule |
| “The Humanizer” v2.4 (private skill, Bhaskar Pandey) | Channel auto-detection; LinkedIn structural markers; Hook-vs-Value calibration; the originality check; the never-invent-examples placeholder rule |

Pattern research across all five ultimately traces to
[Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing),
maintained by WikiProject AI Cleanup.

## A note on intent

This is a writing-quality tool. It removes the lazy statistical patterns that
make prose read as machine-extruded and replaces them with specificity, rhythm,
and a real point of view. It is not built for — and should not be used for —
misrepresenting authorship where disclosure is required (academic work,
contractual deliverables, platforms with AI-content policies). Good writing
doesn’t trip detectors, because it doesn’t contain the lazy patterns detectors
look for. Fix the writing and that problem solves itself.

## License

MIT. Derived portions remain under their original MIT licenses; see the linked
repositories for their license texts and copyright holders.
