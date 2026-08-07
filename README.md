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

## How to use

1. **One-time setup:** log in to **app.videoexpress.ai** and **app.clonevoice.ai** in the browser your AI agent controls. In CloneVoice: Settings → API Key → Generate API Key → Copy. In VideoExpress: top-right menu → Edit profile → paste into the **CloneVoice.ai API key** field → Save. Leave the tabs open.
2. Copy the entire [SYSTEM_PROMPT.md](SYSTEM_PROMPT.md).
3. Paste it into Claude, ChatGPT, or Codex, then type one line — your topic (e.g. "the history of Troy"). That's your only input. The agent researches, writes, casts, narrates, animates, syncs, and exports the finished video on its own.

The always-latest copy-paste page: part of the VideoExpress AI Workflow Library.
