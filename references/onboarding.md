# Onboarding: Learn the User's Voice

The `onboard` mode turns 1-5 writing samples into a named, reusable voice
profile. A profile is a distilled specification, not stored samples: it
costs little context, and the user's full unpublished writing never sits in
a plain file.

## Intake

1. Accept samples pasted inline or via `--file path` (up to 5 files).
2. Ask for a profile name if not given (`--profile NAME`). Suggest one from
   context (e.g. "linkedin-voice", "dev-blog"). Lowercase, hyphens, no spaces.
3. Sample count rules:
   - 0 samples: ask for at least one. Do not proceed without.
   - 1-2 samples: proceed, but tell the user calibration is weak and the
     profile will improve if they add more later (merge flow below).
   - 3-5 samples: ideal.
   - More than 5: use the 5 most substantial and say which were skipped.
4. Ideal samples are 150+ words each, in the register the user actually wants
   to publish in. If samples are in wildly different registers (a formal
   article and a shitpost), flag it and ask whether they want one blended
   profile or two separate ones.
5. Optional: the user may also provide anti-samples (writing they dislike).
   Record what makes those feel wrong in the "never" section.

## Extraction

Analyze across all samples. Extract onto the template below. Every claim in
the profile must be evidenced by the samples; do not pad dimensions the
samples don't support (write "insufficient sample" instead).

- **Rhythm:** typical sentence length range, burstiness habits, fragment
  usage, paragraph length pattern.
- **Register:** casual/professional/technical placement, contraction usage,
  formality range.
- **Openers:** how they start pieces and paragraphs (story? claim? question?
  context-first?).
- **Closers:** how they end (hard stop? principle? open question? CTA?).
- **Punctuation tics:** parentheticals, colons, semicolons, ellipses,
  one-line paragraphs.
- **Signature phrases:** 3-5 phrases or constructions they actually use.
  Keep these alive in output.
- **Never-list:** words and constructions absent from or disliked in their
  writing (merge with anti-sample findings).
- **Style anchors:** 2-3 verbatim excerpt lines, each under 25 words, that
  best capture the voice. These are the only verbatim content stored.
- **Opinion posture:** hedged or direct? first person frequency? humor?

## Profile file format

Save as `profiles/<name>.md` inside this skill's directory:

```markdown
# Voice profile: <name>
created: <date>  samples: <n>  updated: <date or ->

## Rhythm
...

## Register
...

## Openers / Closers
...

## Punctuation tics
...

## Signature phrases (keep)
- ...

## Never (avoid)
- ...

## Style anchors
> ...
> ...

## Opinion posture
...
```

Keep the whole file under 60 lines. It is a specification for Pass 3, not an
essay.

## Applying a profile

When Step 2 selects a saved profile, load its file and treat it as the
mirror-voice specification: it overrides the named voices for Pass 3
(texture) only. Passes 1 and 2 (banned vocabulary, structural tells) always
run at full strength; a profile never licenses AI patterns. If a signature
phrase in the profile collides with the banned lists, the ban wins, and note
the collision to the user once.

## Updating a profile

If `onboard` runs and `profiles/<name>.md` already exists, ask, never
silently overwrite:

- **Replace:** rebuild from the new samples only.
- **Merge:** re-analyze the existing profile's anchors plus the new samples;
  refresh every section; bump `updated:`.
- **Keep:** abort, leave the file untouched.

To remove a profile, the user deletes the file; offer the exact path.

## Environment behavior

- **Claude Code (writable skill directory):** save the file as above. Confirm
  the saved path to the user. Remind them once, on first save only: if this
  skill folder is a git repo they push, `profiles/` should be in `.gitignore`
  so personal voice data stays off public GitHub.
- **Claude.ai (ephemeral filesystem):** the file will not survive the
  conversation. Still build the profile, then output the complete profile
  block in a code fence with this instruction: "Save this block to your
  project knowledge (or keep it handy). Paste or attach it in any future
  conversation and I'll apply it as your voice profile." When a user pastes a
  profile block in any session, treat it exactly like a saved profile.

## Privacy

Profiles distill style, not content. Do not copy sentences from samples into
the profile except the 2-3 short style anchors. Never include names, client
details, financial figures, or anything sensitive from the samples in the
profile file.
