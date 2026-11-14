# ItsSkills

ItsSkills is an collection of reusable agent skills for general work, software engineering, and learning.

## Skill catalog

Use these identifiers with `--skill` when installing individual skills. Each link opens the skill's instructions. Invocation metadata support depends on the consuming agent.

Each skill bundle lives under `skills/<skill>/`. Choose skills by their purpose and invocation conditions.

Skills are divided into model invoked skills and manually invoked skills. The model can load model invoked skills when their invocation conditions match the task, while manually invoked skills must be explicitly invoked by the user.

### Model invoked

| Skill                                                        | Purpose                                                                           |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------- |
| [action-authorization](skills/action-authorization/SKILL.md) | Resolve permission for consequential actions and record scoped grants or denials. |
| [alignment](skills/alignment/SKILL.md)                       | Stress-test a plan, decision, or idea with the user.                              |
| [code-review](skills/code-review/SKILL.md)                   | Review changes against repository standards and the originating spec in parallel. |
| [codebase-design](skills/codebase-design/SKILL.md)           | Design deeper modules, clearer interfaces, and testable boundaries.               |
| [decision-records](skills/decision-records/SKILL.md)         | Record consequential decisions as lightweight ADRs.                               |
| [diagnosing-bugs](skills/diagnosing-bugs/SKILL.md)           | Diagnose bugs and performance regressions.                                        |
| [domain-language](skills/domain-language/SKILL.md)           | Build and sharpen a project's domain language and glossary.                       |
| [frontend-design](skills/frontend-design/SKILL.md)           | Design or reshape frontend pages, components, and interactive prototypes.         |
| [pr](skills/pr/SKILL.md)                                     | Write a pull request body.                                                        |
| [propose-first](skills/propose-first/SKILL.md)               | Propose a solution and wait for approval before implementing.                     |
| [prototype](skills/prototype/SKILL.md)                       | Build a throwaway artifact to answer a design question.                           |
| [repitch](skills/repitch/SKILL.md)                           | Re-explain a message or part of one.                                              |
| [research](skills/research/SKILL.md)                         | Investigate primary sources and save findings as Markdown in the repo.            |
| [tdd](skills/tdd/SKILL.md)                                   | Build features or fix bugs with test-driven development.                          |
| [verifying-work](skills/verifying-work/SKILL.md)             | Prove results, establish feedback loops, and maintain verification guidance.      |
| [wizard](skills/wizard/SKILL.md)                             | Generate an interactive Bash wizard for steps only a human can perform.           |
| [writing](skills/writing/SKILL.md)                           | Write and revise technical prose for humans and coding agents.                    |

### Manually invoked

| Skill                                                                          | Purpose                                                                                                            |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| [implement](skills/implement/SKILL.md)                                         | Implement work from a spec or set of tickets.                                                                      |
| [improve-codebase-architecture](skills/improve-codebase-architecture/SKILL.md) | Find module-deepening opportunities, present an HTML report, and align on a choice.                                |
| [ingest-document](skills/ingest-document/SKILL.md)                             | Extract project-relevant proposals from a document and ask which to adopt.                                         |
| [pause-work](skills/pause-work/SKILL.md)                                       | Pause safely and save a resume checkpoint.                                                                         |
| [retro](skills/retro/SKILL.md)                                                 | Conduct a retrospective on a coding session.                                                                       |
| [to-tickets](skills/to-tickets/SKILL.md)                                       | Break a plan, spec, or conversation into tracer-bullet implementation tickets with explicit blocking dependencies. |
| [to-questionnaire](skills/to-questionnaire/SKILL.md)                           | Turn unresolved decisions into a questionnaire for someone with the missing knowledge.                             |
| [to-spec](skills/to-spec/SKILL.md)                                             | Synthesize the conversation into a spec and publish it to the issue tracker.                                       |
| [wayfinder](skills/wayfinder/SKILL.md)                                         | Map work spanning multiple agent sessions into decision tickets and resolve them in sequence.                      |

## Installation

The repository follows Vercel's skills CLI source layout and can be consumed as a source-only Nix flake input. Both methods use the same complete skill bundles. The unpinned examples below target main; select a revision containing the skills you need.

### Individual skills

Choose any skill or combination by identifier:

```sh
npx skills add ItsEthanDev/its-skills --skill writing codebase-design
```

### Nix

Add a source-only input to your configuration flake:

```nix
inputs.its-skills = {
  url = "github:ItsEthanDev/its-skills";
  flake = false;
};
```

For installation of skills through Home Manager, pass your flake `inputs` through `extraSpecialArgs` and point its skill discovery at the source directory. Replace `my-coding-agent` with your preferred agent harness. Refer to home manager options to determine the exact interface for your setup.

```nix
{ inputs, ... }: {
  programs.my-coding-agent = {
    enable = true;
    settings.skills = [ "${inputs.its-skills}/skills" ];
  };
}
```

The directory contains every skill bundle. To select individual skills, use their complete directory paths and include any skills they require:

```nix
settings.skills = [
  "${inputs.its-skills}/skills/writing"
  "${inputs.its-skills}/skills/codebase-design"
];
```

### Installation notes

- The CLI commands leave target-agent selection to the CLI prompts and use project-local installation by default. Add `--global` for user-wide installation or `--agent <agent>` to select a target explicitly.
- Invocation metadata support depends on the consuming agent.

## Project documentation

- [Quickstart](docs/quickstart.md): prerequisites and local verification.
- [Guiding Principles](PRINCIPLES.md): guiding qualities for project work.
- [Glossary](GLOSSARY.md): agreed project terms.
- [Action permission storage decision](docs/adr/0001-checkout-local-action-permissions.md): rationale and trade-offs for checkout-local permission records.

## Agent documentation

- [Agent instructions](AGENTS.md): conditional pointers and commit behavior.
- [Issue tracker](docs/agents/issue-tracker.md): GitHub operations and wayfinding.
- [Triage labels](docs/agents/triage-labels.md): implementation-role mappings.
- [Domain guidance](docs/agents/domain.md): active terminology practice and maintenance.

## Acknowledgments

ItsSkills draws on ideas and adapted guidance from:

- [Matt Pocock's skills](https://github.com/mattpocock/skills), published under the [MIT license](https://github.com/mattpocock/skills/blob/24fe0ef7737efae15c87225755e9f6f5965e4888/LICENSE). Copyright (c) 2026 Matt Pocock.
- [Lauren Tan (Poteto)'s Pstack](https://github.com/cursor/plugins/tree/main/pstack), published under the [MIT license](https://github.com/cursor/plugins/blob/e43c7ee26e0038c6c1fa8380dd34ce86ff94cb2a/pstack/LICENSE). Copyright (c) 2026 Lauren Tan.
- [Anthropic's frontend design skill](https://github.com/anthropics/skills/tree/main/skills/frontend-design), published under the [Apache License 2.0](https://github.com/anthropics/skills/blob/dbd4588f9e1033efb41dad4bef2f7947c8993d44/skills/frontend-design/LICENSE.txt).
