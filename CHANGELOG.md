# Changelog

Each target has its own version. A release publishes only the targets whose version is new.

## Claude

### 0.1.6

- **Icon:** new ZeroDrift icon.

### 0.1.5

- **README:** support email is support@zerodrift.ai.

### 0.1.4

- **Validate skill:** without the plugin's hooks, checks Gmail and Slack drafts before sending too.
- **README:** Claude-only setup and check scope.

### 0.1.3

- **Skills:** sign-in steps cover both Claude Code and Codex.

### 0.1.2

- **README:** the send check also runs on other connectors' `send_message`, `reply`, `forward`, `create_draft` and `update_draft` tools.

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

## Codex

### 0.1.6

- **Icon:** new ZeroDrift icon.

### 0.1.5

- **Listing:** full description, capabilities, support link and icon.
- **README:** support email is support@zerodrift.ai.

### 0.1.4

- **Validate skill:** Codex checks Gmail drafts with ZeroDrift before sending.

### 0.1.3

First release. ZeroDrift for Codex from `ZeroDriftAI/zerodrift-codex-plugin`.

- **Check before sending:** Gmail sends, drafts, draft updates and forwards are checked before they run. A blocked message is stopped.
- **Check on request:** ask Codex to check a draft with ZeroDrift.

## OpenAI directory

### 0.1.6

- **Icon:** new ZeroDrift icon.
- **Skills:** check drafts only when asked; sign-in steps for ChatGPT and Codex.

### 0.1.5

- **Review:** clearer expected behavior for each test case. Available in the US.

### 0.1.4

First release for the ChatGPT and Codex plugin directory. Checks drafts on request; doesn't block sends.
