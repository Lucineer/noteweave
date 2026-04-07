# NoteWeave

You have notes. This agent quietly looks for connections between them.

NoteWeave is an agent for the Cocapn Fleet that reads the plain-text notes you already keep in a git repository, finds thematic links, and suggests connections you might have missed.

---

## Why This Exists

Most tools for connecting ideas require you to do the work—tagging, linking, and recalling old notes. NoteWeave runs in the background on the markdown files you already have, helping you discover relationships without changing your workflow.

## What It Does

It scans your note repository, uses embeddings to group related content, and creates two types of suggestions as separate files in your repo.

*   **Links**: Generates a `LINKS.md` file proposing bi-directional links between notes that share underlying themes, not just keywords.
*   **Synthesis**: When it identifies a strong cluster across several notes, it writes a short synthesis note that summarizes the thread, citing each source note.
*   **Non-Destructive**: It never modifies your original files. All output is written to its own directory. Review, merge, or ignore the suggestions at your pace.
*   **Self-Contained**: Deploys as a single Cloudflare Worker with zero external dependencies.

**Limitation:** Synthesis is constrained by the context window of the configured LLM. It works best on clusters of notes where the combined relevant excerpts fit within that limit.

---

## How It Works

1.  **Fork** this repository.
2.  **Deploy** to Cloudflare Workers.
3.  **Configure** your LLM provider API keys as environment secrets.
4.  **Point** it at a public or private git repository containing your notes.

It will periodically clone your repo, analyze new commits, and push suggestions back to a branch for your review.

## Try It

You can see a demo with public notes at the Fleet hub:
https://the-fleet.casey-digennaro.workers.dev/agents/noteweave

## Architecture

A stateless, scheduled Cloudflare Worker. It interacts only via git operations, holds no persistent data, and signs all commits for traceability.

## Bring Your Own Keys

You supply the API keys for your chosen LLM provider. No credentials are bundled, and there are no proxy calls or telemetry.

---

MIT License. Built as part of Cocapn Fleet by Superinstance & Lucineer (DiGennaro et al.).

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> · <a href="https://cocapn.ai">Cocapn</a>
</div>