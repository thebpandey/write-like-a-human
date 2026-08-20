# Channel Rules

Merged from The Humanizer (channel auto-detection, LinkedIn markers, Hook vs.
Value calibration), lguz (LinkedIn special rules), and Aboudjem (--purpose
layers), extended to Facebook, Reddit, Instagram, and X for this skill's
objective. Detect the channel first; apply its rules on top of the universal
passes.

## Detection cues

| Channel | Detect if ANY of |
|---------|------------------|
| Blog/article | Headings, >3,000 chars of structured prose, developed multi-paragraph argument, SEO-style structure |
| LinkedIn | One-sentence-per-line formatting, hashtags, engagement CTA ("Thoughts?"), @mentions, <3,000 chars with no headings, emoji as section markers |
| Facebook | Personal-network tone, event/life-update framing, group-post context, medium length with no headings, casual direct address to friends/followers |
| Reddit | Subreddit conventions (TL;DR, "long-time lurker", markdown, throwaway framing), reply-to-thread context, community jargon |
| Instagram | Caption framing, heavy line breaks, hashtag blocks, references an image/reel, <2,200 chars |
| X (Twitter) | <=280 chars per post or explicit thread structure ("1/"), compressed phrasing |

If ambiguous, default to blog/article and state the assumption.

## Blog / article

- Open with substance: a story, number, or claim. Never "In this article".
- Sentence-case headings; improve generic heading copy.
- Prose over bullets wherever the content flows; no inline-header lists.
- Paragraphs vary in length; the argument must unfold (reshuffle test).
- Close on the strongest specific point or an open question, not a recap.
- Reviews and critical writing: name real tradeoffs, state a verdict, include the one detail only someone who used the thing would know (or flag a placeholder for the user to supply it).

## LinkedIn

Length: under 1,300 chars for short-form, 3,000 max. Density wins.

Bans (beyond universal):
- Engagement bait closers: "Agree?", "Thoughts?", "Drop a comment", "Repost if this resonates"
- Vulnerability performance: "Can I be real for a second?", "I wasn't going to share this but..."
- Fake humility: "I'm no expert, but..." before a confident claim
- Arrow chains (->) as process diagrams; write sentences
- One-line-per-paragraph throughout (the #1 ghostwriter tell); group into 2-4 sentence paragraphs
- ALL-CAPS word injection, "Read that again.", period.separated.emphasis
- Information-withheld hooks that force the "...more" click and deliver nothing
- Achievement-post formula (emotion word + thanks + generic lesson + rocket emoji)
- Fake dialogue format (CEO:/CMO: exchanges laundering an opinion)
- Tag-and-thank lists, hashtag stacks (weave 1-3 or drop), external link in body

### Hook vs. Value calibration (run on every LinkedIn post)

Stage 1 (first 30-60 min): the hook determines initial distribution. Stage 2
(ongoing): dwell time, saves, and substantive comments keep it alive. AI
writing games Stage 1 and dies at Stage 2.

Hooks that clear both stages:
- Specific consequence opener ("I lost my best employee yesterday.")
- One data point with personal stakes ("Conversion dropped 40% in a week. Here's what I found.")
- Contrarian claim backed by an experience only this author could have
- A real story that ends unresolved

Two tests before shipping:
- **Saves test:** is there one referenceable specific (named tool, concrete step, number with context) someone would save to return to?
- **Comment test:** is there a claim specific enough to disagree with, or a tradeoff with no clean answer? "So true!" comments mean the post failed.

## Facebook

- Write like a person talking to people who know them. First person, plain words, contractions.
- Medium length; 1-3 short paragraphs usually. Longer storytelling is fine if it's an actual story with specifics.
- No corporate framing, no hashtag stacks (0-2 max), no LinkedIn-style hooks.
- Emoji: sparing and only where a person would actually use one; never as section markers.
- For business/page posts (educational or promotional): lead with the concrete useful thing, one clear point per post, end with a plain question or nothing. No "Tag someone who needs this."

## Reddit

The most AI-hostile audience on this list. Redditors detect and punish
performative writing instantly.

- Match the subreddit's register. Read the room before writing.
- Zero marketing tone. Zero hashtags. Zero engagement bait.
- Get to the point; if long, add a TL;DR at the top or bottom, written plainly.
- First-person specifics and honest uncertainty build credibility ("I've only tested this on X, so YMMV").
- Markdown is native: paragraphs and occasional lists are fine, but no bold-header bullet formatting, no essay structure.
- Admit tradeoffs and what you don't know. Overclaiming gets shredded in comments.
- Never fabricate experiences ("been doing this 10 years") the user hasn't stated. Placeholder instead.

## Instagram

- Caption serves the visual. Line 1 must stand alone (that's all that shows before "...more").
- Short sentences and line breaks are native here; use them, but the words must still sound like a person, not a template.
- Tone: personal, present-tense, concrete. One idea per caption.
- Hashtags: if used, a small relevant set, placed at the end or first comment; never mid-sentence.
- Emoji allowed where natural; never three in a row, never as bullet decoration.
- CTA only when there's a real reason ("recipe's in the comments"), never "double tap if you agree."

## X (Twitter)

- One idea per post. Compression is the craft: cut every word that doesn't earn its place, but keep human rhythm; a telegram is not a voice.
- No hashtag stuffing (0-1 max). No "🧵" theatrics unless the user wants a thread.
- Threads: each post must stand alone AND advance the argument; the first post is a specific claim or observation, not a promise of value to come ("a thread on how to...").
- Fragments and lowercase are acceptable where they match the user's voice.
- Strong opinions do well; hedged mush does not. Say the thing.

## Content-type layers (apply on top of channel)

- **Educational / instructional / guide:** steps in the doing order; concrete verbs; numbers and exact names; state prerequisites and where it breaks; no "comprehensive guide" framing.
- **Opinion / critical:** thesis visible in the first three sentences; steelman the other side in one line if it strengthens the piece; verdict stated plainly.
- **Journal / experience:** specifics over conclusions; mixed feelings allowed and encouraged; no tidy lesson bolted on the end unless one genuinely emerged.
- **Product / service review:** what was actually used, for how long, what broke, what surprised; a number or two; a clear "who this is for / who should skip it." Flag any fact the user must supply rather than inventing it.
