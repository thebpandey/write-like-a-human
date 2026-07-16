# /write-like-a-human

A Claude Code skill that writes new content, or rewrites existing drafts, so
they read like a specific human wrote them. Built by merging the strongest
methods from five humanizer skills into one pipeline, then extending it from
"rewrite only" to "write and rewrite" across six channels.

## What it does

- **Writes from scratch** (topic, brief, outline, or notes in; finished piece out) or **rewrites** an existing draft, or runs a **detect-only** audit with a 0-100 AI-tell score.
- **Learns your voice.** Run `onboard` with 1-5 samples of your writing; the skill distills them into a named voice profile saved under `profiles/`. On later runs it offers your profile (asks which one if you have several, with "none/default" always available), and adapts its output to your style. Multiple named profiles are supported for different registers (say, a dev blog voice and a LinkedIn voice). Profiles are gitignored by default: they encode your personal style and should not be pushed to a public repo. In Claude.ai, where files don't persist between conversations, `onboard` outputs the profile as a block you save to project knowledge and paste back in later sessions.
- **Covers:** articles, blog posts, LinkedIn posts, Facebook posts, Reddit posts, short Instagram captions, and X posts. Content types: educational, instructional, guides, opinion pieces, journals, experiences, product/service reviews, critical writing.
- **Pipeline:** detect channel -> pick voice (named profile or mirror your samples) -> draft (write mode) -> three edit passes (vocabulary, structure, human texture) -> channel rules -> self-audit loop -> quality checklist.
- **Never invents facts.** Missing specifics become bracketed placeholders you fill in, flagged at the end.

## Install (Claude Code, manual-only skill)

Unzip so the folder lands at `~/.claude/skills/write-like-a-human/`:

macOS / Linux:
```bash
unzip write-like-a-human.zip -d ~/.claude/skills/
```

Windows (PowerShell):
```powershell
Expand-Archive write-like-a-human.zip "$HOME\.claude\skills\"
```

The frontmatter ships with `disable-model-invocation: true` and
`user-invocable: true`, so Claude will not auto-trigger it. You invoke it
explicitly:

```
/write-like-a-human write "a LinkedIn post about why I stopped cold-calling for land deals" --voice sharp-opinionated
/write-like-a-human rewrite "<paste draft>" --channel reddit
/write-like-a-human detect "<paste text>" --score
/write-like-a-human onboard --profile dev-blog   (then paste 1-5 samples)
/write-like-a-human write "release notes intro" --profile dev-blog
```

If your Claude Code version refuses the slash command because of the
`disable-model-invocation` flag (a known bug in some builds), say "use the
write-like-a-human skill on this" instead, or update Claude Code.

To let Claude trigger it automatically later, delete the
`disable-model-invocation: true` line from SKILL.md.

## File structure

```
write-like-a-human/
├── SKILL.md                          # workflow: modes, passes, audit, quality gate
├── README.md                         # this file
├── .gitignore                        # keeps profiles/ (personal voice data) out of git
├── profiles/                         # your saved voice profiles land here (gitignored)
└── references/
    ├── banned-vocabulary.md          # 3-tier banned words + phrases, with human alternatives
    ├── ai-patterns.md                # structural pattern catalog + false positives + statistical signals
    ├── voices.md                     # 5 named voice profiles + mirror-voice procedure
    ├── channels.md                   # per-channel rules: blog, LinkedIn, FB, Reddit, IG, X
    └── onboarding.md                 # onboard mode: sample intake, profile format, update rules
```

References load only when needed (progressive disclosure), keeping the
always-loaded footprint small.

## What came from where

| Source | What this skill took |
|--------|----------------------|
| [blader/humanizer](https://github.com/blader/humanizer) (MIT) | Wikipedia-derived pattern catalog with before/after examples; the draft -> "what makes this still obviously AI?" -> final self-audit loop; false-positive guidance (flag clusters, not isolated tells); signs-of-human-writing preservation list; hard em-dash ban |
| [lguz/humanize-writing-skill](https://github.com/lguz/humanize-writing-skill) (MIT) | The three-pass edit structure (vocabulary -> structure -> texture); tiered banned-vocabulary dictionary with human alternatives; named voice profiles + mirror voice + the voice-selection prompt; the secondary-convergence warning; the pre-delivery quality checklist |
| [Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill) (MIT) | Argument/mode interface (detect/rewrite, flags); 0-100 scoring rubric and formula; burstiness and perplexity principles; soul-injection techniques (callbacks, self-correction, imperfect starts); emerging 2026 patterns (paragraph-reshuffling test, whether-closers, symbolic gloss, infomercial hooks, treadmill effect) |
| [brandonwise/humanizer](https://github.com/brandonwise/humanizer) (MIT) | Statistical signals table (burstiness, type-token ratio, trigram repetition); expanded Tier 1/Tier 2 vocabulary; "if you wouldn't say it in conversation, don't write it" always-on principle |
| "The Humanizer" v2.4 (private skill, Bhaskar Pandey) | Channel auto-detection with stated detection; LinkedIn-era structural markers (achievement formula, fake dialogue, information-withheld hooks, ALL-CAPS injection); Hook vs. Value two-stage calibration with saves/comment tests; originality check ("only I could write this"); the never-invent-examples placeholder rule |

Pattern research across all five ultimately traces to
[Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing),
maintained by WikiProject AI Cleanup.

## License

MIT. Derived portions remain under their original MIT licenses; see the
linked repositories for their license texts and copyright holders.

## A note on intent

This skill is a writing-quality tool: it removes the lazy statistical
patterns that make prose read as machine-extruded and replaces them with
specificity, rhythm, and a real point of view. It is not built for, and
should not be used for, misrepresenting authorship where disclosure is
required (academic work, contractual deliverables, platforms with AI-content
policies). Good writing doesn't trip detectors because it doesn't contain the
lazy patterns detectors look for. Fix the writing and that problem solves
itself.
