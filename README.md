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

## 使用示例

它不会一上来就甩文档，而是分四步带你走完。下面是一段简化的真实流程：

**① 你描述想法**

> 我想做一个帮上班族记录每天喝水量的小程序。

**② 技能先访谈（每轮最多 3 个问题，不会一次问爆）**

> 收到，核心需求是「帮上班族记录每日饮水量」。先对齐几个问题再开始：
> 1. 目标用户主要是哪类上班族？大概什么年龄、什么场景下用？
> 2. 现在他们一般怎么记录喝水这件事？
> 3. 这一版希望几周内做出来？

**③ 问清楚后，先给一版精简「概念 PRD」让你确认方向**

> ## 概念版 PRD
> 核心用户：25–35 岁久坐白领
> 要解决的一件事：上班时容易忘记喝水、喝得不够
> 产品形态：微信小程序
> 页面结构：首页 / 记录页 / 统计页 / 个人中心
> 最小可用版功能（≤ 3 条）：1. 一键记录一次饮水 2. 每日目标与进度 3. 喝水提醒
> 本版本不做：社交、排行榜、硬件联动
> 商业模式：免费
> 技术前提：微信登录 / 云数据库 / 无第三方依赖
>
> 以上是概念版 PRD，请确认：① 方向是否对齐？② 有需要调整的地方吗？

**④ 你确认、冻结范围后，才输出可落地的完整 PRD**

> 包含每个功能的用户流程（正常 + 异常路径）、状态机、字段规则、文案规则、异常处理，不留「待定 / TBD」这类含糊占位。

> 💡 你也可以直接说「直接写完整 PRD」，它会简单解释为什么需要先对齐几个问题，然后从第一步开始——这是为了避免产出一份没法用的 PRD。

<!--
效果预览（可选）：建议放一张你真实跑出来的对话截图，比任何描述都有说服力。
做法：把截图拖进 GitHub 仓库页面的 issue 输入框得到一个图片链接，或把图片提交到仓库后，
在下面这行取消注释并替换路径即可：
![效果预览](./docs/demo.png)
-->

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
