# -codex-

可以找回你的 Codex 历史对话记录。

## 恢复历史对话 Skill

这是一个 Codex skill，用于在切换 provider 后，通过本地已安装的 `codex-provider-sync` CLI 同步 Codex 历史会话 metadata，让隐藏的历史对话重新可见。

## 安装

1. 下载或克隆本仓库。
2. 将 `恢复历史对话` 文件夹复制到 Codex skills 目录：
   - Windows: `%USERPROFILE%\.codex\skills\恢复历史对话`
   - macOS/Linux: `~/.codex/skills/恢复历史对话`
3. 重启 Codex，或重新加载 skills。

## 前置条件

此 skill 只封装操作流程，不自带 `codex-provider-sync` CLI。目标机器需要已安装并可运行：

```powershell
codex-provider status
```

在 Windows 上，skill 会优先使用：

```powershell
& "$env:APPDATA\npm\codex-provider.cmd" sync
```

## 使用方式

在 Codex 中说：

```text
使用 恢复历史对话 skill 帮我恢复切换 provider 后隐藏的历史会话
```

或：

```text
找回历史对话
```

## 包含文件

- `恢复历史对话/SKILL.md`
- `恢复历史对话/agents/openai.yaml`

