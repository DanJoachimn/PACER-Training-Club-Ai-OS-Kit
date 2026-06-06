---
name: pacer-install-mentor
description: Companion skill to PACER kick-off. Fires at the end of each install phase to give the owner a 3-line "what just happened / why it matters / when you'd use it" explanation. Non-developer language. Zero quizzes, zero questions, zero friction. Read or skip. Born from Dani's own experience — feeling "ok, Hyperframes and genmedia and ObsidianVault and all this, but what's the value prop?" when looking at any new install. Turns the install moment into the tutorial without making the owner do homework. Triggered automatically at every phase boundary in PACER kick-off, OR manually with "explain what we just installed" / "what did that do".
---

# pacer-install-mentor

## Purpose

Charlie Warren (YC): *"The humans in the loop also need to enjoy the software. They are your users."*

The PACER kick-off installs the kit. It does not, today, tell the owner what they just got and why they should care. The result: a non-developer HTC owner ends a kick-off session with a working install they can't explain to themselves, let alone to a coach. They become dependent on Dani for understanding, which means they become dependent on Dani for support.

This skill closes that gap without adding friction. At the end of each install phase, the owner gets a tight three-line block:

1. **What just happened** — plain English, what got wired
2. **Why this matters for you** — value prop, anchored in their specific context (their gym, their members, their coaching style)
3. **You'll use this when** — one or two concrete situations where they'll touch this feature

That's it. No quiz. No "do you understand?" beat. No "click here to continue." The owner reads or skips. Either way, the install advances.

If they read, they leave the kick-off able to explain PACER to a coach. If they skip, they still have the working install. The skill is invisible upside.

## When to Use

**Automatic triggers:** PACER kick-off invokes this skill at every phase boundary. No human decision required.

**Manual triggers:**
- "Explain what we just installed"
- "What did that do?"
- "Value prop on [feature]"
- "Why do I have this?"
- Any time the owner pauses or looks confused

**Do NOT use when:**
- The owner explicitly says "skip the explanation" or "just install it"
- Mid-phase (during the actual install work) — only at phase boundaries
- For features the owner is already an expert on — surface check first

## The mentor pattern

For each install phase, produce a block in this EXACT shape:

```markdown
### 🛠 What just happened
{One sentence. Plain English. No jargon. What got wired or set up. Avoid "we configured the webhook" — use "your gym's lead form now pings PACER the second someone fills it out."}

### ⚡ Why this matters for you
{One sentence. Anchored in their specific gym context. Use the brand voice doc + the kick-off interview answers to make this personal. Avoid "this improves lead response time" — use "the next lead who fills out your form on Tuesday at 9pm gets a personal reply from PACER in 90 seconds — you stop losing leads to the gym down the road that answered faster."}

### 🌒 You'll use this when
- {Concrete use case 1 — a moment in their actual week when this feature lights up}
- {Concrete use case 2 — a second, different moment, ideally one they didn't expect}
```

Three sections. Three sentences (plus the bullet list, max two bullets). Total reading time: 15 seconds.

## Quality bar per section

### "What just happened"

- **Plain English.** Non-developer. If a 60-year-old HTC owner who's never used a webhook reads this, they understand it.
- **Specific.** Don't say "we set up the lead system." Say "your contact form now sends every new lead straight to PACER's inbox."
- **Visual when possible.** Use mental imagery the owner can picture. "Pings", "fires", "watches", "wakes up" — concrete verbs.
- **Past tense.** This is the recap of what just happened, not what will happen.

### "Why this matters for you"

- **Personalized.** Reference the owner's specific gym name, their member count, their location, their pain point if known.
- **Anchored in their pain.** From the kick-off interview, you know what they complained about. Tie this feature to that.
- **One concrete benefit.** Not "improved response times and better member engagement and..." — pick ONE clear benefit and land it.
- **Mode 2 voice.** No corporate filler. No "leverage", no "synergize", no "robust." Talk like a friend who runs another gym down the street.

### "You'll use this when"

- **Real moments.** Anchor each use case to a specific weekly moment they'll recognize. "Tuesday at 9pm when a lead form comes in while you're coaching the evening class."
- **One expected, one unexpected.** First bullet = the obvious use case. Second bullet = a use case they didn't realize this feature covered. The second one is the dopamine hit.
- **Max two bullets.** Don't pad.

## The phase-by-phase template

For PACER's standard install phases, here are pre-drafted mentor blocks. Tune at install time using the owner's specific context.

### Phase: Brand voice extraction completed

```
### 🛠 What just happened
PACER spent the last 20 minutes learning how you talk — your gym's voice, the phrases your members hear from you, the tone you use when something matters. It saved that as PACER's writing voice.

### ⚡ Why this matters for you
Every email, social caption, and member message PACER ever drafts will sound like you wrote it — not like ChatGPT wrote it. Your members can't tell the difference. They just feel like they're hearing from {GymName}.

### 🌒 You'll use this when
- A new member needs a welcome email and you're coaching back-to-back classes — PACER drafts it in your voice in 30 seconds
- Three months from now, when a new coach joins and you want their member emails to sound like yours — PACER's voice is the reference
```

### Phase: Wodify webhook wired

```
### 🛠 What just happened
Your lead form is now wired directly to PACER. The second someone fills it out, PACER knows — even if you're holding a wall ball.

### ⚡ Why this matters for you
The gym down the road takes 47 hours to answer a lead. PACER answers in 90 seconds, in your voice, with three qualifying questions. Three times more of those leads will book a trial. Math: 20 leads/month × 3× close rate × your trial-to-member conversion = real revenue you used to lose by being mid-class.

### 🌒 You'll use this when
- Saturday morning, three leads come in while you're running the 9am class — by the time you check your phone after, all three have replied to PACER and one's already booked
- The Tuesday-night DM you would have missed because you were coaching, eating dinner, and putting your kid to bed
```

### Phase: Member onboarding sequence installed

```
### 🛠 What just happened
The five-email sequence for every new member is now running on autopilot — Day 0 welcome, Day 2 PFT booking, Day 7 check-in, Day 14 community invite, Day 30 race nudge.

### ⚡ Why this matters for you
The 27-percentage-point retention gap between gyms with full onboarding (87% at 6 months) and gyms without (60%) closes for you starting now. Every new member gets the same world-class first 30 days regardless of how busy your week is.

### 🌒 You'll use this when
- The new member who signs up Friday and you completely forget about until Tuesday — PACER welcomed them on Friday, scheduled their PFT on Sunday, and checked in this morning
- The day you wake up sick and can't do anything — your members signing up that day get the exact same onboarding experience as any other day
```

### Phase: Telegram bridge connected

```
### 🛠 What just happened
PACER now lives in your Telegram. You can text or send a voice note from anywhere — between classes, on the school run, in bed at 11pm — and PACER hears you.

### ⚡ Why this matters for you
You don't need to open a laptop to use PACER. The thoughts you have walking from your car to the gym become commands PACER can act on. The window of "time when you could think but couldn't act" closes.

### 🌒 You'll use this when
- 6:15am walking into the gym, voice-noting "remind me to follow up with Sarah about her PFT booking" — PACER queues it and pings you at 11am when you have laptop time
- 9pm on the couch, "draft a member spotlight on James for this week" — by morning, three caption variants are waiting
```

### Phase: First custom skill enabled

```
### 🛠 What just happened
PACER's first add-on for your gym is live. Just like apps on your phone — the base PACER works for any HTC, but this skill is specifically wired for {GymName} based on what you told us today.

### ⚡ Why this matters for you
PACER gets stronger every time we ship a new skill — and the skills we build land on your install for free. Most gym software is what you bought on day one. PACER is what it grows into.

### 🌒 You'll use this when
- Next month, when we ship the Race Countdown Calendar — it shows up on your install automatically, ready to use for your March HYROX
- Six months from now, when you can't remember what life was like without it
```

## Format constraints

- **15 seconds to read max.** If it's longer, cut.
- **No headings beyond the three section markers.** No `####` subsections. No bullet lists inside the "What just happened" or "Why this matters" sections.
- **Bold sparingly.** Maybe one bold phrase per block, and only if it does real work.
- **Light emoji at section starts is fine** (🛠 ⚡ 🌒 are the defaults). Don't carpet-bomb the body.
- **No questions.** Period. Not "make sense?" — not "any questions?" — not anything that asks the owner to do work.
- **No "click here to continue."** The next phase just starts. The mentor block is fire-and-forget.

## What this skill is NOT

- **Not a quiz.** No verification, no "did you understand?" The owner is an adult. Trust them.
- **Not documentation.** Documentation is searchable, deep, complete. This is the just-in-time micro-explanation. The full docs live elsewhere.
- **Not a tutorial.** A tutorial says "now click here, now click here." This says "here's what happened, here's why you care." Past tense, not imperative.
- **Not for re-installs or upgrades.** When a new skill ships to an existing install, that's the building-brief's job, not the install-mentor's.

## Hybrid Rule compliance

- Reads: brand voice doc, kick-off interview answers (from same session)
- Writes: nothing persistent. The mentor block is output to the owner's terminal/Claude Code session in-line during kick-off. If the owner wants a written record, save to `~/Desktop/{owner-name}/PACER install notes.md` (outside their vault, theirs to own).
- Never writes to: vault `Notes/`, `_context/`, Projects body, daily-log dividers (not Dani's vault, but same rule applies if the owner has an Obsidian setup)

## Self-annealing notes

- If owners consistently ask follow-up questions about a specific phase, that phase's mentor block is failing — tune it up.
- If owners explicitly skip the block ("just install it"), that's data: they want even less. Track and shorten.
- If owners ask "wait, what was that thing?" 30 minutes after a phase, the use-cases weren't sticky enough — punch them up.
- Default-tune toward fewer words, not more.

## Companion skills

- **PACER kick-off** — the parent skill. install-mentor fires at its phase boundaries.
- **anti-ai-writing** — every mentor block runs through these rules before output. Voice consistency matters even more here than elsewhere because the owner is forming their first impression.
- **claumedian** — optional. A drop of humor in the "you'll use this when" bullets can land beautifully (the unexpected use case is a natural humor moment). Don't force it.

## First real test

When Dani runs PACER kick-off for the SHC pilot (or whichever HTC is install #1), have install-mentor fire at each phase boundary. After the install, ask the owner one question only: "If you had to explain PACER to one of your coaches tomorrow, could you?" If yes, the skill is earning its keep. If no, tune.
