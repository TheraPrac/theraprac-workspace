# Workspace Cursor Rules

These rules apply to all AI agents operating in this workspace across all projects.

## Network and Authentication Restrictions

### No Auto-Running Authenticated Commands
- **Never** automatically execute commands that require authentication (GitHub CLI, AWS CLI with credentials, etc.)
- **Always** request explicit user approval before running authenticated commands
- **Never** assume credentials are available or should be used

### No GitHub CLI Usage
- **Never** run `gh` commands automatically
- **Never** use GitHub CLI for fetching issue content, closing issues, or commenting
- All GitHub interactions must be initiated by the user using provided helper scripts

### No Network API Calls
- **Never** make direct network calls to external APIs (GitHub, Jira, etc.)
- **Never** fetch issue content, PR data, or repository information from APIs
- All required information must be provided by the user

## Agent Role and Authority

### Act as Collaborator, Not Executor
- The AI agent is a **collaborative partner**, not an autonomous executor
- Provide code, fixes, and documentation
- **Never** take actions that change external state without explicit user direction

### Explicit User Authority Required
- **State-changing actions** require explicit user approval:
  - Git commits (unless explicitly requested)
  - Pushing to remote repositories
  - Closing GitHub issues
  - Commenting on PRs
  - Creating branches
  - Merging branches
  - Any GitHub state changes

### User Maintains Control
- The user maintains full control over:
  - Repository state
  - GitHub issue/PR management
  - Deployment decisions
  - External service interactions

## Memory and State Management

### GitHub as System of Record
- **GitHub is the agent's memory** - Issues and PRs are the canonical source of truth
- **Never create durable markdown files or local artifacts as memory**
- All agent output is ephemeral and intended to flow back into GitHub
- The agent does not maintain state outside of GitHub context provided by the user
- Prefer deterministic, explicit workflows over implicit automation

### No Local Artifacts
- **Never** create `.md` files, summary files, or other artifacts as memory
- **Never** persist state locally that should be in GitHub
- All summaries, notes, and documentation should be emitted in chat only
- Users copy/paste agent output into GitHub via helper scripts or manually

## Issue and PR Management

### Issue Content
- Issue content must be **provided by the user**
- Do not attempt to fetch issue content from GitHub
- Work with the information provided

### Issue Closure
- **Never** close issues automatically
- Use the provided helper script: `scripts/github/close-issue.sh`
- Only close issues when explicitly directed by the user
- Helper scripts accept summary text via STDIN (no file requirements)

### PR Comments
- **Never** comment on PRs automatically
- Use the provided helper script: `scripts/github/comment-pr.sh`
- Only comment when explicitly directed by the user
- Helper scripts accept summary text via STDIN (no file requirements)

## Git Workflow

### Commits
- Follow the one-issue-per-commit rule (see BugFix Agent contract)
- Use clear, descriptive commit messages
- Reference issue numbers in commit messages
- Never skip hooks (no `--no-verify` flag)
- **Commits must be executed outside the sandbox** - The sandbox environment restricts git operations. When committing, use `required_permissions: ['all']` or execute commits manually outside the AI assistant context

### Branches
- Only create branches when explicitly requested
- Use descriptive branch names
- Never force-push without explicit user approval

## Project-Specific Considerations

These rules apply across all workspace projects:
- `theraprac-api` (Go backend)
- `theraprac-web` (Next.js frontend)
- `theraprac-infra` (Terraform infrastructure)
- `ziti-source` (Go networking library)

Each project may have additional conventions documented in their respective directories, but these workspace rules take precedence for AI agent behavior.

## Helper Scripts

Helper scripts are provided in `scripts/github/` for common GitHub operations:
- `close-issue.sh` - Close issues with summary comments
- `comment-pr.sh` - Comment on PRs with issue references

These scripts are designed to be:
- Safe and minimal
- Readable and maintainable
- Context-aware (use current git context, not hardcoded repos)
- Accept summary text via STDIN (no file requirements)

Agents should **suggest** using these scripts when appropriate, but **never** execute them automatically without user approval.

**Usage Pattern**:
- Agent emits summary in chat (ephemeral)
- User copies summary and pipes to script: `echo "<summary>" | scripts/github/close-issue.sh <n>`
- Summary flows back into GitHub, completing the cycle

