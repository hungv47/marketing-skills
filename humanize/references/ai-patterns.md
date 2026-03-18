# AI Writing Patterns — Detection & Fix Reference

33 patterns across 7 categories. Each pattern includes severity:
- **Hard Tell** — Immediately flags content as AI-generated. Fix before publishing.
- **Soft Tell** — Suspicious in clusters. Fix when 3+ appear in the same piece.

---

## High-Frequency AI Vocabulary

These words appear significantly more often in post-2023 AI-generated text than in human writing. A single instance is fine — clusters of 3+ in one piece are a signal.

> additionally, align (with), comprehensive, crucial, cutting-edge, delve, dynamic, elevate, empower, endeavor, enhance, ensure, evolving, foster, furthermore, garner, harness, highlight, holistic, implement, innovative, interplay, intricate, landscape, leverage, meticulous, moreover, multifaceted, navigate, notably, optimize, overarching, pivotal, realm, robust, seamless, showcase, streamline, tapestry, testament, transformative, underscore, utilize, vibrant

**Sophistication-seeking words** (above) are chosen to sound impressive. The list below covers a different failure mode:

**Lazy extremes** — false-authority words that substitute for evidence:

> always, every, everyone, everybody, never, nobody

These make claims sound definitive without providing proof. "Everyone struggles with onboarding" is unfalsifiable filler. "68% of trial users drop off before day 3" is a claim. Replace with specifics or scope the claim honestly.

**Rule:** When you spot 3+ of these in a paragraph, flag the paragraph for rewrite. Replace each with a plain-language equivalent or delete if the sentence works without it.

---

## High-Frequency AI Phrases

Exact phrases to search for. Unlike the vocabulary list (individual words that cluster), these are multi-word constructions that are almost always AI-generated.

### Emphasis Crutches (delete on sight)
- "Full stop."
- "Let that sink in."
- "Make no mistake"
- "Read that again."
- "And that's the point."

### Meta-Commentary (delete — the writing should speak for itself)
- "In this section, we'll..."
- "As we'll see..."
- "Let me walk you through..."
- "Before we dive in..."
- "Here's the thing:"

### Performative Emphasis (delete — if it needs a promise, it's not convincing)
- "I promise"
- "This is what X actually looks like"
- "And I mean that"
- "Seriously."
- "No, really."

### Business Jargon (replace with plain equivalents)
Note: "navigate" and "landscape" also appear in the vocabulary list above. The vocabulary list flags clusters; this table provides direct replacements.

| AI Jargon | Plain Equivalent |
|-----------|-----------------|
| navigate | handle |
| unpack | explain |
| lean into | accept |
| landscape | situation |
| deep dive | analysis |
| double down | commit |
| circle back | revisit |
| moving forward | next |

---

## Category 1: Content Structure

### 1. Predictable Paragraph Structure
**Severity:** Hard Tell
**Description:** Every paragraph follows the same template: topic sentence → explanation → example → transition. Human writing varies — some paragraphs are one sentence, others build through three ideas before landing.
**Example:**
> "Project management is essential for team success. It helps teams stay organized and meet deadlines. For example, companies using project management tools see 28% better results. This shows the importance of proper planning."
**Fix:** Vary paragraph length between 1-6 sentences. Let some paragraphs start with evidence, others with a question, others mid-thought. Delete the topic sentence entirely when the paragraph is clear without it.

### 2. Symmetric Lists
**Severity:** Soft Tell
**Description:** Every list item is the same length, same structure, same level of detail. Human lists are messy — the important item gets three lines, the obvious one gets four words.
**Example:**
> - **Communication:** Effective communication ensures all team members are aligned...
> - **Organization:** Strong organization skills help maintain project timelines...
> - **Leadership:** Good leadership inspires team members to perform...
**Fix:** Let list items vary in length. The most important point gets the most space. Some items can be a single phrase. Drop the bold label when the item is self-explanatory.

### 3. Section Uniformity
**Severity:** Soft Tell
**Description:** Every section is roughly the same length and follows the same internal structure. Human writers spend 500 words on the thing that matters and 50 on the thing that doesn't.
**Example:** A blog post where "Why It Matters," "How It Works," and "Getting Started" are each exactly 3 paragraphs with a subheading, a list, and a closing line.
**Fix:** Let section length reflect importance. Cut thin sections entirely or merge them into a stronger section. Not every section needs a subheading.

### 4. Template Transitions
**Severity:** Hard Tell
**Description:** Connective tissue between sections follows formulaic patterns: "Now that we've covered X, let's look at Y" or "With that in mind." Human writing either transitions implicitly or uses a single word.
**Example:**
> "Now that we've explored the benefits, let's dive into the implementation details."
**Fix:** Delete the transition entirely. If the reader can't follow without it, the section order is wrong. When a transition is genuinely needed: "But," "So," "Here's the thing," or just a line break.

### 5. Formulaic "Challenges and Future" Sections
**Severity:** Hard Tell
**Description:** AI-generated articles include formulaic sections that follow a predictable pattern: acknowledge challenges → "despite these challenges" → optimistic future outlook. The structure is: problem → pivot → hope.
**Example:**
> "Despite these challenges, the future of remote work looks promising. As technology continues to evolve, teams will find new and innovative ways to collaborate effectively. The possibilities are truly exciting."
**Fix:** If challenges are real, state them with specifics and consequences. If the future section adds nothing concrete (no dates, no plans, no evidence), delete it. "The future looks bright" is never a useful sentence.

---

## Category 2: Language Quirks

### 6. Paired Synonyms
**Severity:** Hard Tell
**Description:** Two words that mean the same thing joined by "and" — a verbal tic AI uses for emphasis that humans rarely do.
**Example:** "clear and concise," "robust and reliable," "innovative and cutting-edge," "simple and straightforward," "comprehensive and thorough"
**Fix:** Pick one. "Clear" or "concise" — never both. If you can't pick, neither word is specific enough. Replace with what you actually mean.

### 7. Copula Avoidance
**Severity:** Hard Tell
**Description:** Substituting elaborate constructions for simple "is/are": "serves as," "stands as," "represents," "marks," "boasts," "features," "offers." AI does this to sound more sophisticated; it just sounds bureaucratic.
**Example:**
> "Gallery 825 serves as LAAA's primary exhibition space and stands as a testament to the organization's commitment to the arts."
**Fix:** Use "is." "Gallery 825 is LAAA's exhibition space." Simple copulas are invisible to the reader — elaborate substitutes draw attention to themselves.

### 8. Hedge Stacking
**Severity:** Hard Tell
**Description:** Multiple hedges in one sentence: "It's worth noting that this could potentially help somewhat improve..." Human writers hedge once or commit.
**Example:**
> "It's important to note that this approach might potentially offer some benefits in certain situations."
**Fix:** Commit or cut. "This approach works when [specific condition]." One hedge per paragraph maximum. If you're not sure enough to state it, cut the claim entirely.

### 9. Superficial -ing Phrase Tacking
**Severity:** Hard Tell
**Description:** Appending present participle phrases to sentences to add fake analytical depth: "highlighting the importance of," "underscoring the need for," "showcasing the potential of," "reflecting broader trends in." The -ing phrase adds no information the sentence didn't already convey.
**Example:**
> "The temple's vibrant colors reflect centuries of regional tradition, showcasing the community's deep connection to its heritage and highlighting the enduring importance of cultural preservation."
**Fix:** Delete the -ing phrase. If the sentence still makes sense (it almost always does), the phrase was filler. If the -ing phrase genuinely adds new information, promote it to its own sentence.

### 10. Vague Attributions
**Severity:** Hard Tell
**Description:** Attributing claims to unnamed authorities: "Experts argue," "Industry reports suggest," "Observers have noted," "Some critics believe," "Studies show." Human writers name their sources.
**Example:**
> "Industry experts believe this technology will play a crucial role in the future of healthcare. Several studies have shown promising results."
**Fix:** Name the source and date. "A 2024 Stanford study found..." or "Kent Beck argues..." If you can't name the source, the claim is unsubstantiated — either find the source or cut the claim.

---

## Category 3: Style Tells

### 11. Exclamation Inflation
**Severity:** Hard Tell
**Description:** Exclamation marks used for enthusiasm rather than genuine surprise or command. More than one per 500 words signals AI.
**Example:**
> "Great news! Our new feature is live! Try it today and see the difference!"
**Fix:** Remove all exclamation marks. Add back only where the sentence genuinely demands one (commands, actual surprise, direct quotes). Maximum one per 500 words.

### 12. Em-Dash Overuse
**Severity:** Soft Tell
**Description:** Em dashes appearing 3+ times in a short piece as a structural crutch — used to insert asides — where commas or periods would work — creating a choppy rhythm.
**Example:**
> "Our platform — built for modern teams — offers real-time collaboration — making it easy to stay aligned — no matter where your team is located."
**Fix:** Keep one em dash per 300 words maximum. Replace others with commas, periods, or parentheses. Often the aside can be cut entirely.

### 13. Emoji as Punctuation
**Severity:** Hard Tell
**Description:** Emojis used as bullet points, section markers, or emphasis rather than genuine expression. Especially: rocket, fire, check mark, point-right, lightbulb.
**Example:**
> "Key features: Speed, Reliability, Scale"
**Fix:** Remove all structural emojis. Use emojis only where the brand voice genuinely calls for them and only in casual channels (social, chat). Never in long-form content.

### 14. Bold-Keyword Highlighting
**Severity:** Soft Tell
**Description:** Bolding the "key term" in every paragraph as a scanning aid, or using inline bold headers ("**User Experience:** The user experience...") to structure prose. Human writers bold for emphasis on specific phrases, not systematically.
**Example:** Every paragraph has one **bolded keyword** that summarizes the point, or every list item starts with a **Bold Label:** followed by explanation.
**Fix:** Remove systematic bolding. Bold only when a specific phrase genuinely needs emphasis — max 2-3 per 1,000 words. Convert bold-label lists into flowing prose when the items aren't genuinely parallel.

### 15. Title Case in Headings
**Severity:** Soft Tell
**Description:** Capitalizing All Main Words In Every Heading. AI defaults to title case; most modern style guides and human writers use sentence case.
**Example:**
> "Strategic Negotiations And Global Partnerships In The Modern Era"
**Fix:** Use sentence case: "Strategic negotiations and global partnerships." Only capitalize the first word and proper nouns unless the brand style guide explicitly requires title case.

---

## Category 4: Communication Habits

### 16. False Empathy Opener
**Severity:** Hard Tell
**Description:** Opening with performed understanding: "I understand how frustrating this can be" or "That's a great point" before the actual response. Human empathy is specific, not formulaic.
**Example:**
> "I completely understand where you're coming from. This is indeed a challenging situation that many teams face."
**Fix:** Delete the empathy line. Start with the substance. If empathy is needed, make it specific: "Migrating mid-sprint is brutal" instead of "I understand how challenging that can be."

### 17. "Great Question" Prefix
**Severity:** Hard Tell
**Description:** Validating the reader before answering: "Great question!" "That's an excellent point." "This is such an important topic." Empty calories before the meal.
**Example:**
> "Great question! This is something many people wonder about. Let me break it down for you."
**Fix:** Delete entirely. Answer the question. The reader knows their question is good — they asked it.

### 18. Premature Certainty
**Severity:** Soft Tell
**Description:** Confident claims about contested or nuanced topics without qualification. AI tends toward definitive statements where humans would hedge appropriately.
**Example:**
> "The best approach is always to use microservices for any application that needs to scale."
**Fix:** Add genuine nuance — not hedge stacking (pattern #8), but actual conditions: "Microservices make sense when your team is large enough to own separate services. Below ~20 engineers, the coordination overhead usually costs more than the flexibility gains."

### 19. Caveat Avalanche
**Severity:** Hard Tell
**Description:** Excessive disclaimers and qualifiers, especially at the end: "Of course, results may vary. It's important to consider your specific situation. Always consult with a professional." CYA energy.
**Example:**
> "However, it's important to note that every situation is unique. Results may vary depending on your specific circumstances. Always consult with relevant stakeholders before making any decisions. This is not professional advice."
**Fix:** One caveat maximum, and only when it's genuinely important. Place it inline where it's relevant, not as a footer. If you need to disclaim, make it specific: "This won't work if your database is sharded" instead of "results may vary."

### 20. Permission-Seeking Closers
**Severity:** Hard Tell
**Description:** Ending with "Let me know if you'd like me to..." or "Would you like me to elaborate on any of these points?" or "Feel free to ask if you have any questions!" Signals assistant mode.
**Example:**
> "I hope this helps! Let me know if you'd like me to go deeper into any of these areas. Feel free to reach out if you have any other questions!"
**Fix:** End with the content. If there's a natural next step, state it as a recommendation, not an offer: "Next step: audit your top 5 pages against these patterns" instead of "Let me know if you'd like me to audit your pages."

---

## Category 5: Filler Patterns

### 21. Throat-Clearing Intros
**Severity:** Hard Tell
**Description:** One or more sentences before the actual content begins: "In today's fast-paced digital landscape..." or "When it comes to marketing..." These are warm-up sentences the writer (or AI) needed but the reader doesn't.
**Example:**
> "In today's rapidly evolving business landscape, companies of all sizes are discovering the importance of effective communication strategies."
**Fix:** Delete every sentence before the first one that says something specific. The right opening is usually your second or third sentence.

**Also flag these sentence starters** (common residual tells after stripping the obvious throat-clearers):
- **Wh- setup starters:** "What makes this hard is..." → State the constraint directly: "The constraint is..."
- **Paragraphs starting with "So"** — conversational filler disguised as a logical connector. Delete "So" or replace with the actual logical link.
- **Sentences starting with "Look,"** — performs directness rather than being direct. Delete "Look," and the sentence is already direct.

### 22. "Comprehensive" Promise
**Severity:** Hard Tell
**Description:** Promising completeness: "This comprehensive guide will cover everything you need to know about..." or "Here's a complete breakdown of..." Human writers rarely promise comprehensiveness because they know they can't deliver it.
**Example:**
> "This comprehensive guide will walk you through everything you need to know about content strategy, from planning to execution."
**Fix:** Delete the promise. Start with the content. The reader will judge completeness for themselves.

### 23. Redundant Bridges
**Severity:** Soft Tell
**Description:** Sentences that exist only to connect two ideas that don't need connecting: "With this in mind," "Building on that," "Taking it a step further," "That said." Bridge words are fine; bridge sentences are filler.
**Example:**
> "Taking all of this into consideration, it becomes clear that we need to think about the next step. Building on the foundation we've established, let's explore what this means in practice."
**Fix:** Delete the bridge sentence. If the next paragraph doesn't follow logically without it, the structure is wrong — reorganize rather than bridge.

### 24. Safety-Net Qualifier
**Severity:** Soft Tell
**Description:** Softening every recommendation: "You might want to consider..." "One approach could be..." "It may be worth exploring..." Human experts state their recommendation, then qualify only when genuinely uncertain.
**Example:**
> "You might want to consider looking into implementing some form of automated testing, as it could potentially help reduce bugs."
**Fix:** State the recommendation directly: "Add automated tests to your CI pipeline." Qualify only when the recommendation genuinely depends on context the reader has and you don't.

### 25. Generic Positive Conclusions
**Severity:** Hard Tell
**Description:** Vague upbeat endings that promise a bright future without specifics: "The future looks bright," "Exciting times lie ahead," "The possibilities are endless." Distinct from formulaic conclusions (#5) — this is specifically the empty optimism problem.
**Example:**
> "As we look to the future, the possibilities are truly exciting. With continued innovation and dedication, we can achieve remarkable things together."
**Fix:** Replace with a specific, measurable next step or prediction. "Q3 goal: reduce onboarding time to under 48 hours" instead of "the future looks bright." If there's no concrete forward-looking statement to make, end before the conclusion.

---

## Category 6: Structural Tics

### 26. Rule of Three Overuse
**Severity:** Soft Tell
**Description:** AI forces ideas into groups of three to appear comprehensive and rhythmic. Human writing groups by what actually exists, not by what sounds balanced.
**Example:**
> "The conference featured keynote sessions, panel discussions, and networking opportunities — creating a vibrant atmosphere of learning, collaboration, and innovation."
**Fix:** Use the actual number. If there are two things, list two. If there are five, list five (or the most important two). Don't pad to three or trim to three for rhythm.

### 27. Negative Parallelism
**Severity:** Soft Tell
**Description:** "It's not just X; it's Y" / "Not only...but also..." AI overuses this construction for dramatic emphasis. Occasional use is fine; every-other-paragraph use is a tell.
**Example:**
> "It's not just about the technology; it's about the people. It's not just a tool; it's a movement."
**Common variants** (same construction, different wrapper):
- "Not because X. Because Y."
- "[X] isn't the problem. [Y] is."
- "The answer isn't X. It's Y."
- "It feels like X. It's actually Y."
- "stops being X and starts being Y"

A single instance of any variant is fine. The tell is clusters — two or more binary contrasts in the same piece signals AI structure.

**Fix:** State the positive claim directly. "The value is in how teams use it" instead of "It's not just a tool; it's a movement." Reserve the "not just X; it's Y" structure (or any variant) for one genuinely surprising contrast per piece maximum.

### 28. Synonym Cycling
**Severity:** Soft Tell
**Description:** AI has repetition-penalty code that causes excessive synonym substitution. The same entity gets called "the platform," "the tool," "the solution," "the system," "the product" across consecutive paragraphs. Human writers repeat the same word or use pronouns.
**Example:** A product review that cycles through "the device," "the gadget," "the unit," "the hardware," "the product" when referring to the same phone.
**Fix:** Pick one term and stick with it. Use "it" for subsequent references in the same paragraph. Synonym cycling draws more attention than repetition — readers notice inconsistency more than they notice a word appearing twice.

### 29. False Ranges
**Severity:** Soft Tell
**Description:** Using "from X to Y" constructions where X and Y aren't meaningfully on a scale or spectrum. AI uses this to sound comprehensive.
**Example:**
> "The platform handles everything from the singularity of the Big Bang to the grand cosmic web of modern data infrastructure."
**Fix:** List the actual things. "The platform handles ingestion, transformation, and storage" is clearer than a false range. Use "from X to Y" only when X and Y are genuine endpoints of a meaningful spectrum.

### 30. Colon-List Dependency
**Severity:** Soft Tell
**Description:** Over-reliance on "Here's what/why/how:" followed by a bulleted list. Human writing integrates information into prose more often than it lists.
**Example:**
> "Here's why this matters:
> - Reason one
> - Reason two
> - Reason three"
**Fix:** Integrate 2-3 items into a sentence. Reserve lists for 4+ genuinely parallel items. "This matters because [reason one], and teams that ignore it [consequence]."

---

## Category 7: Agency & Perspective Tells

### 31. False Agency
**Severity:** Hard Tell
**Description:** Inanimate things given human verbs — attributing intention, desire, or action to concepts, data, markets, or abstractions. AI does this to sound analytical; it reads as evasive because it hides who actually did the thing.
**Example:**
> "The data tells us that retention is declining. The culture shifts toward remote work. The market rewards companies that move fast."
**Fix:** Name the actor. "We looked at the data — retention dropped 12% in Q3." "More employees are choosing remote." "Customers are switching to faster competitors." If you can't name who does the verb, the sentence is too abstract.

### 32. Narrator-from-a-Distance
**Severity:** Soft Tell
**Description:** Floating above the scene, observing and commentating without being inside it. The writing reads like a documentary voiceover — omniscient, detached, slightly condescending. AI defaults to this because it has no actual position in the scene.
**Example:**
> "Nobody designed this to happen. This is simply how organizations evolve. People tend to avoid hard conversations until the cost becomes unavoidable."
**Fix:** Put the reader (or the writer) inside the scene. Replace "nobody" and "people" with "you" or "we." See the Reader Presence table in [voice-injection.md](voice-injection.md) for specific rewrites.

### 33. Vague Declaratives
**Severity:** Hard Tell
**Description:** Announcing that something is important, significant, or high-stakes without naming what it is or why. The sentence performs emphasis instead of providing it. AI uses these as paragraph openers to build false momentum.
**Example:**
> "The implications are significant. The stakes are high. This matters more than most people realize."
**Fix:** Replace with the actual implication, the actual stake, the actual reason it matters. "If this migration fails, we lose 3 months of pipeline data" instead of "The stakes are high." If you can't name the specific consequence, delete the sentence.

---

## Quick Scan Checklist

When auditing content, scan in this order (most obvious tells first):

1. **Hard Tells** — Any single one flags the content
   - [ ] Throat-clearing intro (21)
   - [ ] "Great question" / false empathy (16, 17)
   - [ ] Paired synonyms (6)
   - [ ] Copula avoidance (7)
   - [ ] Superficial -ing tacking (9)
   - [ ] Vague attributions (10)
   - [ ] Template transitions (4)
   - [ ] Formulaic "challenges and future" (5)
   - [ ] Permission-seeking closer (20)
   - [ ] Hedge stacking (8)
   - [ ] Exclamation inflation (11)
   - [ ] "Comprehensive" promise (22)
   - [ ] Emoji as punctuation (13)
   - [ ] Caveat avalanche (19)
   - [ ] Generic positive conclusion (25)
   - [ ] Predictable paragraph structure (1)
   - [ ] False agency (31)
   - [ ] Vague declaratives (33)

2. **Soft Tells** — Flag when 3+ appear in the same piece
   - [ ] Symmetric lists (2)
   - [ ] Section uniformity (3)
   - [ ] Premature certainty (18)
   - [ ] Em-dash overuse (12)
   - [ ] Bold-keyword highlighting (14)
   - [ ] Title case in headings (15)
   - [ ] Redundant bridges (23)
   - [ ] Safety-net qualifier (24)
   - [ ] Rule of three overuse (26)
   - [ ] Negative parallelism (27)
   - [ ] Synonym cycling (28)
   - [ ] False ranges (29)
   - [ ] Colon-list dependency (30)
   - [ ] Narrator-from-a-distance (32)

3. **Vocabulary check** — Scan for 3+ high-frequency AI words in any single paragraph (see vocabulary list above)

---

## Speed Scan Checklist

A flat 11-item rapid-fire checklist for re-checking during final audit (Step 5). Covers the most common residual tells — patterns that survive initial stripping or get reintroduced during voice injection.

- [ ] Any sentence that sounds profound but says nothing specific? → Rewrite with facts
- [ ] "Full stop." / "Let that sink in." / "Make no mistake" → Delete
- [ ] Paragraph starting with "So" or "Look," → Delete the opener
- [ ] "Not X. Y." binary contrast used more than once → Keep the best, rewrite the rest
- [ ] Inanimate subject + human verb ("the data tells us") → Name the actor
- [ ] "The implications are significant" or similar vague declarative → Name the implication
- [ ] Three consecutive sentences within ±3 words of each other → Vary length
- [ ] Lazy extreme (always/never/everyone/nobody) without evidence → Scope or cite
- [ ] "Navigate," "unpack," "lean into," or "landscape" → Replace with plain equivalent
- [ ] -ing phrase tacked onto the end of a sentence → Delete and check if meaning survives
- [ ] Any sentence announcing what the text will do ("In this section...") → Delete
