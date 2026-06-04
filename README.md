# prd-writer

> **A conversational PRD-writing skill for Claude Code.** It interviews you from the user, business, and technical angles, aligns on a concise concept doc, then produces an implementation-ready Chinese PRD — flows, states, fields, copy, and edge cases included.
>
> **一个会「带你聊」的 Claude Code 写 PRD 技能。** 从用户、业务、技术三个视角访谈，先对齐一版精简概念稿，再产出可直接落地的中文 PRD —— 流程、状态、字段、文案、异常一应俱全。

一个 Claude Code 技能（skill）：引导式产品需求发现对话，分阶段产出标准中文 PRD 文档。

它不会一上来就甩给你一份完整 PRD，而是先从**用户 / 业务 / 技术**三个视角做诊断，确认页面结构与导航，输出一份简洁的**概念 PRD** 与你对齐、冻结范围，再生成包含流程、状态、字段、文案与异常处理的**落地版 PRD**。

适用场景：描述一个产品想法、功能需求、改进点、vibe-coding 项目、MVP 范围，或直接说「写个 PRD / 需求文档 / 产品需求 / 功能规格」。

## 安装

两种方式任选其一。

### 方式一：一行命令（终端，需已装 Node）

```
npx skills add https://github.com/Panix22/prd-writer-skill --skill prd-writer
```

借助 [`skills`](https://www.npmjs.com/package/skills) 工具一行装好，自动放进你的 skills 目录。

### 方式二：Claude Code 官方插件（无需任何额外工具）

在 Claude Code 里依次执行：

```
/plugin marketplace add Panix22/prd-writer-skill
/plugin install prd-writer@prd-writer-skill
```

第一条把本仓库登记为插件市场（marketplace），第二条从中安装 `prd-writer`。好处是支持 `/plugin update` 一键升级、`/plugin uninstall` 卸载。安装后重启或重新加载会话即可使用。

## 使用

安装后直接对 Claude 描述你的产品想法，或显式触发：

```
/prd-writer
```

也可以直接说「帮我写个 PRD」「整理一下这个功能的需求文档」之类，技能会自动介入并引导你完成分阶段流程。

## 更新 / 卸载

```
/plugin update prd-writer@prd-writer-skill
/plugin uninstall prd-writer@prd-writer-skill
```

## 目录结构

```
prd-writer-skill/
├── .claude-plugin/
│   └── marketplace.json          # 市场清单
└── plugins/
    └── prd-writer/
        ├── .claude-plugin/
        │   └── plugin.json       # 插件清单
        └── skills/
            └── prd-writer/
                ├── SKILL.md      # 技能主体
                └── references/
                    └── prd-template.md
```

## License

MIT
