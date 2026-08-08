# CloneVoice + VideoExpress Narrative Video Workflow

Integrate [CloneVoice.ai](https://www.clonevoice.ai) and [VideoExpress.ai](https://www.videoexpress.ai) together to create **full-length animated 2D narrative videos with 100% automation** — a perfectly matching AI narration voice, and animated video that syncs to that voice, scene by scene.

Your AI agent (Claude, ChatGPT, or Codex) drives VideoExpress in your browser: it writes and fact-checks the script, splits it sentence by sentence, generates every animated scene **against that sentence's own narration audio** through the built-in CloneVoice.ai integration, and assembles the finished video where every visual lands at the correct moment — because every clip is rendered in sync with its own line of narration.

## One deterministic path — by design

This prompt gives the agent **exactly one way** to do every step. No alternatives, no "preferred" routes, no fallbacks a lazy model can take. The workflow is a fixed gate sequence:

1. **GATE 0** — Verify the CloneVoice API key on both sides before anything is generated.
2. **GATE 1** — Research, script, and a **frozen chunk table**: one sentence per row, 120 characters max (the hard cap enforced by the app), declared before any audio exists.
3. **GATE 2** — Character references generated first and saved to My AI Images, then reused in every scene via Consistent Character mode.
4. **GATE 3** — The per-scene loop: still image → narration audio for that one sentence (CloneVoice voice, inside the Create Narration Video dialog) → narration-synced clip. One row, one clip. A proof scene runs first.
5. **GATE 3.5** — Every clip collected, previewed, and accepted.
6. **GATE 4** — All clips assembled in story order. No separate narration track — the clips carry their own audio.
7. **GATE 5** — Completion requires an evidence table: N table rows = N distinct clips on the timeline, durations summing to the export. The agent cannot call the job done early.

## The non-terminal execution contract — no stalls, no half-finished runs

Some agents (observed live on ChatGPT) hit a browser hiccup mid-production — a lost tab, a dead modal, a queued render — decide they're stuck, and end the run with "I generated some scenes; you can continue from here." The prompt's **Section 0.1** makes that decision explicitly illegal:

- The run has exactly **two legal endings**: verified completion (all N clips accepted, on the timeline in order, exported, downloaded, and the file watched) or a verified hard blocker from a **closed seven-item list** (login/security, the API-key fix, an unauthorized purchase, an explicit insufficient-credits message, a platform still down after the full recovery procedure has run twice, an irreversible public action, or you telling it to stop) — each requiring visible on-screen evidence.
- Everything else — stale tabs, dead modals, failed selectors, queued renders, restarted sessions — is a defined **recoverable state** routed through one recovery loop: reacquire the live tab, reconcile the media library against the production ledger, reopen the generator, and resume at the first unfinished row. Waiting is done by visible polling every 20–40 seconds, never by refreshing and never by ending the turn.
- Partial-completion final messages are prohibited by name, and the prompt's last line repeats the rule: if the evidence table doesn't balance at N/N/N/N with a watched export, keep working.

No prompt can overcome a genuine login, credit, outage, or platform limit — that's exactly what the hard-blocker list is for. Everything short of that gets recovered, not reported.

## How to use

1. **One-time setup:** log in to **app.videoexpress.ai** and **app.clonevoice.ai** in the browser your AI agent controls. In CloneVoice: Settings → API Key → Generate API Key → Copy. In VideoExpress: top-right menu → Edit profile → paste into the **CloneVoice.ai API key** field → Save. Leave the tabs open.
2. Copy the entire [SYSTEM_PROMPT.md](SYSTEM_PROMPT.md).
3. Paste it into Claude, ChatGPT, or Codex, then type one line — your topic (e.g. "the history of Troy"). That's your only input. The agent researches, writes, casts, narrates, animates, syncs, and exports the finished video on its own.

The always-latest copy-paste page: part of the VideoExpress AI Workflow Library.
