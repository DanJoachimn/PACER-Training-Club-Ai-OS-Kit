# INSTALL-PART-2.md — Training Club Part 2 (Reach) install playbook

> **This file is read by an AI agent when the user says "run Part 2" or "continue install" after completing Training Club Part 1.** Days, weeks, or months after Part 1 — doesn't matter. The kit's already in place; this playbook deepens it.

---

## When this fires

User says any of:
- "run Part 2"
- "continue install"
- "let's do Part 2"
- "deepen the setup"
- "more setup"
- "expand my partner"
- "finish the Training Club kick-off"

OR: the AI offers it after the user has been using Part 1 for a few days and seems ready for more (proactive opportunity-spotting moment).

---

## Stage 0 — Greeting + check Part 1 is in place (~30 sec)

```bash
test -f ~/Documents/[AI_NAME]/.training-club-part-1-complete \
  || { echo "Training Club Part 1 not complete; redirect to INSTALL.md"; exit 1; }
```

If Part 1 isn't done → tell user, route them to `INSTALL.md` first.

If done → continue:

> "Good to see you back. Part 2 is where I learn your club deeper. Here's what we'll do (~30 min, ~30 messages, fits comfortably in one Pro session):
>
> 1. **5-question voice interview** — sharper voice profile than Part 1's lightweight one (~10 min)
> 2. **Training Club deep kick-off (Section C+)** — programming defaults, race calendar, member archetypes, your scaling philosophy (~10 min)
> 3. **ElevenLabs upgrade** — premium voices if you want them (~5 min, optional)
> 4. **Granola meeting capture** — auto-record + transcribe member calls + coach syncs (~5 min, optional)
> 5. **Optional skills** — content pipeline, document transformations, others (~varies)
> 6. **Siri & Apple Watch** — last because it's least essential (~10 min, optional)
>
> Ready to start with the voice interview, or want to pick a different stage to go to first?"

---

## Stage 1 — 5-question voice interview (~10 min)

Invoke the kick-off skill's **B-Express** path directly. The skill's flag-aware logic detects `.voice-foundation-3q-complete` exists and offers Express (5-Q) as the upgrade.

```bash
# Skill reads .voice-foundation-3q-complete → routes to "upgrade from 3-Q to 5-Q" framing.
# Run the 5 questions from Section B-Express (B1-B5).
```

The questions are the same as Personal Part 2's voice interview, with one Training Club-flavored variant for B4:

- **B1.** One-line principle — *"If [CLUB_NAME] were a person walking into a room, what's the energy? One sentence."*
- **B2.** Target member — *"Tell me about the actual person who walks into [CLUB_NAME] for the first time. Where do they shop? What do they aspire to? What do they fear about a HYROX-style class?"*
- **B3.** Reference brands — *"Three brands — fitness or anywhere — whose copy you'd genuinely admire."*
- **B4.** Other Training Clubs whose tone is wrong for yours — *"Two Training Clubs or fitness brands whose tone GRATES on you. What's specifically wrong?"*
- **B5.** Banned words / tropes — *"Words, phrases, or patterns that — if I ever wrote them in a draft for [CLUB_NAME] — would make you reject the whole draft."*

Capture answers verbatim. Write to:
- `~/Documents/[AI_NAME]/vault/Brand/Voice guide.md` (overwrite Part 1's 3-Q version)
- `~/Documents/[AI_NAME]/vault/Brand/Reference brands.md`
- `~/Documents/[AI_NAME]/vault/Brand/Do-not-use list.md`

Mark complete:

```bash
touch ~/Documents/[AI_NAME]/.voice-express-complete
```

---

## Stage 2 — Training Club deep kick-off (Section C+, ~10 min)

Read the Training Club kick-off additions for the deeper variants:

```bash
cat "$HOME/Documents/[AI_NAME]/.training-club-overlay/training-club-overlay/kick-off-training-club-additions.md"
```

That file contains the Training Club-flavored Section C+ — four buckets, ~2-3 min each:

- **C+1. Coaches + Members** — name your team and the 3-5 members the AI should know about by name + status. Creates files in `Coaches/[name].md` and `Members/[name].md`.
- **C+2. Programming defaults** — your default block length, scaling philosophy, benchmark cadence. Updates `vault/Programming/README.md` + `scaling-library.md` with operator-specific overrides.
- **C+3. Race calendar** — the 1-3 HYROX races per year that are "ours" (local, traveled to, content-anchored). Updates `vault/Events/race-calendar.md`.
- **C+4. Member archetypes** — the 2-3 archetype patterns at the club ("The Returner," "The First-Racer," etc.) so member-checkin-draft pulls archetype-aware tone. Updates `vault/_context/ideal-member-profile.md`.

Each bucket: ask the questions in the kick-off-additions file, capture answers, draft the file content, **show as a code block in chat** and ask *"save it or review and paste?"* (Hybrid Rule — `_context/` writes are user-gated).

Mark complete:

```bash
rm -f ~/Documents/[AI_NAME]/.training-club-kick-off-cplus-pending
touch ~/Documents/[AI_NAME]/.training-club-kick-off-cplus-complete
```

---

## Stage 3 — ElevenLabs upgrade (optional, ~5 min)

> "You've been using Mac's built-in voices since Part 1. ElevenLabs offers premium voices — more natural, more personality. Free tier covers ~10K characters per month at no cost. Want to set it up?
>
> If yes: I'll walk you through making a free account at elevenlabs.io, getting an API key, and pasting it into your config. ~5 min.
>
> If skip: stay on Mac voices. They work fine; this is purely a quality upgrade."

If yes — follow the same flow as Personal `INSTALL-PART-2.md` Stage 2 (open https://elevenlabs.io, walk through signup, clipboard-transfer API key, test).

Mark complete:

```bash
touch ~/Documents/[AI_NAME]/.elevenlabs-configured
```

---

## Stage 4 — Granola meeting capture (optional, ~5 min)

Especially valuable for Training Club operators: coaching calls, member onboarding calls, sales calls, internal coach syncs all auto-captured.

Same flow as Personal `INSTALL-PART-2.md` Stage 3:

1. User downloads Granola from granola.ai (if not already installed)
2. Grant microphone + system audio permissions
3. AI installs the `granola-sync` skill (already in `~/.claude/skills/` from Part 1)
4. Configure `granola-sync/scripts/config.py` with user's vault path + tag rules — recommend tagging by member name + by class type
5. Test sync — manual run produces files in `vault/Meeting Notes/`
6. Schedule via launchd (12:30 + 17:00 daily)

Mark complete:

```bash
touch ~/Documents/[AI_NAME]/.granola-configured
```

---

## Stage 4.5 — Obsidian Web Clipper (browser → vault, ~3 min)

Vault feeder #2 for the Training Club operator. Granola pumps coaching calls + member onboarding meetings into the vault automatically. The Obsidian Web Clipper pumps the open web — competitor blogs, race recap articles, programming research, retention industry pieces, anything readable in a browser — into the vault as clean markdown, in one click.

Combined with the AI's vault-awareness, *"summarize what I've clipped this week"*, *"find the article I clipped about hybrid programming"*, *"pull the strongest retention arguments from my last 3 clippings"* all just work — no copy-pasting.

> "Want to add the Obsidian Web Clipper? It's the cleanest way to feed articles, transcripts, and pages from the open web straight into your vault. ~3 min to install. Especially useful for Training Club operators tracking competitor content, race coverage, and programming research."

If yes:

1. Open Chrome (or Edge / Firefox / Safari) → install the **Obsidian Web Clipper** extension from the browser's store. Direct link: https://obsidian.md/clipper
2. Click the extension icon → point at the vault at `~/Documents/[AI_NAME]/vault/`.
3. Recommend `vault/Clippings/` as the destination folder (Web Clipper creates it if missing). Matches the Hab schema convention for raw source material.
4. Pick the default template — bundled "Default" handles most cases. YouTube template is useful for race recap videos.
5. Test: open any article in the browser, click the Web Clipper icon, save. Confirm a new markdown file appears in `~/Documents/[AI_NAME]/vault/Clippings/`.

Mark complete:

```bash
touch ~/Documents/[AI_NAME]/.obsidian-clipper-configured
```

After install: the AI reads everything in `vault/Clippings/` as context. Operator clips race recaps + competitor content + retention research, AI absorbs it, queries spanning "what's in my head + what I've been reading + what my clients are doing" become trivial.

---

## Stage 5 — Optional skills menu (varies)

### Optional skills

Training Club-relevant optional skills the user can install now or anytime later:

> "These are skills you can install now or anytime later. Each is independent. Tell me which interest you and I'll install just those — or say 'skip' and we move on.
>
> - **Content pipeline** — multi-stage content production (research → draft → quality → distribute). For Training Clubs publishing newsletter / longer-form regularly (~10 min).
> - **Document transformations** — mines meeting transcripts for case-study material — *'mine my coaching calls this month for testimonial-grade member quotes.'* Pairs with Granola (~5 min).
> - **Hyperframes** — animated explainer videos by conversation. Class promos, race recaps, member spotlights (~5 min).
> - **Video Use** — cut filler words + dead air from recordings. For coach-led IG Reels, member testimonials (~5 min).
> - **Book mirror** — turns books you've read (via Readwise highlights) into chapter-by-chapter synthesis docs. Programming, coaching, retention books (~5 min)."

Install only what user picks.

### Optional MCP server additions

MCPs are different from skills — they're external servers that expose tools to the AI. One MCP server, one capability. Installed via Claude Code Settings → MCP servers → Add new → paste the server's command from its README.

> "Worth considering at this stage:
>
> - **youtube-transcript MCP** — fetches transcripts from any YouTube video by URL. Lets the AI summarize a race recap video, pull quotes from a HYROX athlete interview, transcribe a programming methodology video, or fact-check claims — without copy-paste. Pairs nicely with the Obsidian Web Clipper (clip the YouTube page, fetch the transcript, ask for a synthesis). ~3 min to install. Search the Anthropic MCP registry or upstream for the current canonical package."

If the operator adds youtube-transcript MCP, verify it works with a Training Club-relevant test:

```
Test query: "Pull the transcript of this race recap: https://www.youtube.com/watch?v=<id>"
```

The AI should return the full transcript text. If it scrapes successfully, mark complete:

```bash
touch ~/Documents/[AI_NAME]/.youtube-transcript-mcp-configured
```

---

## Stage 6 — Siri & Apple Watch (EXPERIMENTAL — untested by kit author, ~10 min, LAST)

🚧 **Honest disclosure up front:** this stage has **not been verified by the kit author**.

- The **Siri path** is based on Apple's documented Shortcuts patterns. Reads like it should work but hasn't been tested end-to-end on a real install yet. Scheduled for first real verification soon.
- The **Apple Watch path** is fully untested. The kit author does not own an Apple Watch. The instructions are extrapolated from Apple's documentation, not from a working install.

If a Training Club operator tries this, they're beta-testing. Capture anything that breaks.

### Tell the operator this — once, plainly

> "Last optional step, and I want to be straight with you: this one is experimental. The Siri integration looks like it should work based on how Apple's Shortcuts framework is designed, but I haven't tested it end-to-end yet on a real install. The Apple Watch piece is even less verified — the kit's author doesn't own a Watch, so those instructions are based on Apple's docs, not on a working setup.
>
> If you want to try it, great — you're beta-testing. The use case is real (hands-free voice query from your watch while you're between classes — *'Hey [AI_NAME], who do I check in on today?'*), but I can't promise it works yet. If something breaks, tell me what you saw and we'll feed it back to the kit. If you'd rather skip until this is verified, totally fine — everything else in your install works without it."

If operator wants to try → walk through Personal `guides/09-siri-apple-watch-integration.md`. Pause at every step. If anything fails, **log it and stop** — don't improvise workarounds.

If operator skips → mark deferred:

```bash
touch ~/Documents/[AI_NAME]/.siri-deferred-until-verified
```

If operator successfully completes the setup (rare until first verified install lands):

```bash
touch ~/Documents/[AI_NAME]/.siri-configured
echo "$(date -Iseconds) — Siri configured (UNVERIFIED PATH, operator is first-mover)" >> ~/Documents/[AI_NAME]/logs/install.log
```

### Kit author's commitment

Siri path scheduled for verification by kit author "soon" (commit date 2026-05-18). Once verified, this stage gets downgraded from EXPERIMENTAL to "tested on macOS X / iOS Y." The Watch path stays EXPERIMENTAL until someone with a Watch contributes a verified walkthrough.

### Hard rules for this stage

- **Never present this stage as a "feature" the operator is getting.** It's an experiment they're opting into.
- **Never claim "Apple Watch hands-free" works.** Frame as theoretical.
- **If something fails, stop and log.** No improvised workarounds.
- **Capture friction in detail** — first real test of an untested stage = highest-value friction log entry possible.

---

## Stage 7 — Part 2 close

```bash
touch ~/Documents/[AI_NAME]/.part-2-complete
touch ~/Documents/[AI_NAME]/.training-club-part-2-complete
date -Iseconds > ~/Documents/[AI_NAME]/.part-2-date
echo "$(date -Iseconds) — TRAINING CLUB PART 2 COMPLETE" >> ~/Documents/[AI_NAME]/logs/install.log
```

Close with:

> "Part 2 done. Now I really know your club.
>
> **What you have now (beyond Part 1):**
> - A 5-question voice profile — drafts land closer to how you'd actually write
> - Deep Training Club context — coaches by name, key members by status, programming defaults, race calendar, member archetypes
> - Premium voice replies (if you upgraded to ElevenLabs)
> - Meeting auto-capture (if you wired Granola) — every coaching call captured within hours
> - The optional skills you added
> - Siri & Apple Watch (if you set them up)
>
> **What this means for you:**
> - `member-checkin-draft` now writes in archetype-aware tone, not generic
> - `block-builder` knows your default block length, scaling philosophy, and race calendar
> - `weekly-retention-review` understands which coaches own which member relationships
> - Drafts compound week over week — the learnings loop is running
>
> **Example use cases now possible:**
> - *'Mine my coaching calls this week for testimonial-grade member moments.'*
> - *'What's the pattern in what my Returner-archetype members keep asking?'*
> - *'Build me an 8-week block ending at HYROX Copenhagen, scaled to my Sunday class average.'*
> - *'Hey Siri, [AI_NAME] — draft a follow-up for the trial members from this week.'*
>
> **What's next:** the kit gets better over time. Run `/update` to pull new skills as they ship. The 100-question deluxe voice interview is still on the table — that's a separate 90-min sitting, best done a few weeks in when you've watched the AI draft enough to know what's still off."

---

## What's still in your back pocket after Training Club Part 2

| Skill / Feature | When to invoke |
|---|---|
| 100-Q deluxe voice interview | When you've used the AI for a few weeks and want maximum voice fidelity. Separate 90-min session. |
| New skills shipping via `/update` | The kit gets new skills over time. `/update` pulls them. |
| LLM Council | *"council this"* / *"pressure-test this"* for any locked decision with real stakes — locking pricing, deciding to expand to a second location, hiring a head coach, etc. |
| Promote member files | As members come and go, add new files in `Members/` and archive the inactive ones to `Archive/`. |

---

*Part 2 of 2 — Reach (Training Clubs). Part 1 (Foundation) is the prerequisite — see INSTALL.md.*
