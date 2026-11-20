# Product spec skill

A skill for Claude that turns a rough feature idea into a product spec an engineer or an AI agent can build from without guessing.

It interviews you, reads what already exists, and writes a spec where every acceptance criterion can be answered yes or no.

## Why

AI agents build what the spec says and nothing more. If a spec is vague, the agent guesses, and you spend your time fixing what it guessed. This skill puts the effort in up front.

## What it does

1. **Gathers what exists.** It reads the brief you point to, related documents and tickets, the codebase and the designs if it can reach them. It looks up outside rules and quotes the source.
2. **Interviews you.** Small rounds of questions. It pushes hardest on edge cases, error states, limits and what existing users see.
3. **Writes the spec** in a fixed template, with numbered, closed acceptance criteria.
4. **Lists what it assumed** and what is still open, with an owner for each.
5. **Critiques its own spec as the engineer** who has to build it, and brings you the gaps.

## Closed acceptance criteria

Closed means a tester can mark it yes or no.

- Closed: "Given a user who enters the wrong password five times, when they try a sixth time within 15 minutes, then sign-in is refused and they see the time remaining."
- Open: "Account lockout should work properly."

## Install

1. Download this repository, then zip the `product-spec` folder on its own.
2. In Claude, add it as a custom skill.
3. Start a chat and say "set up the product spec skill".

In Claude Code, copy the `product-spec` folder into your skills folder.

## Setup

The first time you use it, the skill asks six questions:

1. Where do your specs live? (Notion, Linear, Confluence, Google Docs, the code repository)
2. Where is work tracked? (Linear, Jira, monday.com, Asana, GitHub Issues)
3. Where do decisions get discussed? (Slack, Microsoft Teams, email)
4. Is there a codebase to read? (GitHub)
5. Where are your designs? (Figma)
6. Any house rules: voice, extra template sections, outside rules to check.

It then checks which of those tools are connected and tells you which ones are missing. You connect tools in your own Claude settings. The skill cannot do that for you.

The answers are saved in the Settings section at the top of `SKILL.md`. To change one later, edit that section or run setup again. A team that wants everyone on the same settings can commit a filled-in copy to a shared repository.

It works with nothing connected. You paste the brief and it writes the spec back to you.

## Use

Say what you want to build:

> Write a spec for letting users export their transactions as a CSV.

Or point it at a decision or a brief:

> Use the product spec skill on this decision page: <link>

## How we use it

The spec is stage one of three:

1. **Product spec.** Product writes it with this skill.
2. **Feasibility document.** Engineering's agents answer the spec: how each acceptance criterion will be met, the risks, and any gaps in the spec. Gaps go back to product and the spec is fixed first.
3. **Epics and issues.** The work is broken down, with acceptance criteria copied word for word from the spec.

Every ticket traces back to a criterion in the spec.

## Licence

MIT. See `LICENSE` in the repository root.
