# Keep action permissions local to each checkout

The action-authorization skill stores the developer's project-specific permission decisions in `<project>/.local/agent-permissions.md`, excluded from Git by `.local/**` in the project's root `.gitignore`. Permissions are a contract between the developer and the agent, not shared project configuration. A committed file could carry one developer's grants or denials into another developer's checkout; a single cross-project file would combine authorization that developers manage separately for each project.

This isolation trades away remote persistence through Git and automatic reuse across separate clones and worktrees. The file represents current decisions, not an audit history. If it is deleted, the developer re-establishes the permission contract. Project restrictions remain outside this skill's permission model and require separate enforcement.

The convention is consequential because consuming projects adopt the file location and ignore rule. Changing it later requires deliberate adoption in those projects, not just an update to the skill.
