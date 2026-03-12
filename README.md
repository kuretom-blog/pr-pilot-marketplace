# pr-pilot

A Claude Code plugin that streamlines your entire PR workflow — from code review to changelog generation, commit message drafting, and test gap analysis.

## Skills

### `/review` — Code Review
Analyzes diffs or code snippets across four dimensions:
- **Readability** — naming, structure, clarity
- **Performance** — inefficiencies, N+1 queries, unnecessary allocations
- **Security** — injection, auth gaps, secret exposure
- **Maintainability** — duplication, coupling, testability

Each issue is categorized by severity (Critical / Warning / Info) with concrete fix suggestions.

### `/changelog` — Changelog Generation
Generates [Keep a Changelog](https://keepachangelog.com/) formatted entries from diffs or commit history. Automatically categorizes changes into Added, Changed, Fixed, Removed, Deprecated, and Security sections.

### `/commit-msg` — Commit Message Drafting
Drafts [Conventional Commits](https://www.conventionalcommits.org/) compliant messages with auto-detected type, scope, and breaking change identification. Provides up to 3 candidates to choose from.

### `/test-suggest` — Test Gap Analysis
Identifies missing test cases for changed code, covering:
- Normal paths and key use cases
- Boundary values (null, empty, min/max)
- Error paths and exception handling
- Regression risks from the current change

Outputs ready-to-use test code matching your project's framework.

## Installation

```bash
claude plugin add kuretom-blog/pr-pilot
```

## Usage Examples

```bash
# Review staged changes
/review $(git diff --cached)

# Generate changelog for recent commits
/changelog $(git log --oneline -10)

# Draft a commit message from staged diff
/commit-msg $(git diff --cached)

# Suggest tests for changed files
/test-suggest $(git diff main)
```

## Project Structure

```
.claude-plugin/
  plugin.json            # Plugin metadata
skills/
  review/SKILL.md        # Code review skill
  changelog/SKILL.md     # Changelog generation skill
  commit-msg/SKILL.md    # Commit message drafting skill
  test-suggest/SKILL.md  # Test suggestion skill
```

## License

MIT License. See [LICENSE](LICENSE) for details.

## Author

kuretom
