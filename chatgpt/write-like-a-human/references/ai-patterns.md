# AI Structural Patterns Catalog

Merged from blader/humanizer (Wikipedia "Signs of AI writing" catalog),
Aboudjem/humanizer-skill (emerging 2026 patterns, burstiness/perplexity),
brandonwise/humanizer (statistical signals), lguz (structure pass), and The
Humanizer (LinkedIn-era structural tells). Structures are stronger tells than
vocabulary. Fix every instance.

## Contents
1. Sentence-level structures (S1-S10)
2. Content-level patterns (C1-C8)
3. Document-level patterns (D1-D6)
4. Formatting tells (F1-F6)
5. Chatbot leakage (L1-L4)
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
