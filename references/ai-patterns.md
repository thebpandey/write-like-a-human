# AI Structural Patterns Catalog

Merged from blader/humanizer (Wikipedia "Signs of AI writing" catalog),
Aboudjem/humanizer-skill (emerging 2026 patterns, burstiness/perplexity),
brandonwise/humanizer (statistical signals), lguz (structure pass), and The
Humanizer (LinkedIn-era structural tells). Structures are stronger tells than
vocabulary. Fix every instance.

Refreshed against all four upstream repos on 2026-09-13. Entries marked *weak
alone* are defaults a person may choose on purpose: act on them only when
several tells share a passage.

## Contents
1. Sentence-level structures (S1-S16)
2. Content-level patterns (C1-C11)
3. Document-level patterns (D1-D6)
4. Formatting tells (F1-F9)
5. Chatbot leakage (L1-L8)
6. Statistical signals
7. What NOT to flag (false positives)
8. Signs of human writing (preserve these)

---

## 1. Sentence-level structures

**S1: Parallel negation ("Not X, but Y").** Appears 5-10x more in AI text.
Rewrite as a direct positive statement.
Bad: "Not because I lacked skill, but because the context changed."
Good: "The context changed, and I had to adapt."
Also kill clipped tailing negations ("...no guessing", "...no wasted motion").

**S2: Tricolons / rule of three.** Models group everything in threes to sound
comprehensive. Use the natural number. Two is underrated.
Bad: "collaboration, innovation, and problem-solving."
Good: "figuring things out together."

**S3: Rhetorical question + answer.** "What does this mean? It means..."
Lead with the answer.

**S4: Mirror structures.** Consecutive sentences with identical shapes.
Break the symmetry; let the second thought take a different shape and length.

**S5: Superficial -ing tails.** "...showcasing X, reflecting Y, highlighting
Z" tacked on for fake depth. Delete, or promote the content to its own
sourced sentence.

**S6: Copula avoidance.** "serves as / stands as / boasts / features" where
"is / has" works. Simple copulas are clear, not boring.

**S7: Negative parallel drama + staccato runs.** A single short sentence for
emphasis is fine. A run of clipped fragments ("No aesthetic prior. No
nostalgia. The old rules were gone.") is engineered drama. Rewrite as prose.

**S8: False ranges.** "From the Big Bang to dark matter" where the endpoints
are not on a meaningful scale. Name the actual items.

**S9: Synonym / noun-phrase cycling.** "the protagonist... the main
character... the central figure... the hero" within a paragraph. Pick the
clearest term and repeat it. Humans repeat words.

**S10: Aphorism formulas.** "X is the language/currency/architecture of Y",
"X becomes a trap". Replace with the concrete claim it gestures at.

**S11: Repeated sentence openings.** Several sentences in a row start with the
same subject because repetition is handled by rule instead of by ear. Merge the
sentences, change the subject, or lead with the action. Do not ban the word; a
deliberate rhythm ("She came. She saw.") is a human choice. *Weak alone.*
Bad: "She noted the door. She noted the lock on it. She filed both away."
Good: "She noted the door and its lock, then filed both away."

**S12: Stacked qualifiers and leftover hedge debris.** "could potentially",
"might arguably", "to be fair", "in some cases it may", "to some extent",
"in some ways". Two kinds: qualifiers piled up to repair an earlier
overstatement, and a hedge that made sense mid-draft before the claim
solidified. Reread every hedge against its own sentence and delete the ones
whose caution no longer matches the sentence's confidence. Keep scope
statements, safety and legal notices, real corrections, and ordinary human
hedges like "perhaps" or "tends to". *Weak alone.*
Bad: "It could potentially possibly be argued that the policy might have some
effect on outcomes."
Good: "The policy may affect outcomes."

**S13: Uniform hyphenated pairs.** "data-driven", "high-quality", "real-time",
"cross-functional", "end-to-end", "well-documented" hyphenated in every
position. Hyphenate a compound modifier before a noun ("a high-quality
report"); drop it after the verb ("the report is high quality"). *Weak alone.*

**S14: Passive voice and missing subjects.** Agentless constructions that hide
who acts: "no configuration is needed", "the results are preserved
automatically", "it is recommended that", "changes were made". Name the actor
and use active voice where it clarifies. *Weak alone.*

**S15: Colon and question-mark reveals.** "The result: a complete disaster."
"The outcome? Four managers agreed." Weave the reveal into a normal sentence.

**S16: False agency.** Abstractions performing willed human actions: "the data
tells us", "the market rewards", "the decision emerges". Name the human actor,
or address the reader as "you".

## 2. Content-level patterns

**C1: Significance inflation.** "marking a pivotal moment", "a testament to",
"setting the stage for", "evolving landscape". State what the thing is or
does; cut commentary about what it represents.

**C2: Symbolic gloss / meaning-telling.** "The closed factory represents the
decline of American manufacturing." State the fact; let the reader interpret.
Good: "The factory closed in 2009. Three hundred jobs. The high school
dropped football the next year."

**C3: Promotional language.** Travel-brochure adjectives ("nestled",
"vibrant", "breathtaking", "renowned"). Replace adjectives with facts.

**C4: Vague attributions.** "Experts believe", "Industry reports", "Studies
show" without a name. Name the source or drop the claim. Never invent one.

**C5: Notability name-dropping / source-listing as content.** "Featured in
Wired, Forbes, and other outlets." Pick one source and say what it reported.

**C6: Formulaic challenges/outlook sections.** "Despite these challenges...
continues to thrive." State specific problems with dates and data, or cut.

**C7: Inflation of importance sentences.** Sentences that exist only to say
the topic is important. Delete; if it's important, the content shows it.

**C8: Speculative gap-filling.** "Likely grew up...", "maintains a low
profile". Say what isn't known, or cut. Don't dress a guess up as fact.

**C9: Argument residue (arguing with no one).** "This isn't mainly about...",
"I'm not saying...", "To be clear...", "Don't get me wrong...", "Some might
argue... but", "A tempting approach would be...", "It would be easy to dismiss
this as...". The text rebuts an objection or rejects an option that appears
nowhere else in the piece, usually a leftover from an internal draft. Cut the
defense and state the claim. Keep an objection the piece actually names and
answers in full, and keep an option a reader would genuinely weigh. Several
unrelated rejections in a row is a much stronger tell than one.
Bad: "This isn't mainly about prompt length, and I'm not arguing documentation
doesn't matter. The issue is whether the agent can use the instruction."
Good: "The issue is whether the agent can use the instruction when it acts."

**C10: Diff-anchored writing (describing the previous version).** Docs, lesson
copy, and comments that narrate what the text replaced instead of what is true
now: "was added to", "now uses", "has been updated to", "replaces the old",
"previously". Describe the thing as it is. Mention the prior version only in
change logs, release notes, and migration guides.
Bad: "This function was added to replace the previous approach of iterating
through all items, which caused O(n squared) performance."
Good: "This function uses a hash map for O(1) lookups."

**C11: Hedged-enumeration openers.** "There are several ways to...", "There are
a few things to consider", "Generally speaking,", "It is generally a good idea
to". Announcing a vague list instead of committing to an answer. Give the
specific answer first.

## 3. Document-level patterns

**D1: Paragraph-reshuffling immunity.** Test: can you swap paragraph 2 and
paragraph 4 without breaking the piece? If yes, it reads as AI. Make each
paragraph depend on something concrete in the previous one: references,
callbacks, consequences.

**D2: The treadmill effect (low information density).** Paragraphs where
sentences 2-N rephrase sentence 1. Apply the "what's actually new here?"
test per sentence. A paragraph that loses 60% of its words and reads better
is the right outcome. Markers: "In other words,", "Put simply,",
"Essentially,".

**D3: Neat endings everywhere.** AI wraps every paragraph and the whole piece
in a bow. Let at least 30% of paragraphs just stop. End the piece on the
strongest specific point or an open thought, never a recap.

**D4: Whether-closers.** Paragraphs ending "Whether you're X or Y, there's
something for everyone." Cut the closer; end on the strongest specific point.

**D5: Uniform paragraph length and metronomic rhythm.** Vary paragraph length
dramatically. Four sentences, then one line.

**D6: Intro > 3-point list > conclusion template.** The default AI essay
shape. Restructure around an actual argument that unfolds.

## 4. Formatting tells

**F1: Em and en dashes.** The single most reliable formatting tell. Zero in
final output. Replace, in rough preference order: period, comma, colon,
parentheses, restructure. Catch spaced dashes and double hyphens too.

**F2: Boldface overuse and erratic inline bolding.** Strip inline bold except
glossary terms and UI labels. If something deserves emphasis, sentence
structure should provide it.

**F3: Inline-header vertical lists.** "- **Topic:** sentence about topic."
Rewrite as prose unless the content is genuinely a checklist.

**F4: Title Case Headings.** Use sentence case.

**F5: Emoji decoration.** No emoji as section markers or enthusiasm signals.
(Channel exception: see channels.md for Instagram/Facebook allowances.)

**F6: Curly quotes as a fingerprint.** Only meaningful when stacked with
other tells; many editors auto-curl. See false positives.

**F7: A heading restated in the first sentence.** A heading followed by a
one-line paragraph that says the heading again before the real content starts.
Also "This section covers X." Cut the restating line.
Bad: "## Performance / Speed matters. / When users hit a slow page, they leave."
Good: "## Performance / When users hit a slow page, they leave."

**F8: Decoration around headings and lists.** Arrows, emoji, or icons on
headings and list items, and a horizontal rule between every section. Strip
them. If the document opens with a top-level heading that repeats its own
title, let the title stand once.

**F9: Excessive structure.** Headers and bullets imposed on content that is
three paragraphs of continuous thought. Structure earns its place when the
reader will scan or skip; otherwise write prose.

## 5. Chatbot leakage

**L1: Chatbot artifacts.** "I hope this helps!", "Certainly!", "Would you
like me to...", "Great question!". Delete.

**L2: Collaborative framing in published content.** "In this article, we
will explore...", "Let me walk you through". Delete the meta-commentary;
start with the content.

**L3: Placeholder templates left in.** "[Your Name]", "[INSERT SOURCE]",
"2025-XX-XX". Near-definitive tells. Fill or delete.

**L4: Citation markup and UTM leakage.** "citeturn0search0", "oai_citation",
"utm_source=chatgpt.com" in URLs. Strip all of it.

**L5: Reasoning-chain artifacts.** Chain-of-thought scaffolding that leaked
into the finished text: "Let me think", "Breaking this down", "First, I'll",
"Step 1:" where the numbering was meant to stay internal. Delete the
scaffolding and keep the conclusion in the author's voice.

**L6: Knowledge-cutoff disclaimers.** "as of my last training update", "while
specific details are limited", "based on available information", "not widely
documented", "in the provided sources". The model is reporting where its
knowledge ends, then often filling the gap with a guess (see C8). State what
the source does not show, or cut the sentence. Never present a guess as fact.
Bad: "While specific details about the founding are not extensively documented
in readily available sources, it appears to have been established in the 1990s."
Good: "The founding date is not in the available sources." (Or cut it.)

**L7: Acknowledgment loops and confidence theater.** Restating the reader's
question back at them ("You're asking about X..."), and self-rated confidence
("I'm confident that...", "It's worth noting that..."). Delete both and make
the claim.

**L8: Invisible-character residue.** Zero-width space (U+200B), zero-width
joiner (U+200D), soft hyphen (U+00AD), stray non-breaking spaces, and Cyrillic
or Greek homoglyphs standing in for Latin letters. Strip them and normalize to
plain text. This is text hygiene, not detector evasion: these characters break
search, copy-paste, and screen readers.

## 6. Statistical signals

| Signal | Human | AI | Fix |
|--------|-------|----|-----|
| Burstiness (sentence-length variance) | High | Low, metronomic | Mix 3-8 word, medium, and 25-40 word sentences; never 3+ similar in a row |
| Perplexity (word predictability) | Higher | Lowest-probability-avoidant | Choose the second or third word that comes to mind, not the first |
| Type-token ratio | 0.5-0.7 | 0.3-0.5 | Vary vocabulary naturally; but repeat nouns rather than cycling synonyms |
| Trigram repetition | Low | High | Watch for reused 3-word phrases |

## 7. What NOT to flag (false positives)

None of these are reliable indicators alone. Look for **clusters** of tells,
not isolated ones. A single em dash means nothing; em dashes plus rule-of-three
plus "vibrant tapestry" plus a Conclusion section is a confession.

- Perfect grammar and polish (professionals exist)
- Mixed casual and formal registers (often a technical person, not a bot)
- Bland prose without specific tells (dry writing is just dry writing)
- Formal or academic vocabulary generally (AI overuses *specific* fancy words, not all of them)
- Common transition words in isolation (one "however" is not a tell)
- Curly quotes alone (Word, Docs, and most CMSes auto-curl)
- Em dashes alone (many journalists love them; evidence only with formulaic rhythm)
- One short emphatic sentence (flag staccato only in runs)
- "Honestly" or "look" mid-sentence (the tell is the standalone theatrical opener)
- Unsourced claims (most of the web is unsourced)
- Salutations/sign-offs (predate ChatGPT by centuries)
- Watched phrases inside quotations, titles, proper names, or examples where the phrase is being discussed rather than used

## 8. Signs of human writing (preserve these)

When you see these, lean toward leaving the prose alone. Over-editing
destroys what makes a piece sound human.

- Specific, unusual, hard-to-fabricate detail ("the lawyer who used to work upstairs from my dentist")
- Mixed feelings and unresolved tension ("mostly good, but it bothers me and I can't fully explain why")
- Dated, era-bound slang, memes, or in-jokes
- First-person editorial choices the writer could defend
- Genuine asides, parentheticals, and self-corrections
- Natural variety in sentence length
