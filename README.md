# DeepSeek Harness

English | [中文](README.zh.md)

DeepSeek Harness (`dsh`) is an open-source agent harness developed by [DeepSeek AI](https://deepseek.com).

It is built on an **everything-is-a-plugin** architecture and powered by [Cordis](https://github.com/cordiverse/cordis), whose design is described in [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512).

Documentation: [https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## What it does

DeepSeek Harness runs configurable AI agents that can inspect and edit workspace files, execute shell commands, search and fetch web content, and delegate work to subagents. Sessions retain durable history so users can resume work and review what happened.

Profiles package these capabilities for an interactive Web UI, one-shot headless tasks, TypeScript and Python SDK integrations, or ACP automation clients. Plugins let teams select models, tools, execution providers, and permission policies; the [architecture guide](docs/architecture.md) explains how those pieces compose.

## Typical use cases

- **Repository development:** understand a codebase, edit files, run checks, and coordinate multi-step changes in a workspace.
- **Research and knowledge work:** search and fetch web content, or connect external services through MCP within a durable session.
- **Workflow integration:** run one-off tasks from a terminal or script, embed an agent through an SDK, or connect an ACP automation host.
- **Purpose-built agents:** compose profiles and plugins around the models, tools, and execution policies a workflow requires.

## Choose an entry point

| Entry point | Best fit |
|---|---|
| Web UI | Interactive sessions with a browser-based workspace and settings. |
| Headless profile | One-shot tasks from a terminal or automation job. |
| TypeScript or Python SDK | Integrating agent sessions into an application. See the [Python SDK guide](docs/user/guide/python-sdk.md). |
| ACP profile | Connecting automation clients through the Agent Client Protocol. |
| Desktop app | Using the packaged desktop application. |

Tool access and execution are governed by the selected profile's configuration, sandbox, and approval policy. Read the [safety notice](SAFETY.md) before running DSH.

## Developer preview

DeepSeek Harness is in _developer preview_ and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

Review the [safety notice](SAFETY.md) before running the project.

## Run

### Run from `npm`

Install `Node.js`, then run:

```sh
npx @deepseek-ai/dsh web
```

The command starts the Web UI at `http://127.0.0.1:3080` by default and opens it in the default browser for a local launch. An SSH launch only prints the host URL because the SSH client or editor owns the local forwarded address. Pass `--no-open` to run the server without opening a browser. See [Web UI guide](docs/user/guide/index.md).

### Run from source

To run from a repository checkout:

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` prepares the repository artifacts. `pnpm dsh web` uses those built artifacts without rebuilding.

## Community and support

- Submit feedback or bug reports through [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions).
- Add the [`dsh-plugin`](https://github.com/topics/dsh-plugin) topic to your plugin repository for discoverability.
- Join <a href="https://discord.gg/4MrtZUhpxg">DeepSeek Harness Discord community</a>.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Development

Start with the [development guide](docs/development.md) and [architecture documentation](docs/architecture.md).

`pnpm run dev:web` builds, serves, and rebuilds client bundles on source edits in one terminal, and `make help` lists the matching Make targets for Web and Desktop; the guide's application commands section owns the full table.

For agents, follow [AGENTS.md](AGENTS.md).

## Citation

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## License

[MIT](LICENSE)

Third-party dependencies and their licenses are disclosed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
