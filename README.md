# NoteWeave
Connected notes. No extra work.

You write notes. Then you forget they exist. Three months from now you might write the same thought again, without noticing you'd already solved half the problem last quarter.

NoteWeave is an agent for the Cocapn Fleet that watches the plain text notes you already keep. It doesn't ask you to tag, link, or change how you write. It finds the connections you missed.

---

## Why This Exists
Many tools promise to connect your ideas, but they make *you* do the connecting. You stop mid-thought to add tags, or remember to search old notes every time you write something new.

This is backwards. Your notes already contain the connections. NoteWeave doesn't replace your workflow. It does the remembering for you.

---

## What It Does
It runs against your git note repository. All output is written as new files. Your original notes are never modified.

*   **Thematic Links**: Builds a `LINKS.md` file with bidirectional connections between notes that share underlying meaning, not just matching keywords.
*   **Cluster Synthesis**: When a consistent thread appears across 3+ notes, it writes a short synthesis note that ties the thread together, with citations back to every source line. It does not invent ideas.
*   **Non-destructive by design**: It never edits, deletes, or rewrites your original files. All suggestions are pushed to a separate `noteweave` branch.
*   **Zero lock-in**: This is code that reads and writes standard markdown. You can stop using it tomorrow. None of your notes will break.

**Limitation**: Synthesis works for small, tight clusters of notes. It respects LLM context window limits and will skip large groups rather than produce low-quality output.

---

## What Makes This Different
This is not another note app.
1.  You don't import anything. It works on the markdown files you already write.
2.  You host it. You bring your own LLM keys. There is no central server or telemetry.
3.  It tries to be useful, not clever. It will leave you alone unless it finds something worth showing you.

---

## How To Run
This is a fork-first agent.
1.  Fork this repository.
2.  Deploy as a Cloudflare Worker.
3.  Add your LLM provider API keys as worker secrets.
4.  Point it at a git note repository.

It will periodically check for new commits, run analysis, and open branches with suggestions for review.

---

## Try The Demo
See it running against public sample notes on the Fleet hub.

Attribution: Superinstance & Lucineer (DiGennaro et al.).

<div>
<a href="https://the-fleet.casey-digennaro.workers.dev">Fleet</a> · <a href="https://cocapn.ai">Cocapn</a>
</div>