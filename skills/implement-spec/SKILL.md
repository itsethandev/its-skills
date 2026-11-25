---
name: implement-spec
description: "Implement a spec's ticket graph on a single integration branch using parallel subagents."
disable-model-invocation: true
---

You have been provided a spec. This spec should have tickets associated with it, describing how to implement the spec.

Before reading tracker issues, find and read the project's issue-tracker guidance through its README documentation index and agent instructions. Follow the configured tracker operations and locations. If required guidance is missing or ambiguous, explain the gap and ask how to proceed.

The goal is the entire spec implemented on a single **integration branch**, with every ticket resolved the way the issue tracker closes work.

The tickets are not a list of steps. They are a **task graph** with blocking relationships between them. This means there is always a **frontier** of tickets which are ready to be grabbed.

Start every subagent with a fresh context window.

Communication to and from subagents should be sparse. Communicate primarily through **context pointers**: to the spec, tickets, research notes, and previous commits. Don't duplicate information already available via pointers.

**Implementer subagents** should be run in the background where possible for maximum concurrency.

Pushing branches, publishing or updating PRs, and changing tracker records require authorization. If a required action is not authorized, ask before performing it.

## Steps

1. Read the spec and tickets to understand the task graph.

2. (optional) Use an **exploration subagent** to conduct any exploration required by the tickets - relevant codebase files or external documentation. Ensure the exploration subagent can save files - it should save its markdown notes in a directory outside the repo, accessible by all future subagents. This lets **implementer subagents** focus on implementation rather than exploration.

3. Create the integration branch and record its starting commit as the review baseline. If the issue tracker closes work through PRs, or the user asks for one, open a draft PR after the first merge in step 5 (a branch with no commits ahead of its target branch can't open one), marked as closing the spec and tickets.

4. Use a fresh **implementer subagent** for each ticket, each in its own worktree on its own branch. Each implementer subagent:
   - confirms its worktree is based on the integration branch before starting; if not, preserves existing work and recreates the task worktree from the integration branch;
   - calls the Skill tool with `tdd` to build the ticket;
   - commits its work and merges the integration branch tip into its own branch before reporting done.

5. Once an **implementer subagent** completes, merge its work to the integration branch with a **merger subagent**. Serialize these merges so only one merger changes the integration branch at a time.

6. If this changes the **frontier** of available tickets, kick off more **implementer subagents** to work on the new tickets. This allows for maximum concurrency.

7. Once all tickets are complete, call the Skill tool with `code-review` on the integration branch, using the recorded starting commit as the fixed point. Fix all issues raised by the code review in a single fresh **implementer subagent**, then merge and verify those fixes on the integration branch.

8. If a draft PR exists, mark it ready for review. Otherwise, resolve each ticket the way the issue tracker closes work, and report the integration branch.

9. Clean up all **implementer subagent** worktrees created by this run once their work is merged and they have no uncommitted or untracked files. Preserve and report any worktree with unmerged or uncommitted work.
