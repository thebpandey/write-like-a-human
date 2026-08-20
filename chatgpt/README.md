# ChatGPT variant

This directory contains a self-contained ChatGPT Agent Skill package for
`write-like-a-human`.

The package follows the Agent Skills directory format:

```text
write-like-a-human/
├── SKILL.md
├── profiles/
└── references/
    ├── ai-patterns.md
    ├── banned-vocabulary.md
    ├── channels.md
    ├── onboarding.md
    └── voices.md
```

## Install in ChatGPT

1. Download or clone this repository.
2. Create a ZIP archive whose top-level folder is
   `chatgpt/write-like-a-human/`.
3. In ChatGPT, open **Plugins**, select **Skills**, then select
   **Create > Upload from your computer**.
4. Upload the ZIP and review the scan result before installing it.

On macOS or Linux, run this from the repository root:

```bash
cd chatgpt
zip -r write-like-a-human-chatgpt.zip write-like-a-human
```

On Windows PowerShell, run this from the repository root:

```powershell
Compress-Archive -Path .\chatgpt\write-like-a-human `
  -DestinationPath .\write-like-a-human-chatgpt.zip -Force
```

The ZIP must preserve `write-like-a-human/SKILL.md`; do not upload only the
`SKILL.md` file because the workflow depends on the bundled reference files.

## Invoke it

ChatGPT can activate the skill from a matching normal-language request. It does
not require Claude-style slash commands.

Examples:

```text
Use Write Like a Human to rewrite this LinkedIn post in the warm-professional voice: ...
```

```text
Audit this article with Write Like a Human and include the 0-100 score: ...
```

```text
Use Write Like a Human onboarding to create a profile named dev-blog from these samples: ...
```

## Voice profiles

The installed package includes an empty `profiles/` directory. During
onboarding, ChatGPT returns a profile file but does not automatically persist
it in the installed skill. Add the returned `profiles/<name>.md` file through
the ChatGPT Skills editor, or attach it again in a future conversation.

Do not commit personal voice profiles to this public repository.

## Maintenance

The ChatGPT package is intentionally self-contained. When a root reference file
changes, copy the corresponding update into
`chatgpt/write-like-a-human/references/` and review any platform-specific
language in `voices.md` and `onboarding.md`.

OpenAI Skills documentation:
https://help.openai.com/en/articles/20001066-skills-in-chatgpt

Agent Skills format specification:
https://openagentskills.dev/docs/specification
