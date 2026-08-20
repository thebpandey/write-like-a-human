# Onboarding: Learn the User's Voice in ChatGPT

The `onboard` mode turns 1-5 writing samples into a named, reusable voice
profile. A profile is a distilled specification, not a copy of the samples.
This keeps the profile small and avoids storing the user's full unpublished
writing inside the skill.

## Intake

1. Accept samples pasted inline or attached to the ChatGPT conversation. Use up
   to five samples.
2. Ask for a profile name if the user did not provide one. Suggest a name from
   context, such as `linkedin-voice` or `dev-blog`. Use lowercase letters,
   numbers, and hyphens only.
3. Apply these sample-count rules:
   - 0 samples: ask for at least one. Do not proceed without a sample.
   - 1-2 samples: proceed, but state that calibration is weak and can improve
     with more samples later.
   - 3-5 samples: ideal.
   - More than 5: use the five most substantial and identify what was skipped.
4. Prefer samples of at least 150 words in the register the user wants to
   publish. If samples use very different registers, ask whether the user wants
   one blended profile or separate profiles, unless the request already makes
   the intended register clear.
5. Accept anti-samples: writing the user dislikes. Record the disliked traits in
   the profile's `Never` section.

## Extraction

Analyze across all selected samples. Every profile claim must be supported by
those samples. Do not fill unsupported dimensions with guesses; write
`insufficient sample` instead.

Extract:

- **Rhythm:** typical sentence length, burstiness, fragments, and paragraph pattern.
- **Register:** casual, professional, or technical placement; contractions; formality range.
- **Openers:** how pieces and paragraphs start.
- **Closers:** hard stop, principle, open question, or call to action.
- **Punctuation tics:** parentheticals, colons, semicolons, ellipses, and one-line paragraphs.
- **Signature phrases:** 3-5 phrases or constructions the user actually uses.
- **Never-list:** words and constructions absent from or disliked in the user's writing.
- **Style anchors:** 2-3 verbatim lines, each under 25 words, that best capture the voice.
- **Opinion posture:** directness, first-person frequency, uncertainty, and humor.

Keep the analysis private. Return only the finished profile and a brief note on
sample strength.

## Profile file format

Return the profile as `profiles/<name>.md` using this format:

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

Keep the profile under 60 lines. It is a compact specification for Pass 3, not
an essay or a storage location for the source samples.

## Applying a profile

When Step 2 selects a profile bundled in `profiles/`, pasted into the
conversation, or attached as a file, load it and treat it as the mirror-voice
specification. It controls Pass 3 only. Passes 1 and 2 always run at full
strength; a profile never permits banned AI patterns.

If a signature phrase conflicts with the banned lists, the ban wins. Mention
the conflict once in the change summary.

## Updating a profile

When `onboard` targets an existing profile, do not silently replace it. Ask the
user to choose one of these actions unless the request already specifies it:

- **Replace:** rebuild from the new samples only.
- **Merge:** re-analyze the existing profile's style anchors with the new
  samples, refresh every section, and update the `updated:` date.
- **Keep:** leave the existing profile unchanged.

Return the revised complete profile file. Do not claim the installed skill was
updated unless a skill-editing operation actually succeeded.

## ChatGPT persistence behavior

Treat an installed ChatGPT skill as read-only during normal use unless the
current surface explicitly provides and successfully completes a skill-editing
operation.

For every `onboard` run:

1. Apply the generated profile immediately in the current conversation.
2. Return the complete profile as an attachable Markdown file when file
   creation is available. Otherwise return one fenced Markdown block.
3. Tell the user to add the file to the installed skill's `profiles/` directory
   through the ChatGPT Skills editor for cross-chat reuse.
4. If the user does not update the installed skill, they can attach or paste the
   profile in a future conversation.
5. Never say the profile was saved persistently merely because it was generated
   in the conversation.

To remove a bundled profile, the user must remove that profile file from the
skill in the Skills editor and update or reinstall the skill.

## Privacy

Profiles distill style, not content. Do not copy sentences from samples except
for the 2-3 short style anchors. Never include names, client details, financial
figures, credentials, addresses, or other sensitive facts from the samples in
the profile unless the user explicitly requires one as part of their public
voice and understands it will be stored in the profile.

Before the user places a profile in a public repository, warn that personal
voice data can reveal habits and biographical details. Recommend keeping actual
profile files private even when the base skill is public.
