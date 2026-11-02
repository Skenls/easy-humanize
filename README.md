# easy-humanize

A harness-agnostic skill for AI agents. It makes the agent write non-technical text in English or Russian (and, by the same rules, other languages) without the usual AI tells. It is based on the Russian Wikipedia essay "Признаки сгенерированности текста" (signs of AI-generated text), generalized beyond Wikipedia and extended with English patterns.

It is a plain Markdown file with a short frontmatter. It works with any agent harness that can load instructions on demand: Claude Code, Codex CLI, Gemini CLI, Cursor, OpenCode, Aider, custom agent loops, and so on.

## What it does

When the agent is asked to write human-facing prose, it follows a compact rule set and runs a final self-check before answering:

- cuts significance inflation, promotional language, and empty "analysis" tails
- avoids chatbot phrases, disclaimers, summary closers, and "challenges / future outlook" formulas
- avoids "not only... but also", forced triads, synonym rotation, dangling participles, em dash spam
- matches formatting to the medium (plain text for Telegram, sentence-case headings for docs, no stray Markdown)
- never invents sources, links, or identifiers, and strips `utm_source` parameters
- keeps separate watch lists of English and Russian tells, and replies in the language the user wrote in

## When it triggers

- Messages: "write a Telegram message to...", emails, chat replies
- Text documentation, reports, talks, posts, essays
- Any prompt that says it explicitly: "humanize", "sound human", "no AI style", "без ИИ-стиля"

It does not trigger for code, configs, API/reference docs, logs, or structured data.

## Token cost

Only the `name` and `description` from the frontmatter need to be indexed by the harness (roughly 70 tokens). The full body should be loaded only when the skill is triggered, so there is no permanent cost.

## Install

The file is `easy-humanize.md`. Pick the option your harness supports:

1. **Harness with skills (folder + `SKILL.md`, frontmatter indexed, body lazy-loaded).** Create a folder named `easy-humanize` in the harness's skills directory and save the file inside as `SKILL.md`. Examples: `.claude/skills/easy-humanize/SKILL.md` (Claude Code), or the equivalent skills directory of your tool.
2. **Harness with custom commands/prompts.** Save it as a command file (for example `.claude/commands/easy-humanize.md`, or your tool's prompts directory) and call it by name when needed. Auto-triggering depends on the harness.
3. **Harness without lazy loading** (rules files like `AGENTS.md`, `.cursorrules`, a system prompt). Do not paste the whole body into the always-on file. Instead add one line there, for example:
   `For non-technical prose (messages, docs, reports, talks) or when asked to humanize, read easy-humanize.md first and follow it.`
   and keep the file somewhere the agent can read.
4. **Custom agent loop.** Index the frontmatter `description`, and inject the body into the context only when the model or a router decides the skill applies.

## Usage examples

- "Write a Telegram message to my landlord asking to move the payment date to the 10th"
- "Draft a short talk intro about our Q3 results. Humanize it"
- "Напиши доклад на 5 минут про наш релиз, без ИИ-стиля"
- "Rewrite this README section so it doesn't sound like AI"

## Notes and limits

- The rules come from observed patterns, not hard laws. A single marker is not proof of AI text, and the skill targets clusters, not individual words.
- Do not rely on AI detectors to judge the result. They are unreliable, and the aim is text that is specific and readable.
- The skill cannot add facts. If the request lacks concrete material, the agent should ask or write shorter instead of padding.
- English and Russian watch lists are included. For another language, the same rule categories apply; add that language's tells under "Language notes".

## Customizing

- Add personal style rules (preferred tone, banned phrases, signature phrases) under **Rules**.
- Add a sample of your own writing if you want the agent to imitate your voice.
- Keep the body short. Every added line is paid for in tokens on each trigger.
