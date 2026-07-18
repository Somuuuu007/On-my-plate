# On My Plate — Turn every meeting into per-person accountability

**Track:** No-Code · **Marketplace:** [On My Plate](https://app.joinsitrep.com/dashboard/marketplace/on-my-plate--d7111ee5-6503-4eac-9bc6-126935907840) · **Repo:** [GitHub](https://github.com/Somuuuu007/On-my-plate)

## The problem
Every team meeting ends the same way: a summary, a pile of "we should…", and a fuzzy sense of who is actually doing what. Days later someone asks "wait, who owned that?" — and the answer is nobody. The tasks with **no clear owner**, the person who is quietly **overloaded**, the decision everyone *thought* was made but wasn't — these are exactly what a plain summary hides, and exactly what causes work to slip.

## The solution
**On My Plate** is a SitRep agent that turns any meeting into a clear, **per-person accountability report** — so nothing falls through the cracks. It doesn't just summarize; it assigns, flags the gaps, and surfaces what still needs a decision.

For every meeting it produces:
- 👤 **Per-person tasks** — who owns what, by when
- ⚠️ **Needs an owner** — action items nobody picked up (the #1 dropped-ball source)
- 🔀 **Assigned outside the room** — work handed to people who weren't there
- ⛔ **Blocked** & ⚡ **Overloaded** — what's stuck, and who has too much on their plate
- ❓ **Open decisions** — what was left undecided
- 🗓️ **Next steps**

## Why it's different
Most meeting agents on the Marketplace are *summarizers* — follow-up emails, notes, slide outlines — and that space is saturated. On My Plate targets an unfilled gap: **accountability with gap-detection.** The standout feature is **"Needs an owner"** — it actively hunts for tasks nobody claimed instead of silently dropping them. That single behavior turns a passive summary into an active accountability tool.

## How it works
1. A meeting ends → SitRep captures the summary + attendees.
2. On My Plate (a **no-code prompt agent** — no server, no code) reads it.
3. It returns a clean Markdown report the whole team can scan in ~15 seconds.

## Engineering: making a lightweight model reliable
This is a no-code agent, so *the entire product is one system prompt*. The real challenge was making a lightweight model produce a **precise, structured, trustworthy** report every time:

- **Structured system prompt** — clearly separated sections (role, definitions, output format, counting rules, hard rules, edge cases, examples, self-check) the model can follow reliably.
- **Precise definitions** — we explicitly separate the concepts models blur: a *task without an owner* (→ Needs an owner) vs a *decision without an answer* (→ Open decisions); *unowned* ≠ *absent person*. Most errors came from blurring these; defining them fixed them.
- **Prompt-injection defense** — meeting summaries are untrusted input, so the agent treats all meeting content as **data, not instructions**, and ignores embedded commands like "ignore previous instructions."
- **Negative examples** — a "Common failures — never do these" section shows the model the exact mistakes to avoid (inventing an absent person, double-listing an item, treating the meeting title as a task), with reasoning.
- **Edge cases** — empty summaries, missing attendee lists, shared tasks, duplicate mentions, and absent-but-assigned people are all handled explicitly.
- **A final self-check** — before answering, the agent verifies its own output (counts match, nothing invented, no empty sections).

### Iterative, evidence-driven tuning
We didn't guess — we tested. We ran many realistic and adversarial meeting scenarios, watched where the lightweight model broke (phantom "(Absent)" people, miscounts, misclassified decisions, invented tasks), and fixed each **at the root** — through clearer definitions and examples rather than piling on brittle rules. The result stays accurate even on messy, real-world summaries.

## User experience
The output is deliberately **concise and scannable** — emoji-anchored sections, an "at a glance" line, per-person grouping. A busy manager gets the whole accountability picture in seconds, with zero setup.

## Who it's for
Any team that meets and then loses track: standups, sprint planning, client calls, cross-functional syncs. Managers get instant clarity on who owns what; teams get a shared source of truth; nobody can say "I didn't know it was mine."

## Links
- **Marketplace (install & use):** [On My Plate](https://app.joinsitrep.com/dashboard/marketplace/on-my-plate--d7111ee5-6503-4eac-9bc6-126935907840)
- **GitHub (MIT-licensed):** [repo](https://github.com/Somuuuu007/On-my-plate)

*Built for the SitRep AI Hackathon — No-Code track.*
