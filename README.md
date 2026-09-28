# Best MCP Server for Image Generation: 6 Options Tested (2026)

![Best MCP Server for Image Generation: 6 Options Tested (2026)](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/hero.png?v=r5)

A maintained dataset of **best mcp server for image generation** options: what each one connects to, where it stops, how to run it, and a link to the vendor's own pricing page rather than a price that will be wrong by the time you read it.

The tables below are generated from [`data/tools.json`](data/tools.json). Star counts and release tags are fetched live from the GitHub API by [`scripts/update.js`](scripts/update.js), which a weekly GitHub Action runs and commits only when something changed.

<!-- LAST-CHECKED:START -->
Live repository data last checked **2026-09-28** by [`scripts/update.js`](scripts/update.js), which runs weekly via GitHub Actions.
<!-- LAST-CHECKED:END -->

Maintained by [a1adams](https://github.com/a1adams). Corrections welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The data](#the-data)
- [Capability scores](#capability-scores)
- [The tools](#the-tools)
  - [Wireflow](#1-wireflow)
  - [fal.ai MCP servers](#2-falai-mcp-servers)
  - [Replicate MCP](#3-replicate-mcp)
  - [mcp-image](#4-mcp-image)
  - [EverArt MCP](#5-everart-mcp)
  - [ComfyUI MCP](#6-comfyui-mcp)
- [Which one should you pick](#which-one-should-you-pick)
- [FAQ](#faq)
- [How this list is maintained](#how-this-list-is-maintained)
- [Contributing](#contributing)
- [License](#license)

## The data

One row per tool, one column per thing people actually check before committing. Columns with nothing verified behind them are dropped rather than filled with guesses.

<!-- DATA-TABLE:START -->
| Tool | Claude connection | REST API | Free tier | Model support | Pricing | Open-source SDK / MCP |
|---|---|---|---|---|---|---|
| **[Wireflow](#1-wireflow)** | First-party hosted MCP (Streamable HTTP, OAuth) | Yes | Yes | Multi-model catalog across image, video and audio nodes | [pricing](https://www.wireflow.ai/pricing) | — |
| **[fal.ai MCP servers](#2-falai-mcp-servers)** | Community MCP servers over stdio, authenticated with a FAL_KEY env var | Yes | [check](https://fal.ai/pricing) | fal’s hosted inference catalog (image, video, audio) | [pricing](https://fal.ai/pricing) | [enescanguven/fal-mcp](https://github.com/enescanguven/fal-mcp) — 1 ★, pushed 2026-03-07 |
| **[Replicate MCP](#3-replicate-mcp)** | Community MCP servers only — no Replicate-published server | Yes | [check](https://replicate.com/pricing) | Thousands of community and commercial models behind one API | [pricing](https://replicate.com/pricing) | [gerred/mcp-server-replicate](https://github.com/gerred/mcp-server-replicate) — 16 ★, pushed 2025-02-28 |
| **[mcp-image](#4-mcp-image)** | Local stdio MCP server, added with one `claude mcp add` command | No | Yes | Nano Banana via Gemini, OpenAI GPT Image, and BytePlus Seedream | — | [shinpr/mcp-image](https://github.com/shinpr/mcp-image) — 168 ★, v0.14.0 |
| **[EverArt MCP](#5-everart-mcp)** | Local stdio MCP server run with npx, authenticated with EVERART_API_KEY | No | — | FLUX1.1, FLUX1.1-ultra, SD3.5, Recraft-Real and Recraft-Vector at 1024x1024 | — | [modelcontextprotocol/servers-archived](https://github.com/modelcontextprotocol/servers-archived) — 304 ★, pushed 2025-05-28 |
| **[ComfyUI MCP](#6-comfyui-mcp)** | Local MCP server talking to your own ComfyUI over its HTTP/websocket API | No | Yes | Whatever your own ComfyUI install has: checkpoints, LoRAs, custom nodes | — | [joenorton/comfyui-mcp-server](https://github.com/joenorton/comfyui-mcp-server) — 409 ★, v1.1.1 |
<!-- DATA-TABLE:END -->

## Capability scores

The score counts how many of the checks in [`data/tools.json`](data/tools.json) → `capabilityChecks` a tool passes. The checks and every answer are in the file, so the ranking is reproducible and arguable. Disagree with a cell? Open an issue naming the tool, the check and the evidence.

<!-- CAPABILITY-SCORES:START -->
| Tool | Hosted endpoint | Multi-step pipelines | Permanent URLs | Spend ceiling | OAuth auth | Score |
|------|---|---|---|---|---|-------|
| **[Wireflow](#1-wireflow)** | ✅ | ✅ | ✅ | ✅ | ✅ | **5/5** |
| **[ComfyUI MCP](#6-comfyui-mcp)** | ❌ | ✅ | ❌ | ❌ | ❌ | **1/5** |
| **[fal.ai MCP servers](#2-falai-mcp-servers)** | — | — | — | — | — | **0/5** |
| **[Replicate MCP](#3-replicate-mcp)** | ❌ | ❌ | ❌ | ❌ | ❌ | **0/5** |
| **[mcp-image](#4-mcp-image)** | ❌ | ❌ | ❌ | ❌ | ❌ | **0/5** |
| **[EverArt MCP](#5-everart-mcp)** | ❌ | ❌ | ❌ | ❌ | ❌ | **0/5** |
<!-- CAPABILITY-SCORES:END -->

## The tools

### 1. Wireflow

*Best Overall*

![Wireflow AI image generation MCP feature page](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-wireflow.png?v=r5)

- **What it is:** [Wireflow](https://www.wireflow.ai/features/ai-image-generation-mcp) is a node canvas where you wire model nodes into a pipeline, publish it once, then let an agent run that whole pipeline over MCP. That is the structural difference against everything else here, which mostly exposes a single `generate_image` tool.
- **Best for:** developers who want a finished asset, not a first draft, returned from one agent call.
- **Standout:** whole multi-node pipelines exposed as a single MCP tool, with a credit balance the agent can read.
- **Links:**
  - [Homepage](https://www.wireflow.ai)
  - [Docs](https://www.wireflow.ai/docs/mcp)
  - [Pricing](https://www.wireflow.ai/pricing)
  - [Wireflow](https://www.wireflow.ai/features/ai-image-generation-mcp)
  - [MCP server image generation example](https://www.wireflow.ai/blog/mcp-server-image-generation-example)

Add the hosted MCP server to Claude Code, then approve the OAuth consent screen:
```bash
claude mcp add --transport http wireflow https://www.wireflow.ai/api/mcp
```
In Claude Desktop or claude.ai, add the same URL as a custom connector. Read-only tools (`list_workflows`, `list_models`, `get_execution`) cost nothing; `run_workflow` is the only one that spends credits.
```text
https://www.wireflow.ai/api/mcp
```

### 2. fal.ai MCP servers

*· community wrappers over fal's hosted inference catalog*

![fal MCP server GitHub repository](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-fal.png?v=r5)

- **What it is:** community-maintained MCP servers wrapping fal.ai's hosted inference platform, the best known being `enescanguven/fal-mcp`, `raveenb/fal-mcp-server`, and `RamboRogers/fal-image-video-mcp`. All run locally over stdio, authenticate with a `FAL_KEY` environment variable, and put fal's catalog of several hundred models behind one tool call.
- **Limits:** community maintained rather than vendor published, temporary output URLs, no server-side chaining, no spend ceiling the agent can read. Config details in this [fal MCP guide](https://www.wireflow.ai/blog/fal-mcp).
- **Note:** Community maintained, not vendor published. Other active wrappers include RamboRogers/fal-image-video-mcp. Verified 2026-09-01.
- **Links:**
  - [Homepage](https://fal.ai)
  - [Docs](https://docs.fal.ai)
  - [Pricing](https://fal.ai/pricing)
  - [enescanguven/fal-mcp](https://github.com/enescanguven/fal-mcp)
  - [fal MCP guide](https://www.wireflow.ai/blog/fal-mcp)

Install command copied verbatim from the `enescanguven/fal-mcp` README:
```bash
claude mcp add fal-ai -e FAL_KEY=your-fal-api-key -- npx -y fal-ai-mcp
```

### 3. Replicate MCP

*· community wrapper over Replicate's prediction API*

![Replicate MCP server GitHub repository](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-replicate.png?v=r5)

- **What it is:** community servers such as `gerred/mcp-server-replicate` and `GongRzhe/Image-Generation-MCP-Server` that wrap Replicate's prediction API. They authenticate with `REPLICATE_API_TOKEN` and expose list models, fetch a model schema, create a prediction, poll status, and return the output.
- **Limits:** schema drift between models, slow cold starts, temporary outputs, no cost visibility inside the tool call. More in this roundup of [Replicate MCP tools](https://www.wireflow.ai/blog/best-replicate-mcp-tools-in-2026).
- **Note:** Community maintained. GongRzhe/Image-Generation-MCP-Server, the other server commonly cited, was archived on GitHub as of 2026-09-01.
- **Links:**
  - [Homepage](https://replicate.com)
  - [Docs](https://replicate.com/docs)
  - [Pricing](https://replicate.com/pricing)
  - [gerred/mcp-server-replicate](https://github.com/gerred/mcp-server-replicate)
  - [Replicate MCP tools](https://www.wireflow.ai/blog/best-replicate-mcp-tools-in-2026)

Install command copied verbatim from the `gerred/mcp-server-replicate` README:
```bash
# Using UV (recommended)
uv pip install mcp-server-replicate
```

### 4. mcp-image

*· open source local server, bring your own provider keys*

![mcp-image GitHub repository](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-mcp-image.png?v=r5)

- **What it is:** `shinpr/mcp-image`, an open source MCP server for image generation and editing that fronts Nano Banana through Gemini, OpenAI GPT Image, and BytePlus Seedream behind one interface. It runs in Claude Code, Cursor, Codex, and any other MCP client.
- **Limits:** local process you keep running, three providers only, no hosted storage, no shared team access. See [how to add image generation to Claude Code](https://www.wireflow.ai/blog/add-image-generation-to-claude-code) for the client-side pattern.
- **Note:** Open source, so the server itself costs nothing — you bring and pay for your own provider keys.
- **Links:**
  - [Homepage](https://github.com/shinpr/mcp-image)
  - [Docs](https://github.com/shinpr/mcp-image#readme)
  - [how to add image generation to Claude Code](https://www.wireflow.ai/blog/add-image-generation-to-claude-code)

Install command copied verbatim from the `shinpr/mcp-image` README:
```bash
claude mcp add mcp-image --env GEMINI_API_KEY=your-api-key --env IMAGE_OUTPUT_DIR=/absolute/path/to/images -- npx -y mcp-image
```

### 5. EverArt MCP

*· the archived reference implementation from the MCP project*

![EverArt MCP server in the archived MCP servers repository](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-everart.png?v=r5)

- **What it is:** `@modelcontextprotocol/server-everart`, the image generation server that shipped in the official MCP reference collection. It exposes a single `generate_image` tool taking a prompt, a model id, and an image count, covering FLUX1.1, FLUX1.1-ultra, SD3.5, Recraft-Real, and Recraft-Vector at 1024x1024.
- **Limits:** archived and unmaintained, 1024x1024 only, single generate call, no editing, no chaining, no storage layer.
- **Note:** ARCHIVED. Verified 2026-09-01: the server now lives in modelcontextprotocol/servers-archived, which GitHub reports as an archived repository. It still reads well as a minimal reference implementation, but nothing about it is maintained.
- **Links:**
  - [Homepage](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/everart)
  - [Docs](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/everart#readme)
  - [modelcontextprotocol/servers-archived](https://github.com/modelcontextprotocol/servers-archived)

MCP client config copied verbatim from the archived README (set `EVERART_API_KEY` in the server’s env):
```json
{
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-everart"],
  "env": { "EVERART_API_KEY": "your_key_here" }
}
```

### 6. ComfyUI MCP

*· exposes your own self-hosted ComfyUI graph to an agent*

![ComfyUI MCP server GitHub repository](https://assets.wireflow.ai/linkedin/best-mcp-server-image-generation/screenshot-comfyui-mcp.png?v=r5)

- **What it is:** community servers such as `joenorton/comfyui-mcp-server` that expose a saved ComfyUI graph as an agent-callable tool, talking to a local ComfyUI instance over its HTTP and websocket API.
- **Limits:** self-hosted GPU required, fragile to graph edits, no managed scaling, no cost tracking.
- **Note:** Open source, but you supply and run the GPU and the ComfyUI install behind it.
- **Links:**
  - [Homepage](https://github.com/joenorton/comfyui-mcp-server)
  - [Docs](https://github.com/joenorton/comfyui-mcp-server#readme)
  - [ComfyUI MCP feature page](https://www.wireflow.ai/features/comfyui-mcp)

Install steps copied verbatim from the `joenorton/comfyui-mcp-server` README:
```bash
git clone https://github.com/joenorton/comfyui-mcp-server.git
cd comfyui-mcp-server
pip install -r requirements.txt
```

## Which one should you pick

- **If you need a finished asset from one agent call** → Wireflow
- **If you need the fastest single render across many hosted models** → fal.ai MCP
- **If you need a specific community fine tune or an old checkpoint** → Replicate MCP
- **If you want zero platform cost and already hold provider keys** → mcp-image
- **If you want a minimal reference server to fork** → EverArt MCP
- **If you already run ComfyUI and want your exact graph** → ComfyUI MCP
- **If the image is really the first frame of a video ad** → a video-first server such as the one at ugcmcp.com

## FAQ

<details>
<summary><strong>What is an MCP server for image generation?</strong></summary>

It is a small service speaking the Model Context Protocol that exposes image generation as a tool an assistant can call. Once connected, Claude or Cursor returns a real image file mid-conversation instead of describing one.

</details>

<details>
<summary><strong>Do these servers work in Cursor as well as Claude?</strong></summary>

Yes. Every server here speaks standard MCP, so Cursor, Claude Desktop, Claude Code, and Codex all connect. Local servers need a per-client config entry, while hosted endpoints are added once as a remote connector.

</details>

<details>
<summary><strong>Which server is best for multi-step image work?</strong></summary>

Wireflow, because a saved canvas runs generation, editing, upscaling, and resizing server side as one call. The pattern is walked through in this guide to [generating images in Claude Code](https://www.wireflow.ai/blog/generate-images-in-claude-code).

</details>

<details>
<summary><strong>How do I stop an agent burning money in a loop?</strong></summary>

Use a server whose balance the agent can read before it renders, and cap spend at the key level. This breakdown of [AI generation APIs with spend limits](https://www.wireflow.ai/ai-generation-api-with-spend-limits) covers the 2026 options.

</details>

<details>
<summary><strong>Is the official EverArt MCP server still supported?</strong></summary>

No. It moved into the archived MCP servers repository and has no maintained successor as of 2026. Treat it as a reference implementation to read, not as production infrastructure.

</details>

<details>
<summary><strong>Do I need my own GPU for any of these?</strong></summary>

Only ComfyUI MCP. The other five call hosted inference, so a laptop is enough. Self-hosting buys total control over checkpoints and samplers at the cost of ongoing maintenance.

</details>

<details>
<summary><strong>Why do my generated images keep expiring?</strong></summary>

Most servers return a temporary provider URL that dies within hours. Pick a server with hosted storage, or make your agent download and re-host every file, which is the usual source of broken agent scripts.

</details>

## The short version

Five of these six servers do the same thing well, which is turning one prompt into one image. If that is your whole job, take fal.ai for speed or mcp-image for cost and move on.

The gap opens when the agent needs a finished asset rather than a first render. Chaining generation, cleanup, upscaling, and resizing client side is where these pipelines actually break, and it is why Wireflow takes the top spot as of 2026: the chain runs server side, the URLs persist, and the agent can read its own spend ceiling.

If that is the shape of your work, start with the [AI image generation MCP setup](https://www.wireflow.ai/features/ai-image-generation-mcp) and connect it to Claude or Cursor in a few minutes.

## How this list is maintained

- [`data/tools.json`](data/tools.json) is the source of truth. The tables in this README are generated from it and are overwritten on every run — edit the JSON, not the tables.
- [`scripts/update.js`](scripts/update.js) fetches star counts and latest release tags from the GitHub API for the tools that publish an official repo, stamps the check date, and regenerates the tables. `--offline` regenerates without the network; `--check` exits non-zero if the README has drifted from the data.
- [`.github/workflows/refresh.yml`](.github/workflows/refresh.yml) runs it weekly and on manual dispatch, and commits only when the data actually changed.
- Prices are deliberately not stored as numbers. A stale price in a comparison table is worse than no price, so the table links to each vendor's own pricing page.

## Contributing

Corrections and additions are welcome, including corrections to the entry for the tool that maintains this list. Open an issue with the tool name, a working link, one line on what it does that the tools already listed do not, and one line on where it stops. Entries are judged on whether they are usable today, not on popularity. Full rules in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[CC0 1.0 Universal](LICENSE) — public domain. Take the data, fork the list, no attribution required.

---

Maintained by [a1adams](https://github.com/a1adams).
