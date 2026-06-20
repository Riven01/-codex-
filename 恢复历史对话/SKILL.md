---
name: 恢复历史对话
description: Use when the user asks to restore Codex historical conversations, recover hidden sessions after switching providers, synchronize provider metadata, run codex-provider-sync, or says 恢复历史对话 / 恢复历史会话 / 找回历史对话 / 切换 provider 后恢复对话. This skill runs the locally installed codex-provider-sync CLI and verifies the result.
---

# 恢复历史对话

## Purpose

Restore Codex historical conversation visibility after a provider switch by running the locally installed `codex-provider-sync` CLI.

## Workflow

1. Announce that this operation updates `~/.codex` session visibility metadata and creates a backup automatically.
2. Prefer the installed Windows shim:
   - `$env:APPDATA\npm\codex-provider.cmd`
   - If direct command lookup works, `codex-provider` is also acceptable.
3. Run:
   ```powershell
   & "$env:APPDATA\npm\codex-provider.cmd" sync
   ```
4. Run a verification pass:
   ```powershell
   & "$env:APPDATA\npm\codex-provider.cmd" status
   ```
5. Report the backup path, number of rollout files updated, number of SQLite rows updated, and whether `status` shows the current provider consistently across sessions.

## Safety Notes

- `sync` should be used for normal recovery. It does not switch login accounts; it synchronizes historical conversation metadata to the current provider.
- If the user asks to switch providers and recover in one step, use:
  ```powershell
  & "$env:APPDATA\npm\codex-provider.cmd" switch <provider-id>
  ```
- Do not run `restore <backup-dir>` unless the user explicitly asks to roll back.
- If `status` or `sync` reports `encrypted_content`, explain briefly that conversation lists may become visible, but continuing or compacting old encrypted sessions can still fail with `invalid_encrypted_content`.
- If the CLI is missing, check whether the source exists at the current workspace `work/codex-provider-sync-main`; otherwise tell the user the tool needs to be installed first.
