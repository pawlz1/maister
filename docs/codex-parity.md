# Codex functional parity

## Acceptance contract

The Codex variant must preserve the current source plugin's functionality, not
just its files. `plugins/maister/` remains the source of truth. Generated Codex
files must never be edited directly. Claude Code and Copilot behavior must not
regress. Platform-specific tools, model names and invocation syntax may differ;
workflow semantics, artifacts, decisions and safety guarantees may not.

Implementation branch: `add-codex`. Commit each coherent change after its relevant
tests pass. Static validation, runtime loading and model-driven acceptance are
separate evidence categories. Missing live evidence is never a passing result.

## Baseline

Source commit: `a1f05e0` (manifest version `2.2.6`). The source contains 17 skills,
25 agent definitions, six command wrappers and 63 skill files, including shared
references, dashboard assets and the visual companion server.

## Skills

All entries below require source coverage, adapted instruction validation and a
model-driven acceptance scenario. Status starts as **pending**.

| Source skill | Acceptance scenario |
|---|---|
| codebase-analyzer | Parallel exploration and reporter synthesis |
| development | Adaptive phases, characteristic detection, spec, plan, implementation and verification |
| docs-manager | Document operations, index maintenance and project instruction integration |
| implementation-plan-executor | Dependency waves, disjoint file ownership, sequential override and progress logging |
| implementation-verifier | Specialist reports, aggregation and no automatic fixing |
| init | Standards discovery, scaffold, configuration and existing-project choices |
| migration | Migration types, risk, rollback planning and documentation |
| mockup-studio | HTML preview, design resources, ASCII selection and no-Node fallback |
| orchestrator-framework | Shared state, delegation, gates, timestamps and artifact contracts |
| performance | Bottleneck analysis, optional profiling and full delivery workflow |
| product-design | Interactive exploration, alternatives, convergence, prototypes and handoff |
| quick-bugfix | Failing test, fix, passing test and complexity escalation |
| quick-dev | Direct implementation with standards and compliance verification |
| quick-plan | Planning-only exploration, approval, standards checklist and post-implementation verification |
| research | Planning, information gathering, synthesis and optional solution design |
| standards-discover | Parallel discovery, confidence tiers, scopes and optional external inputs |
| standards-update | Manual/context updates, cross-project import and user selection |

## Commands

Each command must have an explicit Codex skill entry point with equivalent
arguments and delegation: `work`, `reviews-code`, `reviews-pragmatic`,
`reviews-production-readiness`, `reviews-reality-check`, `reviews-spec-audit`.
The unified entry point must classify new tasks, read issue context and resume
existing task paths. No routing may bypass the selected workflow.

## Agents

The build must preserve all 25 source roles and their complete instructions:
ascii-mockup-generator, bottleneck-analyzer, code-quality-pragmatist,
code-reviewer, codebase-analysis-reporter, docs-operator, e2e-test-verifier,
gap-analyzer, html-companion-writer, implementation-completeness-checker,
implementation-planner, information-gatherer, production-readiness-checker,
project-analyzer, reality-assessor, research-planner, research-synthesizer,
solution-brainstormer, solution-designer, spec-auditor, specification-creator,
task-classifier, task-group-implementer, test-suite-runner, user-docs-generator.
The docs-operator must preload docs-manager. Exploration roles used dynamically
by codebase-analyzer must also have a working dispatch path.

## Cross-cutting acceptance

| Capability | Required evidence | Status |
|---|---|---|
| Mandatory gates | No progression without an explicit user response, including auto mode | pending |
| Task tracking | IDs, statuses, dependencies and owners survive restart | pending |
| Resume/compaction | State reload selects the correct next phase and preserves decisions | pending |
| Parallel execution | Same-turn fan-out, dependency ordering and collision avoidance | pending |
| Safety | Destructive commands denied; malformed/missing input cannot bypass guard | pending |
| Standards | Index plus applicable files read; compliance checked after implementation | pending |
| TDD | Red and green evidence, full test suite and unrelated regression reporting | pending |
| Artifacts | Existing paths, schemas, summaries, timestamps and work logs preserved | pending |
| Dashboard/reports | Original assets, state projections, HTML companions and HTML-off mode | pending |
| Visual design | HTML/ASCII, bound mockups, development handoff and visual fidelity checks | pending |
| Playwright | Pinned MCP configuration, live E2E evidence and documentation screenshots | pending |
| Failure handling | Retry counters, user-confirmed rollback, blocked states and recovery | pending |
| Distribution | Manifest parsing, local installation, resource resolution and hook trust | pending |
| Existing variants | Copilot regeneration and validation; source behavior unchanged | pending |

## Validation layers

1. Deterministic generator and coverage tests, including all resources and roles.
2. Adapter unit tests: task dependency/state persistence, hook protocol and denial.
3. Actual Codex package/configuration parsing and isolated installation checks.
4. Model-driven acceptance in disposable fixture projects for every scenario above.
5. Regression validation for the original and Copilot variants.

Never mark the port complete before all layers have evidence. A CLI parser test
does not establish workflow correctness. Non-interactive execution must pause
at decisions rather than manufacture approval.

## Local environment discovered

Python 3.9.6 is available. Codex was found outside PATH at
`/Users/pawlz/.codex/plugins/.plugin-appserver/codex-cli/bin/codex`, version
`0.162.0-alpha.17.2`. Node.js is not available in the inspected PATH. Do not modify
personal Codex configuration or authentication to test this plugin; use an
isolated CODEX_HOME for installation/parser tests.