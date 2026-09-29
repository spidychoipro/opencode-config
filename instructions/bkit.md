# bkit Global Configuration

## Project Level

Automatically detect project level (Starter/Dynamic/Enterprise).
Use `$starter`, `$dynamic`, or `$enterprise` skill for level-specific guidance.

## PDCA + NSP (Negative Space Programming) Workflow

For features and changes:

1. **Quick Fix** (<10 lines): Execute immediately
2. **Minor Change** (<50 lines): Proceed with summary
3. **Feature** (<200 lines): Create plan/design docs first
4. **Major Feature** (>=200 lines): Split into subtasks with design

### NSP — MUST DO in every phase

When planning, designing, or implementing, ALWAYS define:

- **What NOT to do**: Explicit constraints, forbidden patterns, excluded features
- **Anti-patterns to avoid**: Known bad practices
- **Out of scope**: What this feature intentionally excludes
- **Tech NOT to use**: Libraries, approaches that are off-limits
- **Boundaries**: Limits on perf, scale, complexity, dependencies
- **Edge cases NOT to handle**: Explicitly deferred cases

Record NSP in every PDCA document under a `## Negative Space` section.

### PDCA Phases

- `$pdca plan` — Create plan document (with NSP)
- `$pdca design` — Create design document (with NSP)
- `$pdca do` — Implement
- `$pdca analyze` — Gap analysis (including NSP violations)
- `$pdca report` — Completion report

## Skill Roles & Boundaries

| Skill              | Role                                     | Scope                              |
| ------------------ | ---------------------------------------- | ---------------------------------- |
| **PDCA**           | Planning, execution, review, improvement | Process & lifecycle                |
| **NSP**            | Project context, conventions, long-term consistency | Constraints & boundaries |
| **Karpathy Guidelines** | Implementation behavior            | Code writing discipline            |

## Implementation Rules (from Karpathy)

- Read existing code before making changes.
- Preserve the current architecture unless explicitly instructed otherwise.
- Before creating new files, classes, modules, or abstractions, first determine whether the existing project structure or implementation can be extended. Prefer extension over duplication.
- Generate the smallest possible diff.
- Avoid unnecessary refactoring or formatting changes.
- Never guess APIs or behavior; inspect the existing code first.
- If requirements are ambiguous and multiple reasonable implementations exist, ask a clarifying question before making irreversible changes. Do not infer user intent when it could significantly affect the architecture, behavior, or public API.
- Keep responses concise and focus on the requested task.

If a requested change conflicts with an existing skill, explain the conflict briefly before proceeding.

## Conflict Resolution Priority

If multiple instructions apply, follow them in this order:

1. **Explicit user request**
2. **Safety requirements**
3. **NSP** (project constraints and boundaries)
4. **PDCA** (planning and execution workflow)
5. **Karpathy Guidelines** (implementation style)

Never use a lower-priority rule to override a higher-priority one.

When a conflict exists, explain it briefly before proceeding.

## Coding Standards

When modifying or writing code, ALWAYS follow both bkit and Karpathy:

- Read existing code first; preserve architecture
- Generate the smallest possible diff; no unnecessary refactoring
- Never guess APIs; inspect existing code
- Follow naming: PascalCase (components), camelCase (functions), UPPER_SNAKE_CASE (constants), kebab-case (folders)
- DRY: Extract to common function on 2nd use
- SRP: One function, one responsibility
- No hardcoded values in cross-platform code; use `vim.fn.expand`, `vim.fn.stdpath`, `vim.fs.joinpath`
- Prefer table-form `vim.fn.system` over string-form for cross-platform safety

## Auto Commit & Push Policy

When work on a git-tracked repo is completed:

1. Run `git add -A`
2. Run `git commit -m "type: description"`
3. Run `git push`

**BUT only if the modified files are ALREADY tracked by git** (i.e., they existed in a prior commit).

- If a file exists only locally (was never committed), do NOT add, commit, or push it.
- Skip entirely if there are no changes to commit.

## Conventions

- Components: PascalCase (`UserProfile`)
- Functions: camelCase (`getUserById()`)
- Constants: UPPER_SNAKE_CASE (`MAX_RETRY_COUNT`)
- Files (component): PascalCase.tsx
- Files (utility): camelCase.ts
- Folders: kebab-case (`user-profile/`)

## Document Structure

```text
docs/
├── 01-plan/features/{feature}.plan.md
├── 02-design/features/{feature}.design.md
├── 03-analysis/{feature}.analysis.md
└── 04-report/features/{feature}.report.md
```

## Response Format

Include bkit status at end:

```text
bkit Status: {feature} | Phase: {phase} | Match Rate: {rate}%
Next: {suggested next action}
```

## Key Skills

| Skill                  | Purpose                                     |
| ---------------------- | ------------------------------------------- |
| `$pdca`                | PDCA workflow (plan, design, do, analyze, report) |
| `$bkit-rules`          | bkit detailed rules reference               |
| `$bkit-templates`      | PDCA document templates                     |
| `$development-pipeline` | 9-phase pipeline overview                   |
| `$code-review`         | Code quality analysis                       |
| `$plan-plus`           | Brainstorming-enhanced planning             |

## When the Task is Complete

When the requested task is done, stop. Do not continue improving unrelated code. Do not refactor, tidy, or optimize anything beyond what was asked.

## Web Search Citation Format

When using websearch_cited, ALWAYS format citations like Wikipedia at the end of your answer:

- Use numbered references like `[1]`, `[2]`, etc. inline in the text
- At the end of your answer, add a "Sources:" section listing all references with:
  - Number: `[1]`
  - Title of the page
  - Full URL

Example:

```text
The Eiffel Tower was completed in 1889 as the centerpiece of the World's Fair[1].

Sources:
[1] Eiffel Tower — Wikipedia
    https://en.wikipedia.org/wiki/Eiffel_Tower
```
