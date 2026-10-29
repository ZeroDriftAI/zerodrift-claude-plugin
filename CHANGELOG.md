# Changelog

## ZeroDrift

### 0.1.1

- **Listing links:** terms of use, support and documentation links in the plugin directory.
- **Validate skill:** loads its when-to-use guidance correctly, checks short Teams replies, and holds flagged content back from Google Drive writes and sharing.

### 0.1.0

First release. Validates drafts with ZeroDrift; never rewrites them.

- **Check before sending:** messages sent or drafted through the Gmail or Slack connector are checked first. A blocked message is stopped; warned and passed messages go through.
- **Check on request:** ask Claude to check a draft, or run `/zerodrift:validate`.
- **Result with findings:** `Passed`, `Warned`, or for a do-not-send verdict `Blocked` (the send was stopped) or `Flagged` (on-request check), then the next step, each flagged line with its number, a short quote and the rules it breaks (severity, policy), and the `job_id`. Lines past the first 20 are summarized by rule. Results also appear in the Activity feed in ZeroDrift Command.
- **Attribution:** Activity shows the signed-in user for every check, and the Claude model for on-request checks.
- **Never reported as passed when not checked:** saved drafts sent as-is, a missing sign-in, an unreachable service and an unavailable check are reported as not checked or as a hook error. Attachments and the original message of a forward are not checked.
- **Connection check:** `/zerodrift:status` confirms you are signed in and shows how many rules are active.
- **Sign in with ZeroDrift:** after installing, run `/mcp` and sign in to ZeroDrift in the browser. No API key to copy.
