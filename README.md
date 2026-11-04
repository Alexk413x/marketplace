# The Library

Claude Code plugins that each work on their own and work better together.

## Install

Add the marketplace once, then install any plugin below with its command:

```sh
claude plugin marketplace add Alexk413x/marketplace
```

## Plugins

- **[Agent Tabs](https://github.com/Alexk413x/ide-agent-tabs)** - Opens agent sessions in IDE
  and terminal tabs, messages between them, and delegates work to another agent CLI.

  ```sh
  claude plugin install ide-agent-tabs@alexk413x
  ```

- **[Codebase KG](https://github.com/Alexk413x/codebase-kg)** - A committed, searchable code
  graph for each repo, so an agent finds code without mapping it again every session.

  ```sh
  claude plugin install codebase-kg@alexk413x
  ```

- **[Sentinel Swarm](https://github.com/Alexk413x/sentinel-swarm)** - An agent swarm that
  takes a PRD to built, tested, reviewed code, with every hand-off checked against a shared
  ledger. Requires Codebase KG.

  ```sh
  claude plugin install codebase-kg@alexk413x
  claude plugin install sentinel-swarm@alexk413x
  ```

- **[The Index](https://github.com/Alexk413x/the-index)** - A band above the prompt that
  shows session cost, limits and git state.

  ```sh
  claude plugin install the-index@alexk413x
  ```

Each plugin has its own licence in its repository.

## Copilot CLI

Copilot CLI can discover this catalog without changing the Claude Code setup.
It supports `.claude-plugin/marketplace.json`, `.claude-plugin/plugin.json`,
and Git URL sources with a `ref`. Keep the existing manifests and Claude
installation commands in place.

With Copilot CLI installed and signed in, register and browse the catalog:

```sh
copilot plugin marketplace add Alexk413x/marketplace
copilot plugin marketplace browse alexk413x
```

The marketplace name is `alexk413x`, not `marketplace`. The Copilot CLI install
syntax is `copilot plugin install PLUGIN@alexk413x`. Check the support table
before installing. A discoverable or installed plugin does not establish that
its MCP connection, hooks, skills, or UI work in Copilot.

### Feature support

| Plugin | Claude Code | Copilot CLI |
|---|---|---|
| Agent Tabs | Existing plugin, MCP tools, hooks, and mod UI. | Has a Copilot CLI MCP and messaging-hook integration for agent tabs. Follow its [agent support guidance](https://github.com/Alexk413x/ide-agent-tabs/blob/main/mcp/README.md#agent-support). The Claude mod UI does not transfer. Marketplace-installed runtime support needs release verification. |
| Codebase KG | Existing plugin, MCP tools, and Claude hooks. | Connection, authentication, and hook behavior need verification. Follow its [client setup guidance](https://github.com/Alexk413x/codebase-kg#readme); do not copy the Claude MCP configuration into Copilot. |
| Sentinel Swarm | Requires Codebase KG, Claude workers, and Claude mod enforcement. | Not supported as a Copilot-native swarm. Discovering skills or an MCP server does not replace those worker and enforcement requirements. |
| The Index | Claude Code only. | Not supported. Copilot support is deferred. |

This table applies to Copilot CLI, not Copilot Chat in VS Code, the Copilot
desktop app, or the GitHub-hosted coding agent. Those surfaces need separate
integration and verification. Agent Tabs needs local access to the target IDEs
or terminals. Opening a Copilot CLI tab does not load every plugin feature into it.

### Setup and verification

Follow the plugin's client-specific setup before using it. After setup, start
a new Copilot CLI session. Use `copilot plugin list` to check installation and
`/mcp` to inspect the MCP connection. Exercise a read-only tool and check the
documented hook behavior separately. A connected MCP server does not establish
hook support.

The release-layout check on 2026-11-03 found Agent Tabs 0.9.10 and Codebase KG
0.15.3 using `mcp/claude.mcp.json`. These configurations use Claude's
`user_config` substitutions and `headersHelper`. Do not assume Copilot can use
them unchanged. Copilot runtime support remains unverified for these releases.

Every catalog entry fetches its repository's `release` ref at the repository
root. All four refs contain matching `.claude-plugin/plugin.json` manifests.
Do not replace `release` with `main`: development repositories can keep their
plugins in subdirectories. Changes in a development branch or checkout do not
reach marketplace users until the release process publishes them to `release`.

To fetch a published plugin fix in Copilot CLI, update that plugin by name, for
example `copilot plugin update ide-agent-tabs`. Use
`copilot plugin marketplace update alexk413x` to refresh catalog changes.
Neither command adds support that the published plugin does not provide.

See GitHub's [plugin installation guide](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/plugins-finding-installing)
and [CLI plugin reference](https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-plugin-reference)
for supported formats and commands.
