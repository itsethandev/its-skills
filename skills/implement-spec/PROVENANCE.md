# Provenance: implement-spec

**Classification: Adapted.** Matt Pocock's integration-branch orchestration for implementing a spec's ticket graph.

## License scope

`LICENSE` contains the collection's MIT notice for original local material and modifications. Copied or adapted upstream material retains the applicable notices below; the local license does not replace them.

- [`licenses/Matt-Pocock-MIT.txt`](licenses/Matt-Pocock-MIT.txt): unmodified [Matt Pocock license](https://github.com/mattpocock/skills/blob/5863806dd4e15c63174bee4e7515a4256792ecfa/LICENSE). Applies to the adapted material identified below.

Retain this file and the applicable license files when distributing this directory. Attribution does not imply endorsement or authorship of unrelated local material.

## File evidence

| Local file | Classification | Pinned source                                                                                                                                                                              | Evidence and changes                                                                                                                                                          |
| ---------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `SKILL.md` | Adapted        | [Matt Pocock: `skills/engineering/implement-spec/SKILL.md`](https://github.com/mattpocock/skills/blob/5863806dd4e15c63174bee4e7515a4256792ecfa/skills/engineering/implement-spec/SKILL.md) | Retains the task graph, fresh subagents, background implementers, worktrees, merger subagents, TDD, review, and tracker completion procedure. Local changes are listed below. |

## Local adaptations

- Describe the skill without requiring the upstream planning skill names.
- Replace `/setup-matt-pocock-skills` with discovery of project-owned tracker guidance and a missing-guidance stop.
- Require authorization for remote writes rather than treating the workflow as permission to publish or close work.
- Record a fixed review baseline for the local `code-review` skill and refer to the PR target branch rather than assume `main`.
- Preserve existing work instead of resetting a worktree; explicitly commit ticket work before handing it to the merger.
- Serialize integration-branch merges to avoid concurrent writers.
- Merge and verify review fixes on the integration branch before completion.
- Limit cleanup to this run's merged, clean worktrees so unrelated or unfinished work is retained.
