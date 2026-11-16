---
name: product-spec
description: Use when someone wants to write a product spec. Interviews them, researches outside rules and the codebase, and writes a spec with closed, testable acceptance criteria that an engineer or an AI agent can build from.
---

# Product spec

Turn a rough feature idea into a spec that an engineer or an AI agent can build from without guessing.

The test of a finished spec: every acceptance criterion can be answered yes or no, and no question is left for engineering to guess.

## Settings

Fill these in once, using the setup flow below. Anything marked "not set" means setup has not been run.

- **Specs live in:** not set
- **Work is tracked in:** not set
- **Decisions are discussed in:** not set
- **Codebase:** not set
- **Voice:** not set
- **Extra template sections:** none
- **Outside rules to check:** none

## Setup

Run setup when any setting above says "not set", or when the person asks to set up or change settings. Skip it otherwise.

Ask these one round at a time. Offer the listed choices, and accept any other answer.

1. **Where do your specs live?** Notion, Linear documents, Confluence, Google Docs, files in the code repository, or somewhere else.
2. **Where is work tracked?** Linear, Jira, Asana, GitHub Issues, or somewhere else.
3. **Where do decisions get discussed?** Slack, Microsoft Teams, email, or somewhere else.
4. **Is there a codebase to read?** A repository name, or none.
5. **House rules.** Whose voice the spec is written in (for example "plain, short sentences, we"). Any sections to add to the template. Any outside rules that usually apply, such as a regulator or a partner.

Then:

1. Check which of the named tools you can reach in this session.
2. For each one you cannot reach, say so by name and tell the person they can connect it in their own settings. Do not try to connect it yourself.
3. Say that the skill still works without them. The person pastes the brief or the thread instead.
4. Show the filled-in Settings block. Save it into the person's copy of this skill if you are able to. If not, ask them to paste it over the Settings section above.

Never block on setup. If the person wants a spec now, write it with what you have and run setup afterwards.

## How to write the spec

Work through these steps in order. Do not write the spec until step 4.

### 1. Gather what exists

Before asking anything, read what the person points to and look for more:

- Any decision page, brief or earlier spec they link.
- Related documents, issues and threads in the tools named in Settings, if you can reach them.
- The codebase, if there is one and you can reach it. Find where the feature touches today's code and note the files. This often shows things the brief missed.
- Outside rules. If a regulator, partner or provider sets a rule, look it up, quote the source and link it. Never state a rule from memory.

Tell the person in a few lines what you found, especially anything that conflicts with their brief.

If you cannot reach a tool, say which one and ask them to paste what matters.

### 2. Interview

Ask questions until you can write every section of the template.

- Ask in small rounds, three or four questions at a time. Use multiple-choice questions where you can, with a recommended option first.
- Each question must be a decision only the person can make. Do not ask what you can find out yourself.
- Push hardest on: edge cases, error states, what happens when a user leaves part-way, limits and thresholds, who pays, what is blocked and for how long, and what existing users see.
- When an answer conflicts with an earlier answer or with a source, say so and ask which is right.
- When the person says "not sure, you decide", pick the option that is cheapest to change later, and record it as an assumption.
- Stop asking when the remaining unknowns belong to someone else. Those become open tasks with an owner.

### 3. Check for gaps yourself

Before writing, list for yourself: every state a user can be in, every way each step can fail, and every number that needs a value. If any is unanswered, go back to step 2.

### 4. Write the spec

Use the template below, plus any extra sections named in Settings.

- Write in the voice named in Settings. If none is set, use plain, short sentences.
- Acceptance criteria must be closed. Each one is a single statement that a tester can mark yes or no. Prefer "Given X, when Y, then Z". Number them (AC-1.1, AC-1.2) so later documents can refer to them.
- Never write "should work", "properly", "as appropriate", "etc." or "and so on" in a criterion.
- Put a number on every limit, time and threshold. Say which ones are settings that can change without a release.
- State what is enforced on the server, what is stored and what is logged.
- Where a rule comes from outside, quote it and link the source.
- Where the code is relevant, name the files or areas a criterion touches.

### 5. List assumptions and open tasks

At the end of the spec:

- **Assumptions to confirm:** everything you decided without a clear answer. One line each, with the criterion it affects.
- **Open tasks before build:** everything that is not a product decision and is still unknown. Each has a named owner. Engineering must not guess these.

### 6. Critique it as the engineer

Re-read the spec as the engineer who has to build it. Look for:

- Criteria that contradict each other or the decisions list.
- States with no criterion.
- Anything an agent would have to guess.
- Criteria that cannot be tested as written.

Fix what you can. Report the rest to the person as questions.

### 7. Close the questions

Go through the assumptions and questions with the person, a few at a time, and update the spec after each answer. The spec is done when no open question is left with product.

### 8. File it

Save the spec in the place named in Settings. If you cannot reach it, give the person the finished spec to paste.

If you edit a spec that someone else may have changed, read the latest version first and change only what was asked.

## Spec template

```
# <Feature>: Product Spec

Draft <n>, <date>. Source: <link to decision or brief>.

## Goal
One or two sentences.

## User story
As a <user>, I want <thing>, so that <outcome>.

## Decisions made
Bullets. Each decision made in the interview.

## Scope
In scope: bullets.
Out of scope: bullets.

## Flow
Numbered steps for each main path. Add a flow diagram if there are branches.

## 1. <Part of the feature>
One or two lines on how it works today, with code references if known.
Acceptance criteria:
- AC-1.1 ...
- AC-1.2 ...

## 2. <Next part>
...

## Build rules
What is enforced on the server, what is stored, what is logged, what is a
setting, test switches for staging.

## Edge cases
Bullets. Each one says what happens.

## Open tasks before build
Numbered. Each has an owner. None is a product decision.

## External approvals
Who must approve what before launch.

## Dependencies
Other work, services or decisions this needs.

## Assumptions to confirm
Bullets, each with the criterion it affects.
```

## Closed and open criteria

Closed: "Given a user who enters the wrong password five times, when they try a sixth time within 15 minutes, then sign-in is refused and they see the time remaining."

Open: "Account lockout should work properly."

Closed: "Given a basket with an item that has sold out, when the user opens checkout, then the item is removed, the total is updated, and a message names the item."

Open: "Handle out-of-stock items gracefully."

## When the spec changes later

- If engineering finds a gap, the answer goes into the spec first. Other documents are updated to match.
- If a criterion needs to change, change it in the spec. Tickets copy from the spec, never the other way round.
- Bump the draft number and date on every change.
