# Voices

Merged from lguz's voices.md (named profiles + mirror), Aboudjem's voice
profiles (technical/blunt additions), and blader's voice calibration
procedure. Passes 1 and 2 always run the same way; the voice controls what
replaces the killed patterns in Pass 3.

## mirror (preferred whenever samples exist)

Build a private working profile from the user's writing samples before
rewriting:

1. Sentence length patterns (short and punchy? long and flowing? mixed?)
2. Word choice level (casual? academic? in between?)
3. How they open (jump in? set context? story? claim?)
4. Punctuation habits (parentheticals? semicolons? fragments?)
5. Recurring phrases or verbal tics (keep 1-2 of them in the rewrite)
6. Transition style (explicit connectors, or just starting the next point?)
7. How they close (principle? question? hard stop?)

Match these in the output. If they write short sentences, do not produce long
ones. If they say "stuff" and "things," do not upgrade them to "elements" and
"components." If they also show writing they dislike, study what feels wrong
to them and avoid it. Do not describe the private working profile back to
them; apply it.

To make a mirror profile reusable across ChatGPT conversations, run the
`onboard` mode. It distills samples into a named profile file. ChatGPT can use
the profile immediately in the current conversation. For future conversations,
the user must add the returned file to the installed skill's `profiles/`
directory through the Skills editor or attach/paste it again. Procedure and
file format are in `references/onboarding.md`.

## clear-thinker (default)

A smart person working through an idea in real time. The writing feels like
thinking, not presenting.

- Rhythm: mix of short and medium; occasional long sentence when an idea needs room; frequent fragments ("That's the thing.")
- Paragraphs: short, 2-3 sentences, some single-sentence; ideas build across paragraphs
- Tone: confident, not aggressive; opinions stated as opinions; comfortable with "I think" and "I'm not sure" when genuine; zero hedging on things they are sure about
- Transitions: mostly invisible; logic connects thoughts; occasional "And"/"But"/"So"
- Signature: real questions mid-text, analogies from unexpected domains, occasional self-questioning, endings that leave an idea hanging
- Avoids: jargon, TED-talk energy, "key takeaway", inflated importance

## casual-storyteller

Telling a friend about something over coffee. You can hear the person's voice.

- Rhythm: varied; short bursts, then a long rambling sentence held together with commas and "and"; fragments are common
- Paragraphs: uneven; length follows the energy of the thought
- Tone: warm, self-deprecating, honest; humor the way a funny person talks, not scripted jokes
- Transitions: conversational and varied ("Anyway," "So then," "Oh, and"); sometimes a hard cut
- Signature: vivid specifics, parenthetical asides, occasional direct address, endings that are personal or half-formed
- Avoids: essay structure, topic sentences, anything rehearsed

## sharp-opinionated

Strong takes with minimal hedging. A commentator who has enough experience to
skip unnecessary diplomacy.

- Rhythm: punchy, mostly short; long sentences build momentum; fragments for emphasis ("Wrong.")
- Paragraphs: short and assertive; one idea, stated clearly
- Tone: direct, occasionally blunt; strong opinions backed by specific evidence
- Transitions: minimal; often starts the next point directly
- Signature: challenges common wisdom and explains why, uses concrete numbers, picks a side, ends with short lines that land
- Avoids: hedging, false balance, committee-sounding prose

## warm-professional

Credible and polished but unmistakably written by a person. Suitable for
business-facing blogs, LinkedIn, and client-facing reviews.

- Rhythm: clean and varied; selective contractions ("it's", "don't")
- Paragraphs: short, usually 3-5 sentences maximum
- Tone: dry wit over jokes; acknowledges difficulty honestly; encourages without sycophancy
- Signature: concrete examples over abstract claims, "we" language only where shared experience is real, personal anecdotes when relevant
- Avoids: corporate filler, stiffness, false enthusiasm

## technical

For developer-facing or expert-audience content such as tutorials, tool
reviews, how-to guides, code explanations, or specifications.

- Rhythm: each sentence makes one point; code-like clarity
- Tone: precise vocabulary, exact terms, no simplifying for its own sake; dry observations about technical absurdity are allowed
- Signature: concrete numbers over vague quantities, file paths and versions where relevant
- Avoids: metaphors that do not clarify, decorative "Note:" labels, hype

## Voice selection prompt

When a voice question is necessary, ask once:

> Before I write this, what voice do you want?
> - **Clear thinker**: smart person working through an idea. Direct, no decoration.
> - **Casual storyteller**: like telling a friend over coffee. Warm, loose, real.
> - **Sharp and opinionated**: strong takes, punchy sentences, minimal hedging.
> - **Warm professional**: credible and polished but still a person.
> - **Technical**: precise and concrete for expert readers.
> - **Your voice**: paste or attach 1-3 paragraphs of your writing and I will match it.
> Or describe the result you want and I will adapt.

Wait for the answer when it materially changes the output. If the user requests
immediate output or seems impatient, default to clear-thinker and proceed.
