# NoteWeave
You take notes. Most of the time, they just sit there.

NoteWeave is an agent for the Cocapn Fleet that reads your notes and suggests connections between them. It helps build a graph from your existing writing without manual tagging.

---

## Purpose
It can be tedious to manually organize every note you write. This agent is designed to work with the notes you already have, running on infrastructure you control.

---

## How It Works
- **No External Database**: Your git repository stores the agent's state and graph.
- **Non-Destructive**: It does not edit your original note files. Links and generated notes are added as separate, versioned commits.
- **Self-Contained**: Fork the repository to run your own copy. It requires no external accounts.
- **Runs on Cloudflare Workers**: The agent is designed for serverless execution.

---

## Features
*   **Semantic Linking**: Suggests connections between notes based on their content.
*   **Graph Synthesis**: Can generate summary notes that reference multiple source notes.
*   **Git-Native**: All agent output is committed to your repository, maintaining a full history.
*   **Fork-First**: This is code to run yourself, not a hosted service.
*   **BYOK (Bring Your Own Keys)**: You provide API keys via environment secrets. The code contains no built-in credentials.
*   **Stateless Design**: The agent reads from and writes to your repository directly.

**Limitation**: The accuracy of suggested links depends on the capabilities of the underlying LLM you configure.

---

## Try the Reference Agent
A public instance is available for testing:
[https://the-fleet.casey-digennaro.workers.dev/agents/noteweave](https://the-fleet.casey-digennaro.workers.dev/agents/noteweave)

---

## Quick Start
1.  Fork this repository to your GitHub account.
2.  Deploy it to Cloudflare Workers.
3.  Configure your model API keys via environment secrets.

---

## Configuration
The agent requires API keys for the LLM provider of your choice (e.g., OpenAI, Anthropic). Set these as secrets in your Cloudflare Workers deployment.

---

## Contributing
Contributions are welcome. Please open an issue to discuss significant changes.

---

## License & Attribution
MIT License. Created as part of the Cocapn Fleet by Superinstance & Lucineer (DiGennaro et al.).

---

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> · <a href="https://cocapn.ai">Cocapn</a>
</div>