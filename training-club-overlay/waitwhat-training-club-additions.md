# Training Club `waitwhat` Additions

> Layered on top of the Personal kit's `waitwhat` SKILL.md. The Personal skill does
> all the real work — this file only pins down the vocabulary and the failure modes
> that are specific to a Training Club operator. AI reads this file when `/waitwhat`
> fires on a Training Club install.

---

## How to use this file

When `/waitwhat` fires on a Training Club install, the AI:

1. Reads the Personal kit's `waitwhat` SKILL.md as baseline — the re-pitch method,
   the "re-explain don't re-shorten" rule, the double-fire escalation
2. Applies the vocabulary and failure modes below
3. Delivers the re-pitch

Nothing here replaces the Personal skill. If this file is missing, the Personal
skill still works correctly on its own.

---

## Why this fires more often on a Training Club install

[PARTNER_NAME] runs a Training Club. They are an expert in coaching, programming,
retention, and their members — and they are **not** a developer. The Personal kit
assumes some tolerance for technical language. This install should assume none.

Two rules from the Personal skill matter more here than anywhere else:

- **Define or drop** — apply this ruthlessly. If a word came from software and not
  from the gym floor, it needs a plain-English swap or a same-sentence definition.
- **Concrete beats abstract** — anchor to *their* club. Their members, their race
  dates, their actual files. Not "your data" — "the 40 members in your Members
  folder."

## Vocabulary — theirs, not software's

Mirror the operator's language. When a technical concept has a Training Club
equivalent, use the equivalent.

| Don't say | Say |
|---|---|
| gym | **Training Club** |
| users, customers, records | **members** |
| workflow, pipeline, process | **the way you run [X]**, or name it: programming, check-ins, onboarding |
| training plan, mesocycle | **block** |
| database, dataset, records | **your member files** |
| trigger, fires, invokes | **runs when**, **happens when** |
| deploy, provision, configure | **set up**, **switch on** |
| API, endpoint, integration | **the connection to [tool name]** — name the actual tool |
| agent, model, LLM | **your AI**, or its name |
| repository, directory, path | **folder**, and give the plain location |

## Anchors that land

When explaining anything abstract, reach for these first — they're already real to
a Training Club operator:

- **A member at risk of leaving** — the clearest stakes there are
- **The next race on the calendar** — dates make timelines concrete
- **A block they're currently programming** — a real thing with real weeks in it
- **A message they'd send a member** — makes "draft," "tone," and "voice" tangible
- **A Saturday morning class** — makes scheduling and timing concrete

## The failure mode specific to this install

The most likely confusion isn't a hard concept — it's [AI_NAME] describing **what
it did** in software terms when [PARTNER_NAME] wanted to know **what changed for
their club.**

> ❌ "I've configured the retention review to run on a weekly schedule and it'll
> surface amber and red members based on attendance decay."
>
> ✅ "Every Monday morning I'll check who's drifting — members who've quietly
> stopped showing up as often. You'll get a short list with names, so you can
> reach out before they cancel."

Same fact. The second one tells them what happens on their Monday.

When `/waitwhat` fires, this is the most probable thing to fix: re-pitch from the
operator's side of the desk, not the machine's.

## If it fires twice on the same thing

Follow the Personal skill's escalation, and add one Training Club-specific move:
**offer to show it instead of explain it.** Run the thing once on one real member
or one real block, and narrate what happened. For an operator, one worked example
beats any third explanation.
