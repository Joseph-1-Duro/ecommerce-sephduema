# Git conventions

Use these conventions for every task and follow the installed `git-commit` skill when making commits.

## Agree on one scope

- Establish the branch's objective, included work, and completion criteria in the task discussion. A clearly scoped user request is the agreement; clarify meaningful ambiguity before expanding it.
- Each branch and pull request must address one objective. Supporting schemas, types, documentation, and relevant tests belong with that objective.
- Discuss unrelated features, fixes, or refactors separately and give each its own branch and pull request.

## Branches

- `main` is the integration branch. Never commit or push directly to it, and never force-push it. Changes reach `main` through pull requests.
- Check the current branch and working tree before starting. Create a new branch from `main` for each agreed task, using the latest `main` when a remote is available.
- Preserve existing uncommitted work. Only stage files or hunks that belong to the current task; unrelated local changes must stay out of its commits and pull request.
- Name branches `<type>/<short-kebab-case-description>`, using a commit type from the table below.

Examples:

```text
feat/storefront-product-list
fix/admin-panel-login
docs/git-conventions
chore/workspace-setup
```

## Commits

Follow Conventional Commits:

```text
<type>[optional scope]: <description>
```

| Type       | Use for                              |
| ---------- | ------------------------------------ |
| `feat`     | New functionality                    |
| `fix`      | Bug fixes                            |
| `docs`     | Documentation                        |
| `style`    | Formatting without behavior changes  |
| `refactor` | Restructuring without feature or fix |
| `perf`     | Performance improvements             |
| `test`     | Tests                                |
| `build`    | Build tooling or dependencies        |
| `ci`       | Continuous integration configuration |
| `chore`    | Maintenance                          |
| `revert`   | Reverting an earlier change          |

- Use an optional scope that identifies the affected area, such as `storefront`, `admin-panel`, or `tooling`.
- Write an imperative, present-tense description, such as "add" or "fix", and keep the subject under 72 characters.
- Keep each commit to one logical change within the branch's agreed objective.
- Inspect the actual diff and relevant untracked files before choosing a message. Stage specific files or hunks and review the staged diff before committing.
- Mark breaking changes with `!` after the type or scope, or a `BREAKING CHANGE:` footer explaining the impact. Reference issues with `Refs #123` or `Closes #123` when relevant.

Examples:

```text
feat(storefront): add product list
fix(admin-panel): validate product prices with Zod
docs: document branch and pull request conventions
```

Follow the skill's Git safeguards: never change Git configuration, commit secrets, or force-push `main`. Do not bypass hooks, run hard resets, or force-push other branches unless explicitly requested. If a hook fails, fix the cause and retry the commit; do not amend an earlier commit to bypass the failure.

## Pull requests

- Open a pull request from the task branch into `main`. Keep its changes focused on the one agreed objective.
- Use a Conventional Commit title that describes the final change. If the PR is squash-merged, use that title as the resulting commit subject.
- Use [the pull request template](.github/pull_request_template.md). Lead with the concrete problem and resulting behavior, state the agreed scope, and summarize validation and any material limitations.
- Run checks appropriate to the change using pnpm and report their actual results. Documentation-only changes need formatting and diff checks; code changes need the applicable lint, strict TypeScript, build, and relevant test checks.
- Complete review and required checks before merging through the pull request workflow.

## Task workflow

1. Discuss and establish one objective and its completion criteria.
2. Check the working tree, preserve existing work, and create a branch from `main`.
3. Implement only the agreed scope and run the applicable checks with pnpm.
4. Use the `git-commit` skill to review the diff, stage related changes, and create Conventional Commits on the task branch.
5. Push the task branch and open a focused pull request into `main`.
6. Address review feedback, pass required checks, and merge through the pull request.
