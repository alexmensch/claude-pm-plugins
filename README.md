# PM Plugins for Claude Code

A collection of Claude Code plugins for product managers and developers who want structured, disciplined feature development workflows.

## Installation

Add this repository as a plugin marketplace, then install the plugin you want:

```
/plugin marketplace add alexmensch/claude-pm-plugins
/plugin install new-feature@pm-plugins
```

## Plugins

### new-feature

Build new product features with a strict development workflow anchored on test-driven acceptance and disciplined coding practices.

Invoke it with `/new-feature` inside Claude Code and describe the feature you want to build. The plugin orchestrates the entire process end-to-end using three specialized agents:

- **technical-spec** -- Analyses the existing codebase in depth, produces a structured requirements table with acceptance criteria and edge cases, and confirms the specification with you before any code is written.
- **test-writer** -- Takes the approved spec and writes comprehensive tests covering all acceptance criteria and edge cases. Runs in the background in an isolated worktree so tests and implementation happen in parallel.
- **code-reviewer** -- Reviews all branch changes before a PR is opened. Checks for DRY violations, unnecessary complexity, duplicated patterns, and unnecessary dependencies. Presents findings for your approval before committing fixes.

#### Workflow

1. A new branch is created from the default branch.
2. You describe the feature. The plugin clarifies ambiguous requirements, then hands them to the **technical-spec** agent which produces a detailed spec for your approval.
3. Once the spec is approved, **test-writer** starts writing tests in the background while implementation code is written in parallel against the same spec.
4. Tests are merged in and the full suite is run. Test failures are treated as implementation bugs, not test bugs -- tests are never changed without your confirmation.
5. The **code-reviewer** agent reviews all changes and presents findings. You decide which fixes to apply.
6. Linting, build verification, documentation updates, and semver versioning are handled.
7. You are prompted to commit and open a PR.

## License

[MIT](LICENSE)
