---
name: easy-humanize
description: Write non-technical prose in English, Russian or other languages (chat/Telegram messages, emails, text documentation, reports, talks, posts, essays) without AI-writing tells. Use when asked to write or rewrite such text, or when the prompt says "humanize", "sound human", "no AI style", "без ИИ-стиля". Skip for code, configs, API/reference docs, logs, structured data.
---

# easy-humanize

Goal: text that reads like a specific person wrote it for a specific reader. Not "text that dodges a detector". Detectors are unreliable; do not optimize for them.

## Scope

Apply to: messages (Telegram, Slack, email), prose documentation, reports, speeches/talks, posts, essays, cover letters, product copy.
Do not apply to: code, comments, configs, API references, CLI help, changelogs, data formats, legal boilerplate where fixed wording is required.
If the user explicitly asks for humanized text, apply regardless of format.

## Process

1. Settle the facts first: who reads it, why, in what language and register, what concrete material exists (names, numbers, dates, events). If the material is thin, ask or write shorter. Never pad.
2. Draft in the reader's register, following the rules below.
3. Run the final check at the bottom. Fix hits by deleting or replacing with a concrete fact, not by swapping synonyms.
4. Deliver only the text. No preface, no "here is your humanized version", no offer to adjust.

## Rules

Patterns appear in clusters. A single hit is fine; several in one paragraph is the tell. Do not mechanically ban words, fix the cause.

**Content**
- Specifics over significance. Replace "played a pivotal role in the industry" with what the person or thing actually did. If you have no fact, cut the sentence.
- No symbolism or importance inflation: "stands as a testament to", "serves as a reminder", "leaves a lasting mark", "a key/turning moment". Ordinary things stay ordinary.
- No notability padding: do not list outlets that "covered" something, and do not name a source inline for trivial facts.
- No shallow analysis tacked on with -ing or "which" clauses ("highlighting", "underscoring", "reflecting", "contributing to"). Inanimate facts do not emphasize or underline anything; people do.
- No vague authority: "experts say", "industry reports show", "some critics argue". Name who, or drop the claim.
- No cutoff or sourcing disclaimers ("as of my last update", "limited information is available"). If you lack facts, say what is missing once, plainly, or ask.
- Never invent sources, quotes, links, ISBN/DOI, statistics. Strip tracking parameters such as `utm_source=openai` from any URL.

**Tone**
- Neutral and plain, not brochure language: avoid "rich", "vibrant", "diverse", "breathtaking", "nestled in the heart of", "boasts", "continues to captivate", "rich cultural heritage".
- No editorial hedges aimed at an imaginary reader: "it is important/worth noting", "keep in mind", "may vary". State the caveat itself if it matters.
- No chatbot voice inside the text: "Sure!", "Certainly", "Great question", "I hope this helps", "Let me know if you'd like...", "You're absolutely right".
- Do not announce the text ("In this article we will explore"). Start with the substance.

**Structure**
- No closing summary that restates the paragraph ("In conclusion", "Overall", "To sum up"). End when the content ends.
- No formula "Challenges" / "Future outlook" ending ("Despite its success, X faces challenges... continues to thrive").
- Do not define the topic as a term ("'X' refers to..."), and do not wrap the title in quotes as a definition.

**Sentences**
- Avoid "not only... but also", "it's not just about X, it's Y".
- Avoid triads by default (three adjectives, three short phrases). Use two or four, or one.
- Avoid merism "from X to Y" when X and Y are not a real scale.
- Do not rotate synonyms for a main subject ("the protagonist", "the key figure", "the leading character"). Repeat the name or use a pronoun.
- No chains of dangling participles ("Using this method, results improved"). Make the subject do the verb.
- Em dashes: at most one or two per page, prefer commas, colons, parentheses, or two sentences.
- Vary sentence length. Plain verbs ("is", "has", "uses") beat "serves as", "boasts", "features", "facilitates".

**Formatting**
- Match the medium. Telegram and chat: short plain paragraphs, no headers, no bullets unless the user lists things, no bold, at most the emoji the user would use.
- Documents: sentence-case headings, never Title Case On Every Word. Lists only for real lists. No bold on every key term. No "**Label:** text" bullet columns. No horizontal rules between sections.
- Do not leak Markdown into targets that do not render it (wikis, plain-text email, some messengers). If the target uses other markup (wikitext, BBCode), use that.
- No decorative emojis or arrows as bullets.

**Human texture**
- Take a position when the register allows (reports and personal messages do, encyclopedic text does not).
- Use concrete detail only from provided material or well-known fact. Do not invent anecdotes.
- Contractions and sentence fragments are fine in casual text. Do not add deliberate typos.
- Keep the user's own wording, jargon, and level of formality when they gave a sample.

## Language notes

The rules are language-independent. Write in the language of the user's request (or the one they ask for) and use that language's own tells as the watch list. English and Russian are covered below; for other languages, apply the same categories and look for the local equivalents.

**English tells**
- Significance: "plays a pivotal/key/vital role", "stands as a testament to", "serves as a reminder", "leaves an indelible mark", "underscores/highlights/showcases/reflects", "a rich tapestry", "evolving landscape", "ever-changing world".
- Promo: "vibrant", "rich cultural heritage", "nestled in the heart of", "boasts", "breathtaking", "continues to captivate", "must-visit", "game-changer", "delve into", "navigate the complexities".
- Hedges and didactics: "it's important/worth noting that", "it should be noted", "keep in mind", "may vary".
- Closers: "In conclusion", "Overall", "In summary", "Despite these challenges... the future looks bright".
- Chatbot voice: "Certainly!", "Great question!", "I hope this helps", "Feel free to reach out", "Let me know if you'd like me to expand".
- Structures: "not just X, it's Y", "not only X but also Y", "from X to Y" as a fake range, triads, "Whether you're A, B, or C".
- Disclaimers: "as of my last update", "based on the available information", "details are limited".

**Russian tells**
- Significance and promo: "играет ключевую/важную роль", "является свидетельством", "оставил неизгладимый след", "богатое культурное наследие", "в самом сердце", "яркий и разнообразный", "захватывающий", "в современном мире".
- Shallow analysis with an inanimate subject: "подчёркивает", "способствует", "демонстрирует", "отражает", "свидетельствует о".
- Hedges: "важно/стоит отметить", "необходимо учитывать", "значения могут варьироваться".
- Closers: "подводя итог", "в заключение", "в целом", "несмотря на трудности, ... продолжает развиваться".
- Chatbot voice: "Конечно!", "Безусловно", "Вы абсолютно правы", "Надеюсь, это поможет", "Сообщите, если нужно расширить".
- Structures: "не только..., но и", "это не просто..., это...", "от X до Y" без реальной шкалы, ряды из трёх однородных членов.
- Style: chains of деепричастные обороты with a lost subject ("используя этот метод, результаты улучшаются"), stacked отглагольные существительные and канцелярит. Prefer a verb and a concrete subject.

**Mixed-language requests**: reply in the language the user wrote their own words in, not the language of any pasted material. Do not translate stock phrases literally from one language into another; that produces its own tells.

## Register quick guide

- **Telegram/chat message**: 1 to 4 sentences, say the point first, no greeting ritual unless the user's style has one, no sign-off, no offer to follow up.
- **Text documentation**: direct instructions, concrete examples, one idea per paragraph, no marketing adjectives, no "overview" fluff.
- **Report / talk**: lead with the finding, then evidence; numbers and names over adjectives; for speech, shorter sentences and spoken rhythm.

## Final check (silent)

Before sending, scan for: significance words; "-ing" analysis tails; vague attribution; promotional adjectives; hedges like "important to note"; summary closer; "not only/just"; forced triads; synonym rotation; more than two em dashes; Title Case headings; bold overuse; chatbot phrases; invented or untracked-looking sources. Remove or replace each with a fact. If a sentence carries no fact after the fix, delete it.
