# Light_line 插件展示页

这是一个零依赖、本地可打开的 Light_line 插件展示与打包页面。

## 使用方式

直接双击或在浏览器中打开：

`C:\Users\Admin\Light_line\index.html`

页面会展示当前 Light_line 插件的 skills、commands、hooks，并允许你勾选需要的能力后下载 ZIP 包。

## 重要边界

- 完整包会尽量保留 `C:\Users\Admin\Light_line\plugins\light-line` 的插件源码结构。
- 自定义包只包含当前勾选的 skills、commands、hooks，以及必要的插件 manifest、README、索引和选择清单。
- hooks 只有在 Codex 插件启用、用户信任并具备 Node 运行环境时才会真实进入生命周期。
- commands 是 pm-skills 风格流程模板；Codex 当前不会把插件 `commands/` 自动注册成原生 slash command。

## 设计原则

页面采用 Newsprint 风格：强网格、黑白高对比、红色少量强调、零圆角、硬边框、报刊式信息密度。它的目标不是“看上去像插件”，而是让插件的能力关系、安装边界和可下载内容都可被看见、筛选、裁剪。
