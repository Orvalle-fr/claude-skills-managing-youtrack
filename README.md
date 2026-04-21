# YouTrack Skill for Claude Code

A Claude Code skill to interact with any YouTrack instance via its REST API.

Inspired by [JetBrains' YouTrack skill](https://github.com/JetBrains/intellij-community/blob/master/.claude/skills/managing-youtrack/SKILL.md).

## Installation

**For a single project** — clone directly into your project's `.claude/skills` directory:

```bash
git clone https://github.com/Orvalle-fr/claude-skills-managing-youtrack \
  /your-project/.claude/skills/managing-youtrack
```

**Globally** — clone into your user-level Claude skills directory:

```bash
git clone https://github.com/Orvalle-fr/claude-skills-managing-youtrack \
  ~/.claude/skills/managing-youtrack
```

## Configuration

The skill requires two environment variables:

| Variable | Description |
|---|---|
| `YOUTRACK_URL` | Base URL of your YouTrack instance, without trailing slash (e.g. `https://youtrack.example.com`) |
| `YOUTRACK_TOKEN` | Permanent token for authentication |

### Generating a token

1. Log into your YouTrack instance
2. Go to your profile → **Account Security** → **Tokens**
3. Click **New token**, give it a name and the required scopes (`YouTrack` is enough for most operations)
4. Copy the generated token

### Setting the variables

**In your shell session:**

```bash
export YOUTRACK_URL=https://youtrack.example.com
export YOUTRACK_TOKEN=perm:your-token-here
```

**In a `.env` file** (do not commit this file):

```
YOUTRACK_URL=https://youtrack.example.com
YOUTRACK_TOKEN=perm:your-token-here
```

Then load it before starting Claude Code:

```bash
source .env && claude
```

**Via Claude Code settings** (`~/.claude/settings.json` or `.claude/settings.json`):

```json
{
  "env": {
    "YOUTRACK_URL": "https://youtrack.example.com",
    "YOUTRACK_TOKEN": "perm:your-token-here"
  }
}
```

> **Security:** never commit `YOUTRACK_TOKEN` to version control. Add `.env` to your `.gitignore`.

## Usage

Once installed and configured, invoke the skill in Claude Code:

```
/managing-youtrack
```

Then describe what you want to do in plain language, for example:

- *"Show me all open issues assigned to me in project MYPROJECT"*
- *"Create an issue: title 'Fix login bug', type Bug, priority High"*
- *"Add a comment to MYPROJECT-42: deployment is blocked"*
- *"Move MYPROJECT-7 to state In Review"*
- *"Log 2 hours on MYPROJECT-15"*

## Supported operations

| Category | Operations |
|---|---|
| Issues | Search, fetch, create, update |
| Custom fields | Read, update |
| Commands | Apply state/assignee changes |
| Comments | List, add, update, delete |
| Tags | List, add, remove |
| Links | Read, add via command |
| Work items | List, log time |
| Users & groups | Search users, list groups |
| Admin | Inspect project custom field schema |
