# On My Plate — Post-Meeting Accountability Agent

**Turn any meeting into a clear, per-person accountability report — so no task, owner, or deadline slips through the cracks.**

Built for the [SitRep AI Hackathon](https://www.joinsitrep.com/hackathon) · No-Code track.

## What it does
Most meeting tools just *summarize*. **On My Plate** goes further — after every meeting it produces a per-person accountability report:

- 👤 **Per-person tasks** — who owns what, by when
- ⚠️ **Needs an owner** — action items nobody picked up (so they don't get dropped)
- 🔀 **Assigned outside the room** — work given to people who weren't there
- ⛔ **Blocked** & ⚡ **Overloaded** — what's stuck, and who has too much on their plate
- ❓ **Open decisions** — what still needs a call

## How it works
1. Your meeting ends → SitRep captures the summary + attendees
2. On My Plate (a no-code prompt agent) reads it and builds the report
3. Your team instantly sees who owns what — nothing forgotten

No server and no code to run — SitRep runs the agent directly from the prompt.

## The agent
This is a **no-code (Managed) agent**: its entire behavior is defined by one carefully engineered system prompt — [`prompt.txt`](prompt.txt).

Prompt-design highlights:
- Precise definitions to prevent common errors (owner vs. decision, unowned vs. absent)
- Prompt-injection defense — meeting content is treated as data, never as instructions
- Robust edge-case handling + a final self-check pass
- Tuned to run reliably on a lightweight model

## Try it
Install from the SitRep Marketplace: **[On My Plate](MARKETPLACE_URL_HERE)**

## Repo contents
- `prompt.txt` — the agent's system prompt (this *is* the whole agent)
- `test-meetings.md`, `stress-tests.md` — test cases used to validate it

## License
[MIT](LICENSE)
