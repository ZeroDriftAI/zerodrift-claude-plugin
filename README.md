# ZeroDrift

Checks drafts Claude writes against your company policies. Each check returns the outcome and next step, then each flagged line with a short quote and the rules it breaks (severity and policy), and the `job_id` to find the check in Activity, for example:

```
ZeroDrift: Flagged — fix before sending (3 issues on 2 lines: 2 do not send, 1 caution)
Line 3: "Your investments are guaranteed to outperform the market this year."
  [Do not send] Missing risk disclosure, Performance disclaimer missing (US Securities & Investment Communications)
Line 5: "Let's lock this in before the window closes."
  [Caution] Urgency pressure tactics (US Marketing Channel Mechanics)
job_id: 08d61777c883409f93890c6ca4a85524
```

Up to 20 lines are shown; any further lines are summarized by rule, and the full list is in Activity.

ZeroDrift validates only; it never rewrites your text. Claude explains each flagged line; it suggests wording only if you ask, and that wording is not checked by ZeroDrift. Results also appear in the Activity feed in ZeroDrift Command.

## What gets checked

- **Supported Gmail and Slack actions**, before they run: Gmail send, reply, forward, create draft and update draft; Slack send, draft and schedule. A `Blocked` message is stopped; `Warned` and `Passed` go through. Attachments, the original message of a forward, and saved drafts sent as-is are not checked. Other connectors and actions are not hook-checked.
- **Other channels, through Claude**: the `validate` skill lets Claude check text before it goes to Outlook, Microsoft Teams, Google Drive documents or the public internet, when it replies to an inbound message, or when you ask it to screen an inbound message or document. Claude decides when to run the check, and nothing is stopped automatically; a do-not-send verdict reads `Flagged`, and Claude holds the content until you decide.
- **Any draft on request**, with the command below or by asking Claude to check it.

## Setup

1. Install in Claude Code:

   ```
   /plugin install zerodrift --marketplace ZeroDriftAI/zerodrift-claude-plugin
   ```

2. Run `/mcp`, select **zerodrift**, and sign in to ZeroDrift in the browser. Approve access for your workspace.

Claude Code stores the sign-in in your operating system's secure store and refreshes it. To sign out, use **Clear authentication** in `/mcp`.

## Commands

| Command                       | What it does                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------- |
| `/zerodrift:validate <draft>` | Check a draft now                                                               |
| `/zerodrift:status`           | Confirm you are signed in and show how many rules are active; validates nothing |
| `/mcp`                        | Sign in, sign in again, or sign out                                             |

## Data sent

- **What:** the text being checked (subject and body for connector actions) and, for on-request checks, the Claude model in use. Recipients and attachments are not sent.
- **Where:** `https://mcp.zerodrift.ai`, over HTTPS, authenticated with your ZeroDrift sign-in. ZeroDrift records each check under your user and workspace.
- **When:** only for the checks above, including checks Claude runs on its own for the channels listed in What gets checked. Other replies are not sent.
- **Retention:** ZeroDrift keeps submitted text for seven days by default, per your ZeroDrift agreement.
- **Returned to Claude:** the outcome and, for each finding, its severity, rule name, policy and the quoted text from your draft. No scores, model reasoning or suggested rewrites.

If a message can't be checked (not signed in, service unreachable, or validation unavailable), Claude Code shows a hook error or a not-checked notice and the message goes through.

## Where it runs

Claude Code (terminal, IDE extensions and the desktop app's Code tab). In claude.ai and the Claude desktop app, add `https://mcp.zerodrift.ai/mcp` as a custom connector to check drafts on request; sends are not checked there. Cowork is not supported yet.

## Support

[support@zerodrift.com](mailto:support@zerodrift.com)
[https://zerodrift.com](https://zerodrift.com)
