# CLAUDE.md (claude-md)
CLAUDE.md is the markdown-based project memory format used by Anthropic's Claude Code CLI to give the model persistent, session-spanning instructions about a codebase. CLAUDE.md files are plain markdown that Claude Code loads at session start by walking up the directory tree from the working directory, picking up files at organization-managed, user (~/.claude/CLAUDE.md), project (./CLAUDE.md or ./.claude/CLAUDE.md), and local (./CLAUDE.local.md) scopes. The format supports an `@path` import syntax for composing files together (up to five hops), HTML block comments that are stripped before injection, an AGENTS.md import pattern for compatibility with other agents, and a complementary `.claude/rules/` directory of path-scoped markdown rules with YAML frontmatter.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/claude-md/refs/heads/main/apis.yml)

## Scope

- **Type:** Standard
- **Position:** Standard
- **Access:** Open

## Tags:

 - AI Agents, Claude Code, Coding Standards, Configuration, Developer Workflow, Markdown, Memory, Project Configuration, Standard

## Timestamps

- **Created:** 2025-01-01
- **Modified:** 2026-04-23

## Standard Artifacts

### CLAUDE.md File Format
Plain-markdown file containing project, user, or organization-wide instructions that Claude Code loads as a user message at session start. Recommended size is under 200 lines per file with concrete, verifiable instructions and markdown headers and bullets for structure.

**Reference:** [https://code.claude.com/docs/en/memory](https://code.claude.com/docs/en/memory)

### CLAUDE.md @path Imports
The `@path/to/file` syntax expands and inlines another file into a CLAUDE.md at load time. Imports support relative and absolute paths, recursive imports up to five hops, and are commonly used to pull in README, AGENTS.md, package.json, or shared instruction files from a user's home directory.

**Reference:** [https://code.claude.com/docs/en/memory#import-additional-files](https://code.claude.com/docs/en/memory#import-additional-files)

### CLAUDE.md Scope Hierarchy
CLAUDE.md resolves through four scopes:

| Scope | Location | Sharing |
|-------|----------|---------|
| Managed policy | `/Library/Application Support/ClaudeCode/CLAUDE.md`, `/etc/claude-code/CLAUDE.md`, `C:\Program Files\ClaudeCode\CLAUDE.md` | Organization-wide via MDM/Group Policy |
| Project | `./CLAUDE.md` or `./.claude/CLAUDE.md` | Team via source control |
| User | `~/.claude/CLAUDE.md` | Just you, all projects |
| Local | `./CLAUDE.local.md` | Just you, current project (gitignored) |

All discovered files are concatenated into context rather than overriding each other.

### .claude/rules/ Directory
Modular markdown rule files with optional YAML frontmatter declaring a `paths` list of glob patterns. Rules without paths load at launch alongside CLAUDE.md; path-scoped rules load only when Claude reads files matching the patterns.

**Reference:** [https://code.claude.com/docs/en/memory#organize-rules-with-claude/rules/](https://code.claude.com/docs/en/memory#organize-rules-with-claude/rules/)

### Claude Code Auto Memory
Auto memory is the machine-managed companion to CLAUDE.md. Claude Code maintains `~/.claude/projects/<project>/memory/MEMORY.md` as a concise index plus topic files written and read by the agent across sessions. The first 200 lines or 25 KB of MEMORY.md load at session start.

**Reference:** [https://code.claude.com/docs/en/memory#auto-memory](https://code.claude.com/docs/en/memory#auto-memory)

## Common Properties

- [Specification](https://code.claude.com/docs/en/memory)
- [Documentation](https://code.claude.com/docs/en/memory#claude-md-files)
- [Vendor (Anthropic)](https://www.anthropic.com/)
- [Tool (Claude Code)](https://code.claude.com/)
- [Settings Reference](https://code.claude.com/docs/en/settings)
- [Hooks Reference](https://code.claude.com/docs/en/hooks)
- [JSON-LD Context](json-ld/claude-md-context.jsonld)
- [Naftiko Capabilities](capabilities/claude-md-capabilities.yml)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
