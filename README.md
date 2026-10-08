# Jouleo skills for AI apps

Skills that teach Claude, Codex and other AI agents how to run a UK solar, battery and EV installer's day in [Jouleo](https://jouleo.co.uk), the CRM built for renewable installers.

With the Jouleo connector and these skills, your AI app can tell you what needs doing today, turn an email or call into an enquiry, book surveys and installs without crew clashes, and move jobs on — acting as you, with your permissions in Jouleo.

## Install the skill

One line, for Claude Code, Codex, Cursor and [40+ other agents](https://github.com/vercel-labs/skills):

```sh
npx skills add helix8-io/jouleo-skills
```

Or ask your AI app:

> Install the Jouleo skill by running `npx skills add helix8-io/jouleo-skills`.

**Codex** can also install it itself: ask it to use `$skill-installer` with `https://github.com/helix8-io/jouleo-skills/tree/main/skills/jouleo-board`.

**Claude.ai and the Claude desktop app:** download the skill from Jouleo (Connected apps → Skills) and upload it in Settings → Capabilities → Skills. Team and Enterprise admins can add it for everyone under Organization settings → Skills.

## Connect Jouleo

The skill works with the Jouleo connector, an MCP server at your company's own Jouleo address. You'll find your address, with step-by-step instructions for each app, in Jouleo under **Connected apps**. It looks like:

```
https://<your-company>.jouleo.co.uk/mcp
```

- **Claude:** Settings → Connectors → Add custom connector, paste the address, then sign in to Jouleo.
- **ChatGPT:** with developer mode on, create an app with the address and choose OAuth.
- **Codex:** `codex mcp add jouleo --url <address>`, then `codex mcp login jouleo`.
- **Claude Code:** `claude mcp add --transport http jouleo <address>`, then run `/mcp` and choose Authenticate.

You sign in with your normal Jouleo account and choose **Everything I can do** or **Look only**. You can see and revoke every connection in Jouleo, and admins can switch AI apps off for the whole company.

## What's inside

| Skill | What it does |
|---|---|
| [`jouleo-board`](skills/jouleo-board/SKILL.md) | The daily board review, turning emails and calls into complete enquiries, booking surveys and installs around crew clashes, moving jobs between stages and explaining what blocks them, notes and archiving. |

## About Jouleo

Jouleo is the job tracker and CRM for UK solar PV, battery storage and EV charger installers — enquiries, quotes, designs, scheduling, MCS and DNO paperwork in one place. Built by [Helix8](https://helix8.io). Find out more at [jouleo.co.uk](https://jouleo.co.uk).

## Licence

MIT — see [LICENSE](LICENSE).
