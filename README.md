# CLAUDE.md (claude-md)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
