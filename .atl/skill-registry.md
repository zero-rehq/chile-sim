# Skill Registry

**Delegator use only.** Any agent that launches sub-agents reads this registry to resolve compact rules, then injects them directly into sub-agent prompts. Sub-agents do NOT read this registry or individual SKILL.md files.

See `_shared/skill-resolver.md` for the full resolution protocol.

## User Skills

| Trigger | Skill | Path |
|---------|-------|------|
| When writing TypeScript code - types, interfaces, generics | typescript | ~/.config/opencode/skills/typescript/SKILL.md |
| When creating a GitHub issue, reporting a bug, or requesting a feature | issue-creation | ~/.config/opencode/skills/issue-creation/SKILL.md |
| When creating a pull request, opening a PR, or preparing changes for review | branch-pr | ~/.config/opencode/skills/branch-pr/SKILL.md |
| When user wants to review PRs, analyze issues, or audit backlog | pr-review | ~/.config/opencode/skills/pr-review/SKILL.md |
| When creating a new skill, adding agent instructions, or documenting patterns for AI | skill-creator | ~/.config/opencode/skills/skill-creator/SKILL.md |
| When writing Python tests - fixtures, mocking, markers | pytest | ~/.config/opencode/skills/pytest/SKILL.md |
| When writing Go tests, using teatest, or adding test coverage | go-testing | ~/.config/opencode/skills/go-testing/SKILL.md |
| When building REST APIs with Django - ViewSets, Serializers, Filters | django-drf | ~/.config/opencode/skills/django-drf/SKILL.md |
| When writing C# code, .NET APIs, or Entity Framework models | dotnet | ~/.config/opencode/skills/dotnet/SKILL.md |
| When building AI chat features - breaking changes from v4 | ai-sdk-5 | ~/.config/opencode/skills/ai-sdk-5/SKILL.md |
| When working with Next.js - routing, Server Actions, data fetching | nextjs-15 | ~/.config/opencode/skills/nextjs-15/SKILL.md |
| When writing React components - no useMemo/useCallback needed | react-19 | ~/.config/opencode/skills/react-19/SKILL.md |
| When styling with Tailwind - cn(), theme variables, no var() in className | tailwind-4 | ~/.config/opencode/skills/tailwind-4/SKILL.md |
| When using Zod for validation - breaking changes from v3 | zod-4 | ~/.config/opencode/skills/zod-4/SKILL.md |
| When managing React state with Zustand | zustand-5 | ~/.config/opencode/skills/zustand-5/SKILL.md |
| When writing E2E tests - Page Objects, selectors, MCP workflow | playwright | ~/.config/opencode/skills/playwright/SKILL.md |
| When writing Angular components, services, templates, or architecture decisions | angular | ~/.config/opencode/skills/angular/SKILL.md |
| When reviewing technical exercises, code assessments, or candidate submissions | technical-review | ~/.config/opencode/skills/technical-review/SKILL.md |
| When building a presentation, slide deck, course material, or talk slides | stream-deck | ~/.config/opencode/skills/stream-deck/SKILL.md |
| When user says "judgment day", "review adversarial", "dual review" | judgment-day | ~/.config/opencode/skills/judgment-day/SKILL.md |
| When creating Jira tasks or tickets | jira-task | ~/.config/opencode/skills/jira-task/SKILL.md |
| When creating Jira epics for large features | jira-epic | ~/.config/opencode/skills/jira-epic/SKILL.md |
| When releasing, bumping version, or publishing homebrew projects | homebrew-release | ~/.config/opencode/skills/homebrew-release/SKILL.md |
| When building desktop apps with Electron | electron | ~/.agents/skills/electron/SKILL.md |
| When building mobile apps with React Native, Expo, or NativeWind | react-native | ~/.agents/skills/react-native/SKILL.md |
| When building Node.js backends with TypeScript | nodejs-backend-typescript | ~/.agents/skills/nodejs-backend-typescript/SKILL.md |
| When using Redis for performance, vector search, or caching | redis-development | ~/.agents/skills/redis-development/SKILL.md |
| When using MySQL for schema, indexing, query tuning, or migrations | mysql | ~/.agents/skills/mysql/SKILL.md |
| When working with Kafka, event streaming, or real-time pipelines | kafka-engineer | ~/.agents/skills/kafka-engineer/SKILL.md |
| When deploying to Vercel with token-based auth | vercel-cli-with-tokens | ~/.agents/skills/vercel-cli-with-tokens/SKILL.md |
| When refactoring components with boolean prop proliferation or designing reusable APIs | vercel-composition-patterns | ~/.agents/skills/vercel-composition-patterns/SKILL.md |
| When optimizing React/Next.js performance | vercel-react-best-practices | ~/.agents/skills/vercel-react-best-practices/SKILL.md |
| When building React Native/Expo mobile apps with performance optimization | vercel-react-native-skills | ~/.agents/skills/vercel-react-native-skills/SKILL.md |
| When implementing view transitions in React/Next.js | vercel-react-view-transitions | ~/.agents/skills/vercel-react-view-transitions/SKILL.md |
| When reviewing UI code for accessibility and design compliance | web-design-guidelines | ~/.agents/skills/web-design-guidelines/SKILL.md |
| When looking for installable skills or extending capabilities | find-skills | ~/.agents/skills/find-skills/SKILL.md |

## Compact Rules

### typescript
- Const Types Pattern: ALWAYS create const object first, then extract type via `type X = (typeof OBJ)[keyof typeof OBJ]`. NEVER direct union types.
- Flat Interfaces: one level depth, nested objects → dedicated interface. NEVER inline nested objects.
- Generics with defaults: `interface Result<T = string>`. Avoid `any` — use `unknown` + type narrowing.
- Readonly for immutable data: `readonly string[]` or `ReadonlyArray<string>`.
- Discriminated unions for state machines: `type State = { status: 'loading' } | { status: 'success'; data: T }`.

### issue-creation
- Blank issues are disabled — MUST use a template (bug report or feature request)
- Every issue gets `status:needs-review` automatically on creation
- A maintainer MUST add `status:approved` before any PR can be opened
- Questions go to Discussions, not issues

### branch-pr
- Every PR MUST link an approved issue — no exceptions
- Every PR MUST have exactly one `type:*` label
- Branch names MUST match: `^(feat|fix|chore|docs|style|refactor|perf|test|build|ci|revert)\/[a-z0-9._-]+$`
- Conventional commits only — no AI attribution, no Co-Authored-By

### pr-review
- ALWAYS list issues/PRs first before reviewing — even if user just asks "what's open"
- Use `gh issue list` / `gh pr list` for gathering, then `gh pr view` for details
- Evaluate: test coverage, edge cases, breaking changes, performance, security
- Leave structured review with: Summary, Issues Found, Suggestions, Verdict

### skill-creator
- Skill structure: `skills/{name}/SKILL.md` with optional `assets/` and `references/`
- Frontmatter required: name, description (with Trigger: line), license, metadata
- Body sections: Purpose, Rules (actionable), Patterns (with examples), References
- Keep skills focused — one concern per skill

### pytest
- Fixtures: prefer scope='session' for expensive setup, use conftest.py for sharing
- Markers: use @pytest.mark.parametrize for data-driven tests, @pytest.mark.slow for expensive
- Mocking: prefer monkeypatch over unittest.mock, use pytest-mock's mocker fixture
- Assert: use plain assert statements, not assertEqual etc.

## Project Conventions

| File | Path | Notes |
|------|------|-------|
| AGENTS.md | /home/zero-rehq/chile-sim/AGENTS.md | Index — operating manual for the Chile Sim government AI agent |
| CLAUDE.md | /home/zero-rehq/chile-sim/CLAUDE.md | Claude Code specific instructions for the vault |
| README.md | /home/zero-rehq/chile-sim/README.md | Game state, reading order, directory navigation |
| estado/AGENTS.md | /home/zero-rehq/chile-sim/estado/AGENTS.md | How to read game-state.json and estado snapshots |
| diplomacia/AGENTS.md | /home/zero-rehq/chile-sim/diplomacia/AGENTS.md | Diplomacy format rules and confidence markers |
| doctrina/AGENTS.md | /home/zero-rehq/chile-sim/doctrina/AGENTS.md | Doctrine: what is immutable vs adaptable |
