---
name: prd-writer
description: >-
  Guide product discovery conversations and produce standard PRD documents in
  Chinese. Use when the user describes a product idea, feature request,
  improvement request, vibe-coding project, MVP scope, or explicitly asks to
  write a PRD, product requirements document, 需求文档, 产品需求, or 功能规格.
  Enforce a staged workflow by diagnosing from user/business/technical
  perspectives, confirming page structure and navigation, outputting a concise
  concept PRD for alignment, freezing scope, then generating an
  implementation-ready PRD with flows, states, fields, copy, and exception
  handling.
---

# PRD Writer

## Core Rule

Do not output a full PRD, feature list, or structured requirements document before completing Phase 1 diagnosis, page-structure confirmation, and Phase 2 concept alignment. Keep the interaction conversational until the concept PRD is confirmed.

Use Chinese by default unless the user requests another language.

## Trigger Confirmation

After receiving the user's initial description, restate the core requirement in one sentence, then explain that you will ask a few rounds of questions to align on scope before starting Phase 1.

## Workflow

### Phase 1: Discovery and Page Structure

Collect the required facts from user, business, technical, and page-structure perspectives before drafting. Ask no more than 3 questions per turn, then wait for the user. If the user already provided an answer, do not ask it again.

User perspective:
- Who is the target user? Include age range, role/background, and usage context when possible.
- How do they solve this problem today?
- What single concrete job should the product help them complete?
- How often will they use it: daily, weekly, occasional, or another cadence?

Business perspective:
- Is the product free or paid?
- If paid, what model: one-time purchase, subscription, freemium, or another model?
- Is this a validation project or a long-term product?

Technical perspective:
- What product form: mini program, iOS, Android, H5, Web App, or another platform?
- Does it need accounts and login?
- Where does data live: local storage or cloud database?
- Does it depend on third-party services such as maps, payment, AI APIs, notifications, or analytics?
- How many weeks should this version take to build?

Page-structure perspective:
- What are the main pages or tabs? For example: 首页, 日历页, 记录页, 统计页, 个人中心.
- What does each MVP function map to: which page is the entry, and where does the result appear?
- What navigation pattern should the product use: bottom tabs, side nav, top nav, single-page flow, or wizard?
- Does it need supporting pages such as onboarding, login, settings, detail pages, edit pages, subscription/payment pages, or help pages?

When answers are vague, ask the minimum follow-up needed to remove ambiguity. Do not over-interview once enough information exists to write a precise concept PRD.

If the user does not know the page structure, propose a minimal page-structure draft based on the MVP functions and ask for confirmation. Do not proceed to the concept PRD until the page structure is either provided by the user or confirmed from your draft.

### Phase 2: Concept PRD Alignment

After Phase 1 is complete, immediately output only this concept PRD template. Keep it under 200 Chinese characters when practical, and do not add extra sections.

```markdown
## 概念版 PRD

核心用户：[一句话描述目标用户]
要解决的一件事：[一个具体痛点，不能写多个]
产品形态：[平台]
页面结构：[主页面/Tab，不超过 5 个]
最小可用版功能（≤ 3 条）：
  1. [功能一]
  2. [功能二]
  3. [功能三]
本版本不做：[明确排除的功能]
商业模式：[收费方式 或 免费]
技术前提：[账号体系 / 数据方案 / 第三方依赖]
```

Then ask exactly:

```markdown
以上是概念版 PRD，请确认：① 方向是否对齐？② 有需要调整的地方吗？
确认后进入落地版。
```

If the user requests changes, revise the concept PRD and ask for confirmation again. Do not enter Phase 3 until the user confirms.

### Phase 3: Scope Freeze

Before writing the full PRD, ask the user to confirm the frozen scope:

```markdown
在开始落地版之前，请确认以下内容不会再修改：

✅ 目标用户：[从概念版填入]
✅ 核心功能（≤ 3 条）：[从概念版填入]
✅ 平台选择：[从概念版填入]
✅ 页面结构：[从概念版填入]
✅ 本版本不做：[从概念版填入]

请回复"确认"后继续。
```

If the user changes scope, return to Phase 2 and realign. Continue only after explicit confirmation.

### Phase 4: Implementation-Ready PRD

Load `references/prd-template.md` before writing the full PRD. Follow its structure strictly.

Rules:
- Do not use vague placeholders such as "待定", "TBD", "视情况而定", or "后续补充".
- Fill every section with a concrete decision. If information is missing, infer a conservative default and label it as "建议默认值：" instead of leaving it open.
- Cover every P0/P1 feature with user flow, state machine, field rules when inputs exist, copy rules, and exception handling.
- Include normal paths and exception paths in every user flow.
- Use the current date for the document date unless the user provides another date.
- Use the user as author when no specific author is given.

Before finalizing, run the self-check in `references/prd-template.md`. If any blind spot is missing, add it before presenting the final PRD.

## Output Behavior

When the user asks for a downloadable file or `.docx`, combine this skill with an appropriate document-generation skill. Otherwise, output the PRD in Markdown.

If the user insists on "直接写完整 PRD" without diagnosis, briefly explain that this skill first needs a few alignment questions to avoid an unusable PRD, then start Phase 1 with up to 3 questions.
