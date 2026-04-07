# NoteWeave
Your notes are connected. You just haven't seen it yet.

You write notes, then forget they exist. Months later, you might rewrite the same idea without realizing you'd already explored it. NoteWeave finds those hidden connections for you.

It is an agent for the Cocapn Fleet that reads the plain text or markdown notes you already keep. It does not ask you to tag, link, or change your writing process.

---

## Why This Exists
Other tools require you to organize your thoughts upfront. NoteWeave was built for people who write messy, exploratory notes and want the insights surfaced afterward, not as a prerequisite.

---

## Quick Start
1.  **Fork** this repository. This is a required first step.
2.  Deploy it as a Cloudflare Worker with one click. No local setup is needed.
3.  Add your LLM API key and the path to your note repository as [Worker secrets](https://developers.cloudflare.com/workers/configuration/secrets/).

It will run on a schedule, analyze new commits, and push all its suggestions to a separate branch named `noteweave` for you to review. You control what gets merged.

**See a Live Example:** It is running against public sample notes on [The Fleet](https://the-fleet.casey-digennaro.workers.dev).

---

## How It Works
NoteWeave runs as a scheduled Cloudflare Worker. It has zero npm dependencies. It clones your note repository, performs a semantic analysis on plain text files, and writes all its output as new, standard markdown files. Your original notes are never modified.

### What It Does
*   **Finds Thematic Links**: Generates a `LINKS.md` file with bidirectional connections between notes that share underlying concepts, not just keywords.
*   **Synthesizes Clusters**: When a common thread appears across three or more notes, it writes a short synthesis note to summarize the thread, citing every source line it used.
*   **Is Non-Destructive**: It only ever writes to its own branch. Your main branch and original files are left untouched.
*   **Avoids Lock-in**: It reads and writes standard markdown. You can stop using it at any time without breaking your notes.
*   **Is Self-Hosted**: You provide your own LLM API keys. There is no central server, and no one else ever sees your notes.

**An Honest Limitation**: The synthesis feature is constrained by your LLM's context window. If a cluster of connected notes exceeds a manageable size (typically notes with a combined text over 6000 tokens), it will skip synthesis for that group rather than produce a low-quality summary.

---

## What Makes This Different
1.  It does not run inside your editor. It operates alongside your notes on its own schedule.
2.  There is no new UI or account. You interact with it through git, using your existing workflow.
3.  It will never ask you to change how you write. No required tags, frontmatter, or special syntax.

---

## License
MIT License.

---

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>