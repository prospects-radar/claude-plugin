# ProspectsRadar for Claude

Work your [ProspectsRadar](https://prospectsradar.com) pipeline from Claude. ProspectsRadar finds B2B companies that match your ideal customer profile, scores them, tracks their buying signals and maps the buying committee. This plugin connects Claude to your account and adds five sales workflows on top of that data.

## Skills

| Skill | What it does |
|---|---|
| `daily-briefing` | New buying signals, tasks due, and the prospects worth acting on today |
| `prospect-brief` | One-page brief on one prospect: fit, timing, buying committee, opening angle |
| `pipeline-review` | Strong prospects nobody follows, followed prospects that went quiet, cleanup proposals |
| `plan-outreach` | Picks stakeholders, drafts messages, and creates outreach tasks in ProspectsRadar |
| `tune-icp` | Diagnoses and changes the ideal customer profiles that drive discovery and scoring |

## Connection

The plugin uses one remote MCP server, `https://app.prospectsradar.com/mcp`. It runs nothing on your machine and contains no code, only skill instructions.

The first time Claude uses a tool, you sign in to ProspectsRadar and approve the scopes on its consent screen (OAuth 2.1 with PKCE). Claude then sees only the account and products your login can see. To revoke access, remove the connector in Claude. In Claude Code, sign in with `claude mcp login prospectsradar`.

You need a ProspectsRadar account. Start a trial at https://prospectsradar.com.

## What it changes in your account

Every tool that writes (interest states, tasks, ICPs, products, companies) previews by default (`dry_run: true`). The skills show you the preview and commit only after you confirm. `review_profile` charges account tokens; the skill tells you the cost first. The plugin never sends email or LinkedIn messages: outreach lands as tasks in ProspectsRadar.

## Data

Data flows only between Claude and ProspectsRadar. See the [privacy policy](https://app.prospectsradar.com/privacy).

## Support

https://prospectsradar.com/contact · Documentation: https://docs.prospectsradar.com
