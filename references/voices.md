# Voices

Merged from lguz's voices.md (named profiles + mirror), Aboudjem's voice
profiles (technical/blunt additions), and blader's voice calibration
procedure. Passes 1 and 2 always run the same way; the voice controls what
replaces the killed patterns in Pass 3.

## mirror (preferred whenever samples exist)

Build a private profile from the user's writing samples before rewriting:

1. Sentence length patterns (short and punchy? long and flowing? mixed?)
2. Word choice level (casual? academic? in between?)
3. How they open (jump in? set context? story? claim?)
4. Punctuation habits (parentheticals? semicolons? fragments?)
5. Recurring phrases or verbal tics (keep 1-2 of them in the rewrite)
6. Transition style (explicit connectors, or just starting the next point?)
7. How they close (principle? question? hard stop?)

Match these in the output. If they write short sentences, don't produce long
ones. If they say "stuff" and "things," don't upgrade to "elements" and
"components." If they also show writing they *dislike*, study what feels
wrong to them and avoid it. Don't describe the profile back to them; just
apply it.

To make a mirror profile reusable across sessions, run the `onboard` mode:
it distills the samples into a named file under `profiles/` and future runs
offer it automatically. Procedure and file format in
`references/onboarding.md`.

## clear-thinker (default)

A smart person working through an idea in real time. The writing feels like
thinking, not presenting.
- Rhythm: mix of short and medium; occasional long sentence when an idea needs room; frequent fragments ("That's the thing.")
- Paragraphs: short, 2-3 sentences, some single-sentence; ideas build across paragraphs
- Tone: confident, not aggressive; opinions stated as opinions; comfortable with "I think" and "I'm not sure" when genuine; zero hedging on things they're sure about
- Transitions: mostly invisible; logic connects thoughts; occasional "And"/"But"/"So"
- Signature: real questions mid-text (genuinely open ones), analogies from unexpected domains, occasionally questioning its own argument, endings that leave an idea hanging
- Avoids: jargon, TED-talk energy, "key takeaway", inflated importance

## casual-storyteller

Telling a friend about something over coffee. You can hear the person's voice.
- Rhythm: all over the place; short bursts, then a long rambling sentence held together with commas and "and"; fragments everywhere
- Paragraphs: uneven; length follows the energy of the thought
- Tone: warm, self-deprecating, honest; humor the way a funny person talks, not jokes
- Transitions: conversational and varied ("Anyway," "So then," "Oh, and"); sometimes a hard cut
- Signature: vivid specifics ("the windowless room that always smells like microwave popcorn"), parenthetical asides, occasional direct address, endings that are personal or half-formed
- Avoids: essay structure, topic sentences, anything rehearsed

## sharp-opinionated

Strong takes, zero hedging. A commentator who's been around long enough to
skip the diplomacy.
- Rhythm: punchy, mostly short; long sentences build momentum like a rant; fragments for emphasis ("Wrong.")
- Paragraphs: short and assertive; one idea, stated hard
- Tone: direct, occasionally blunt; says what people are thinking but won't write; strong opinions backed with specific evidence
- Transitions: minimal; often just starts the next point
- Signature: calls out common wisdom as wrong and explains why, concrete numbers, picks a side, short closing lines that land
- Avoids: hedging, false balance, committee-sounding prose

## warm-professional

Credible and polished but unmistakably a person. For business-facing blogs,
LinkedIn, client-facing reviews.
- Rhythm: clean, varied; selective contractions ("it's", "don't")
- Paragraphs: short, 3-5 sentences max
- Tone: dry wit over jokes; acknowledges difficulty honestly ("this part is tricky"); encouragement without sycophancy
- Signature: concrete examples over abstract claims, "we" language where shared experience is real, personal anecdotes when relevant
- Avoids: corporate filler, stiffness, false enthusiasm

## technical

For developer-facing or expert-audience content (tutorials, reviews of tools,
how-to guides with code or specs).
- Rhythm: each sentence makes one point; code-like clarity
- Tone: precise vocabulary, exact terms, no simplifying for its own sake; dry, deadpan observations about technical absurdity are allowed
- Signature: concrete numbers over vague quantities, file paths and versions where relevant
- Avoids: metaphors that don't clarify (most don't), "Note:" as decoration, hype

## Voice selection prompt (when asking the user)

> "Before I write this, what voice do you want?
> - **Clear thinker** - smart person working through an idea. Direct, no decoration.
> - **Casual storyteller** - like telling a friend over coffee. Warm, loose, real.
> - **Sharp & opinionated** - strong takes, punchy sentences, zero hedging.
> - **Warm professional** - credible and polished but still a person.
> - **Technical** - precise, concrete, for expert readers.
> - **Your voice** - paste 1-3 paragraphs of your own writing and I'll match it.
> Or describe what you're going for and I'll adapt."

Wait for the answer. If they seem impatient, default to clear-thinker and go.
