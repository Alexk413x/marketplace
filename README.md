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
