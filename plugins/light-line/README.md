# Light_line 插件

这是 Light_line 的可安装插件本体，向 `pm-skills` 的目录理念对齐：

- `skills/`：18 个技能
- `commands/`：5 个命令模板
- `workflows/`：5 份工作流说明
- `hooks/`：4 个生命周期 hook
- `.codex-plugin/plugin.json`：插件 manifest

## 安装

插件源码位于：

```text
plugins/light-line
```

本地 marketplace 路径：

```text
.agents/plugins/marketplace.json
```

在 Codex 中可先把本地 marketplace 加进去，再安装插件：

```powershell
codex plugin marketplace add C:\Users\Admin\Light_line\.agents\plugins
codex plugin add light-line@personal
```

## 目录

- `commands/`：可复用的 pm-skills 风格模板
- `hooks/`：SessionStart、UserPromptSubmit、PreToolUse、PostToolUse
- `skills/`：围绕前端、窗口治理、BFF/RAG、交付审查等能力
- `workflows/`：对命令背后的落地流程做补充说明

## 边界

- `commands/` 不会被 Codex 自动注册成原生 slash command
- `hooks/hooks.json` 是插件默认 hook 入口
- `skills/` 才是插件能力主体
