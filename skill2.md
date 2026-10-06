---
name: rules-horror
description: This skill should be used when the user wants to generate Chinese rules horror
  stories (规则怪谈) — a genre where numbered rules create escalating supernatural horror
  through implication and contradiction. Triggers include: 规则怪谈, 写规则怪谈, 生成规则怪谈,
  规则类怪谈, 恐怖规则, rules horror, creepypasta rules, 续写规则怪谈, 规则怪谈连载,
  互动规则怪谈, 规则怪谈线索, ARG, 叙事型规则怪谈. The skill produces authentic Chinese
  rules horror with strict disclosure control and internal logic consistency, supports six
  generation modes (classic documents, narrative-fusion, serialized canon, interactive,
  clue-package/ARG, and meta-horror). Self-contained: all style modes, format library,
  serialization, narrative, meta-horror, adjacent-genre and anti-pattern material is
  inlined below. No external files or scripts required.
---

# Rules Horror Generator (规则怪谈)

> **自包含版说明**：原版 `SKILL.md` 依赖 `references/*.md` 六个文件与 `scripts/check_rules.py`。
> 本版已将所有依赖内容内联为附录 A–H，脚本调用改为等价的手工校验清单（附录 G）。
> **仅凭本文件即可运行，无需读取任何外部文件。**

## Overview

Generate authentic Chinese rules horror (规则怪谈) stories. The horror comes from rules themselves — their contradictions, their implications, what they refuse to explain. Never from direct description of monsters or gore.

## When to Use

- User asks for 规则怪谈, 规则类怪谈, 恐怖规则
- User provides a setting keyword (医院, 学校, 宿舍, 小区, 公司...)
- User asks without a theme — randomly pick from the theme pool
- User asks to 续写 / 连载 / 互动 / 补充规则 / 做成解谜线索包

## Generation Modes (生成模式)

Before gathering parameters, determine which MODE the user wants. The mode decides the
shape of the entire output. Default is Mode A. When the user asks without specifying,
infer the mode from the request or offer the two strongest candidates.

| Mode | 名称 | 形态 | 适合谁 | 上限来源 |
|------|------|------|--------|---------|
| A | 经典纯文档 | 只输出被发现的文档(守则/纸条/日志),读者自行拼图 | 硬核解谜读者,贴吧/A岛 | 文档之间的矛盾与留白 |
| B | 叙事融合 | 规则 + 主角破局故事,强钩子、节奏推进 | 短篇平台(番茄/知乎/小红书) | 破局逻辑 + 反差记忆点 |
| C | 连载引擎 | 同一世界观下的多篇/多集,规则随集数演化 | 长篇连载作者 | 五类节点卡 + 伏笔回收 |
| D | 互动生成 | 逐条规则问答、读者提问→补规则、谜题验证 | 直播间/评论区/群聊 | 交互中逐步展开 |
| E | 线索包/ARG | 跨渠道线索(截图/聊天/地图/订单),可被现实验证 | 线下活动、社媒解谜 | 真实锚点 + 多平台联动 |
| F | 元怪谈 | 规则影响读者/文档自身变化/传播即污染 | 资深怪谈读者 | 打破"文档边界" |

Mode A/B/C 共享本 SKILL 的六步工作流。Mode B/D/E/F 在六步工作流上叠加各自专用规则：

- **Mode B 叙事融合** → 附录 D
- **Mode C 连载引擎** → 附录 C
- **Mode E 线索包** → 附录 B 的渠道适配 + 附录 F 的 ARG 条目
- **Mode F 元怪谈** → 附录 E
- 类型嫁接灵感 → 附录 F

**强度拨盘 (Intensity Dial)**:用户可指定 1-5。1=细思极恐的日常不适(可发朋友圈),
3=传统怪谈恐怖(默认),5=认知崩解的深层恐惧。强度影响恐怖天花板的设计高度、
留白比例和语言克制度——强度越高,越要克制,越不能用血腥。

**输出渠道 (Platform)**:贴吧/A岛/知乎/小红书/公众号/B站弹幕/番茄短篇。
渠道决定格式、节奏和语言(见附录 B 末尾「渠道适配」表)。

## Core Principle

**The reader never sees the truth. The reader only sees the rules.**

A rules horror story is a set of documents (notices, handbooks, memos, scribbled notes) from different perspectives. The hidden truth exists only in the author's setting card — never output it. The reader pieces together fragments and scares themselves with their own reasoning.

---

## Six-Step Workflow

Execute each step sequentially. Do not skip steps. Do not output the hidden setting card.

### Step 1: Gather Parameters

Extract from user input:
- **Mode**: A/B/C/D/E/F (see Generation Modes above). Default A. If user asks to
  "写一个能发出去的故事" or mentions a 主角 → Mode B. If 续写/多集/世界观 → Mode C.
  If 提问式/互动/聊天室 → Mode D. If 解谜活动/线索/多平台 → Mode E. If 打破第四面墙/
  规则污染读者 → Mode F.
- **Intensity**: 1-5 dial. Default 3.
- **Setting**: User-specified theme, or randomly pick from the theme pool
- **Format**: Let the setting dictate format — single document, multi-perspective, or
  narrative + rules. For non-classic formats (聊天记录/物流追踪/病历/监控日志/弹幕/语音转写...)
  从**附录 B 格式库**中选定**一个格式族**再动笔。
- **Platform**: Infer from request or ask. 贴吧/A岛/知乎/小红书/公众号/B站/番茄.
- **Length**: User-specified or infer from request. Three modes. (See below)
- **Style**: 从**附录 A** 的六种文风模式中选**一种**,全文档统一使用:
  - **动物园式** — Cold bureaucratic. Horror from content, never tone. Fatal info hidden as afterthoughts. Occasional typos.
  - **大洛山式** — Folkloric dual-billboard. Old (wood) vs new (metal) signs. Chinese mythological vocabulary.
  - **二级学院式** — Heroic rules. Moral positions embedded in documents. Sacrifice and legacy themes.
  - **E市式** — Clinical emergency protocols. Language-as-defense. Rules admit their own corruption.
  - **糖果厂式** — Industrial trauma metaphor. Body horror via deprivation. Time-jumping documents.
  - **育英式** — Extreme minimalism. Three-word rules. Lists that end with impossible items.
  - Default for most everyday settings: 动物园式. Match style to the setting's natural voice.
  - 选定后按附录 A 中该风格的节奏、措辞与句式模板起草。

**短篇 (Short)** — 3-5 minute read:
- 1 document, 5-10 rules, single perspective
- One anomaly, one clean escalation arc
- Formats: a single notice, one post-it, one voicemail transcript, one page from a diary
- Core technique: ONE rule that makes the reader realize they've already broken it
- Example scenarios: a fridge notice, an elevator sign, a bedside note
- Setting card: minimal. Just anomaly + trigger + one protective action

**中篇 (Medium)** — 10-15 minute read (current default):
- 2-4 documents, 15-30 rules, 2-3 factions
- Contradictions between documents, well-developed symbol system
- Formats: official notice + insider notes + administrative records
- Full setting card with all fields

**长篇 (Long)** — 30+ minute read:
- 5-9 documents, 30-80+ rules, 4-7 factions
- Faction conversion paths (how someone moves from faction A → B)
- Document authenticity system (e.g. pen color = trustworthiness, like 二级学院)
- Structural organizing principle BEYOND documents: physical space (大洛山's mountain trail), time cycle, floor plan, bureaucratic hierarchy
- Inter-document causal chains: rule in doc A triggers protocol in doc B
- Reader can do real puzzle-solving — complete hidden story exists
- Symbol system where each symbol = specific contamination state, appears across ALL documents
- Expanded setting card required (see Step 2 long-form additions)
- Long-form SERIAL (连载): 切到 Mode C,先读**附录 C** 再进 Step 2 ——
  你要设计的是 canon sheet 这种管理性制品,不是单篇设定卡。

Theme pool (when user doesn't specify): 医院, 学校宿舍, 住宅小区, 公司办公室, 酒店,
图书馆, 博物馆, 地铁站, 养老院, 幼儿园, 游泳馆, 电影院, 便利店, 老旧居民楼, 山区民宿,
高速公路服务区, 夜市, 长途客运站, 外卖站点, 社区团购自提点, 自习室, 体检中心, 殡仪馆,
婚宴酒店, 宠物店, 棋牌室

### Step 2: Design Hidden Setting Card

Fill this card internally. **NEVER output it to the user.** It exists only to ensure rules are derived from a coherent world.

```
【场景边界】: What is the closed space? What are its physical/supernatural boundaries?
【异常实体】: Its BEHAVIORAL PATTERNS only. Never its appearance, name, origin, or motivation.
  - Activity cycle: Map to SPECIFIC clock times (e.g. 2:17-4:03, not "at night"). These times will be scattered across documents as puzzle pieces.
  - Triggers (what draws its attention — specific actions, not vague "negative emotions")
  - Limitations (what blocks or repels it — AND the cost/boundary of each protection)
【污染/认知扭曲机制】:
  Preferred mechanism: "认知即污染" — the act of KNOWING/UNDERSTANDING is the vector. The more the victim comprehends the entity, the more vulnerable they become. Knowledge IS infection. This creates the genre's fundamental paradox: rules protect you, but reading rules makes you more aware, which makes you more vulnerable.
  - Transmission method (must be tied to perception/cognition: seeing, reading, understanding, recognizing)
  - Early symptoms → late symptoms (each stage = a specific symbol in your concept node system)
  - What accelerates vs. halts progression

【阵营与撰写者】: 2-3 factions. Each document's WRITER is a character from one faction — they write from personal experience, not authorial knowledge.
  - Each faction: LIMITED KNOWLEDGE (only what they've personally seen), MISUNDERSTANDINGS (what they believe that's wrong), HIDDEN FROM THEM (what others keep secret)
  - GOALS must genuinely conflict. Not just "different knowledge levels" — INCOMPATIBLE OBJECTIVES. In 动物园: blue containment vs red escape. Both can't fully succeed.
  - Before writing each document, answer: "What has this specific person seen? What are they afraid of? What do they still not understand?"

【关键概念节点】: 2-4 core nouns that anchor the rule system.
  CRITICAL: Concept nodes MUST be physical objects or substances — things you can touch, hold, ingest, or be touched by.
  ✓ 兔子血、铁器、瓷砖线、水、白手套、黄色价签
  ✗ 索书号B849.1(分类编码)、"异常"(抽象概念)、"规则"(元概念)
  CRITICAL 2: Each concept node must correspond to a specific state in the contamination progression. They form a SYMBOL SYSTEM — not just physical objects but SYMBOLIC MARKERS. In 《动物园》: rabbit=early contamination, goat=terminal state, elephant=cognitive checkpoint. Each node means something specific about "how far gone" someone is.

【节点耦合图】: How concept nodes relate (X disguises Y, Z counters X, etc.)

【真相谱系】: Three layers of "truth" — 表层误解 (what most characters/readers believe
first), 中层机制 (the actual operating rules of the anomaly), 底层隐喻 (the historical,
emotional, or thematic core the setting is ABOUT). The bottom layer never appears in any
document; it exists so the middle layer has gravity. 糖果厂's bottom layer = concentration
camp history; its middle layer = the water/factory mechanics; its surface layer = "just a
strange factory". Designing all three prevents the story from being "spooky but hollow".

【时间轴】: An internal event timeline — BEFORE the incident, first rule added, first
failure, version revisions, present state. Every document sits somewhere on this timeline;
version numbers, dates, and handwriting changes are its visible traces. 时间轴 gives
readers a second puzzle dimension (拼时间线) and prevents 中后期设定漂移 in serials.

【恐怖天花板】: What is the WORST thing that can happen to someone in this setting? Not "feel scared" or "see something weird." The ceiling must involve identity loss, replacement, permanent entrapment, or irreversible cognitive destruction. This is the engine that drives all the rules. If the worst outcome is "read a spooky book" → restart Step 2.

--- LONG-FORM ADDITIONS (only for 长篇 mode) ---

【阵营转化路径】: For each faction, define how someone moves FROM this faction TO another. In 动物园: normal tourist → contaminated → sees ocean pavilion → wears black → becomes goat. In 二级学院: student → sees anomaly → joins 督察部 → dies in battle → legacy passes to next 卫生委员. Conversion paths make the world feel alive and give readers stakes.

【文档可信度体系】: Assign each document a trustworthiness level. NOT all documents are equally reliable. In 二级学院: carbon pencil = trusted, black pen = enemy, blue pen = protector. In 大洛山: wood signs = 天辉(old guard), metal signs = 夜魇(new management). Design 2-3 markers (color/material/source) that signal which faction wrote each document.

【结构组织原则】: For 5+ documents, you need an organizing principle beyond "doc 1, 2, 3." Options:
- 物理空间: 大洛山's mountain trail (100m → 9200m, each document tied to a location)
- 组织层级: 游客守则 → 员工手册 → 中层管理 → 高层文件 → 外部调查
- 时间推进: before incident → during → after → years later → investigation report
- 信息可靠度: from most-trusted to most-corrupted document

【预规划文档地图】: Before drafting any document, list ALL planned documents with:
- Document name, faction author, reliability marker
- What NEW information this document contributes (not found in others)
- Which other documents it contradicts or confirms
- Where it sits in the structural organizing principle
This prevents middle-document bloat and ensures every document earns its place.

【单元任务分工】: Give each document a JOB, not just content. Jobs include:
- 建立 (establishes a concept node or safe behavior the reader will rely on)
- 误判 (plants a plausible-but-wrong explanation the reader will later abandon)
- 推进 (adds one new fact that changes the interpretation of earlier rules)
- 揭示 (shows a consequence/state that only makes sense after cross-referencing)
- 动摇 (undermines a previously trusted faction/document — the corruption pivot)
A document may do one job well. If a document only repeats an established fact, cut it.
In a SERIAL (Mode C), each episode also gets a unit job: 建立规则 / 制造误判 / 推进主线 /
揭示机制 / 回收伏笔 — never just "another scary incident".
```

### Step 3: Draft Rules

Derive every rule from the setting card. Each rule must trace back to a specific setting element.

**Document authenticity test**: After drafting each document, read it aloud. Ask: "Would a real [administrator/lifeguard/librarian/manager] actually write this exact sentence?" Real internal documents:
- Use euphemism: "按报废流程处理" not "那是不存在的"
- Avoid drama: "如手套出现灰色斑点，停止使用并交还" not "手套上出现灰色斑点说明它已经注意到你了"
- Never wink at the reader: no "你会知道的", no "相信我", no "我没开玩笑"
- Sound tired, not theatrical. A real bureaucrat writing supernatural rules is exhausted and scared, not performing.

**规则源于事件原则 (Rules-from-incidents principle)**: Every abnormal rule exists because something specific happened. "不要投喂兔子" → someone fed rabbits, something went wrong. Before writing an abnormal rule, silently note the INCIDENT that forced management to add it. The incident is NEVER stated in the rule — but the rule carries its weight. A rule written because "three employees disappeared" reads differently from a rule written because "management suspects something might happen." The best rules sound like: "We learned this the hard way. We won't tell you what happened. Just do this."

**正常里掺异常原则 (Normal-with-abnormality principle)**: The first document (official notice) must be 40-50% genuinely normal rules. Real bureaucracy: garbage sorting hours, parking permits, noise complaints. Then ONE small impossible detail appears in an otherwise normal rule. The abnormality seeps in through the cracks of normal procedure. Not every rule should contain horror. The reader should sometimes think "wait, was that one weird or am I imagining it?"

**后果模糊化原则 (Consequence opacity principle)**: Never describe what specifically happens if a rule is broken. Vague bureaucratic phrases are acceptable: "后果自负" "概不负责" "按相关规定处理" — these are what real official documents say. But never: "否则你会死" "会被它带走" "会变成..." 《动物园》从不描述进入海洋馆的具体后果，只说不要进去。未知 > 任何可被描述的惩罚。

**动态安全边界原则 (Dynamic safety boundary principle)**: Safety is never binary. Every protective measure has a specific collapse condition. The lion zone is safe → until a 5th white lion appears. The jellyfish room is safe → until the director's office loses power. The reader should be able to INFER the collapse condition from cross-document clues, not be told directly.

**无知即安全原则 (Ignorance-as-safety principle)**: The more documents the reader reads, the more they know, the more vulnerable they become. This applies to the reader AND to characters in the story. The most knowledgeable document-writer should be the most contaminated. Create a genuine dilemma: reading more rules = more survival tools but also = more exposure.

**守则腐败原则 (Rule-corruption principle)**: Consider having a later version of an official document explicitly contradict an earlier version from the SAME source. Rules don't just conflict across factions — they decay within a single faction over time. The rule-writers themselves are losing the battle.

**文档形式多样化 (Format variety principle)**: Default is not always 3 documents. Consider:
- 单文档多版修订 (one notice, progressively annotated by different hands over years)
- 聊天记录 (WeChat group log, delivery driver chat, customer service transcript)
- 物流/订单追踪 (tracking numbers, delivery notes, pickup codes)
- 病历/体检报告 (medical forms with doctor annotations)
- 论坛帖子 + 评论区
- 语音转文字记录
- 日历/日程条目
- Let the setting dictate the format. A delivery station suggests tracking logs. A hospital suggests medical charts. A school suggests exam papers.
- 选定任何格式前,先读**附录 B** 中该格式的条目——每种格式都有真实世界的惯例
  (抬头字段/时间戳/行话/排版痕迹),以及它独有的恐怖抓手和易错点。
- Platform also dictates language: 贴吧/A岛 用"lz/前排/细思极恐"式帖文体,知乎用
  问答/专栏体,小红书用短句+emoji+话题标签,番茄用强钩子短段落。同一份怪谈换渠道
  要重新换皮,不能原文直发。(见附录 B「渠道适配」)

**Document information increment principle**: If using multiple documents, each document must contribute information NOT found in others. Documents should not merely confirm or repeat. Think of each document as a puzzle piece from a different angle — the reader needs all of them to see the full shape. A document that only reinforces existing rules is wasted.

**Protection limitation principle**: Every protective measure must have a boundary. Iron wards off X — but it drains body heat, or loses potency after repeated use, or doesn't work if you've already broken a specific rule. Never create a "universal solution" item. The reader should think "iron helps, but at what cost?" not "just hold iron and you're fine."

**规则数量上限**: 单份文档 8-15 条规则;多文档总规则控制在 30 条以内。需要更多信息就拆到别的文档/阵营,不要堆在一份里。

Escalation is organic, not formulaic. The reader should feel the ground shifting under their feet — not count the paragraphs until the next "scary rule." Some documents should be 90% normal with one wrong sentence. Some should start wrong and get worse. 恐怖程度呈波浪式起伏,不是直线上升——穿插安全区和日常细节,给读者呼吸空间。

Rules are written in **official document tone**: calm, procedural, bureaucratic. The contrast between mundane tone and disturbing content creates the horror.

### Step 4: Logic Verification

Run these checks on the draft:

**A. Forward derivation**: For each rule, ask: "Which element in the setting card justifies this rule?" If a rule can't be traced back — cut it or add the justification.

**B. Reverse check**: For each element in the setting card, ask: "Does at least one rule express this?" If an element has zero rules — either add a rule or accept it stays fully hidden (L3 disclosure).

**C. Contradiction audit**: Find all surface contradictions between rules. For each contradiction, verify the setting card has an explanation (different faction, different time, different cognitive state). If a contradiction has no explanation — fix the setting card or remove one side of the contradiction.

**D. Mechanical check (机械校验) — 手工清单**: 原捆绑脚本已移除,改为按下列 13 项逐条人工扫描
(判定阈值与原脚本完全一致)。**硬错误必须全部修完**;警告尽量修。
机械校验抓的是眼睛会放过的技术性失误,**不能替代 A/B/C 的人工审查**。

| # | 检查项 | 判定条件 | 级别 |
|---|--------|---------|------|
| 1 | 句子长度 | 两个标点之间 >24 字 → 错误;>20 字 → 警告 | 错/警 |
| 2 | "请"字密度 | 含"请"的规则行数 > 规则行总数 ÷ 5 + 1 | 警告 |
| 3 | 禁用 AI 连接词 | 值得一提的是 / 综上所述 / 总而言之 / 需要注意的是 / 请务必注意 / 特别提醒 / 以确保 / 为了避免 / 换句话说 / 不难发现 / 不得不说 / 你会发现 | 错误 |
| 4 | 弱动词 | 进行 / 实施 / 加以 / 作出 / 给予 | 错误 |
| 5 | "的"字链 | 同一句 ≥3 个"的" | 警告 |
| 6 | 破折号滥用 | 全文"——" > 3 处 | 警告 |
| 7 | 三项并列 | 同一句 ≥2 个顿号(A、B、C 平行结构) | 警告 |
| 8 | 连续条件句 | 连续 ≥3 行以 如/如果/当/若 开头 | 错误 |
| 9 | 孤立祈使句 | 不要。/ 不要看。/ 不要听。/ 别去。/ 别看。/ 别听。/ 没有。/ 不解释。/ 快跑。/ 活下去。 | 错误 |
| 10 | 孤儿规则 | 设定概念节点后,未提及任何节点的规则行 >60% → 错误;>40% → 警告 | 错/警 |
| 11 | 黑名单桥段 | 不要回头 / 不要相信任何人 / 镜子里的你不是你 / 所有人都已经死了 | 错误 |
| 12 | AI 平衡句式 | "不是…而是…" → 错误;同句同时出现"不是"与"是" → 警告(人工复核) | 错/警 |
| 13 | 序列套路 | 全文同时出现 首先 / 其次 / 最后 | 警告 |

> 第 10 项用法:先在心里列出本次的概念节点(如"兔子血、山羊肉、海洋馆"),
> 再逐条规则检查是否命中任一节点。

**E. Serial consistency (连载一致性, only Mode C)**: Before delivering a new episode,
load your canon sheet (附录 C) and check: 角色知情边界
(does this character know things they haven't been shown?), 规则有效期 (is a
revoked/expired rule being used as active?), 线索状态 (which clues are open,
which must be paid off, which are overdue?), 伏笔回收计划 (what will be collected
in which future episode). Output a "矛盾 / 待确认 / 可回收项" list; do NOT fix
ambiguities that are deliberate author choices — flag them as 待确认 instead.

### Step 5: Horror Polish

Apply the **four-layer disclosure model**. Check information distribution across rules:

| Layer | Description | Rule |
|-------|-------------|------|
| L0 必须明示 | Minimum info needed for reader safety actions | "If X happens, do Y immediately" |
| L1 暗示存在 | Describe effects/traces, never the entity itself | "If you hear singing from the ward, do not check" |
| L2 矛盾暗示 | Contradictions between rules imply the hidden truth | Rule A contradicts Rule B — reader infers why |
| L3 完全留白 | Fragments that readers assemble themselves | Scattered references to "it", "last time", "that room" |
| L4 元披露 | The document's EXISTENCE or materiality is the horror (Mode F) | The notice itself has more rules now than when you started reading; the file has your handwriting in it |

Only use L4 in Mode F (meta-horror). It must be earned: never announce "this document
is changing" in the text — the change happens across re-reads, versions, or channels.

Disclosure iron rules:
1. NEVER describe the entity's appearance, origin, or motivation
2. NEVER provide a "single truth" — keep at least 2 interpretable directions
3. Horror conclusions are REACHED by the reader, not STATED by the text
4. If a sentence explains "why", delete it and keep only "what to do"
5. NEVER state the nature of the anomaly directly — not even in the most "inside" document. "雾是活的" → wrong. "雾会等你。你不出门它就在窗外。你出门，三分钟内到你面前。" → correct. Describe BEHAVIOR, never essence. This applies to ALL documents including handwritten notes from victims.
6. NEVER state consequences of rule-breaking. "If X, do Y" — full stop. No "otherwise..." No "to avoid..." The reader must never learn what happens if they fail.

**否定性指令心理机制**: When a rule says "不要看窗外", the reader's brain first registers "窗外" before processing "不要". The negation ITSELF plants the dangerous concept. Use this deliberately:
- Place the most disturbing concept AFTER "不要" — the reader must visualize it to negate it
- "不要确认窗外是否在下雨" → reader now knows rain matters, imagines checking
- This creates an inescapable cognitive trap: obeying the rule REQUIRES thinking about the danger

Then run the **Quality Checklist**:

- [ ] **恐怖天花板**: If the reader pieces together the full hidden truth — does it involve identity loss, replacement, permanent entrapment, or irreversible cognitive destruction? If the worst outcome is "feel unsettled" → Step 2 failed, restart.
- [ ] **认知即污染**: Is the contamination mechanism tied to perception/cognition (seeing, reading, understanding, recognizing)? The more you know, the more vulnerable you are?
- [ ] **符号体系**: Do concept nodes form a coherent SYMBOLIC system where each node maps to a specific contamination state? Or are they just random physical objects?
- [ ] **概念节点物理性**: Are all core concept nodes physical objects/substances? Zero abstract nodes (codes, categories, "phenomena")?
- [ ] **恐怖感**: At least 3 "细思极恐" points where the reader's own reasoning creates the scare
- [ ] **创意**: No clichés — 避开附录 H 的烂俗桥段黑名单。Core concept nodes feel original.
- [ ] **逻辑**: All surface contradictions have hidden-setting explanations. Protective items have limitations. Hidden setting forms a complete, coherent narrative (因果闭环).
- [ ] **留白**: ≥30% of key information is L2 or L3 (not directly stated). Zero direct statements of anomalous nature in ANY document. **Zero stated consequences of rule-breaking.**
- [ ] **文档真实性**: Would a real person in this role actually write these sentences? No winking, no theatricality. Bureaucrats use euphemism. Victims understate.
- [ ] **规则源于事件**: Does each abnormal rule carry the weight of an unstated past incident? Would it read differently if the writer had personally witnessed the consequence?
- [ ] **撰写者有限视角**: Does each document reflect its writer's specific, limited knowledge — not the author's full setting card? Do factions have genuinely incompatible goals?
- [ ] **正常里掺异常**: Is the first document 40-50% genuinely normal rules? Can the reader read 3-4 rules before noticing anything is wrong?
- [ ] **文档非叙事化**: 文档是"被发现的物件",不是微型小说。没有人物弧光、没有情感高潮、作者不知道其他文档说了什么。
- [ ] **语言**: See Step 6 for full rules. Key checks:
  - Official docs use 公文惯用语 (本/须/应/不得/经/予以), not "请" (max 1 per 5 rules)
  - Insider docs are fragmented, unnumbered, colloquial — real people don't write numbered lists on post-its
  - Sentences vary in length and pattern, not all "如X请Y"
  - At least one document has an imperfection (water damage/strikethrough/missing text)
  - Zero AI connector phrases. Endings are abrupt.
- [ ] **耦合**: Rules orbit 2-4 PHYSICAL concept nodes with high coupling density. ≥60% 规则涉及核心节点。Zero orphan rules.
- [ ] **信息增量**: If multi-document, each document contributes information not found in others. No document merely confirms another.
- [ ] **动态安全边界**: Does each protective measure have a specific, inferable collapse condition? Not just "sometimes unsafe" — readers should be able to reason about WHEN it fails.
- [ ] **无知即安全**: Does acquiring knowledge through reading later documents increase danger? Is the most knowledgeable writer the most contaminated?
- [ ] **文本考古学**: Do physical document traces (handwriting changes, torn pages, strikethroughs, margin notes) tell a story beyond the text itself?

**模式专项检查 (run for the selected mode, ignore others)**:
- [ ] **B 叙事融合**: 破局是否只依赖前文已展示的信息?(不能作者开挂) 每 800-1200 字
  是否有一次规则触发/信息反转/身份揭露? 结尾是否停在强钩子上而不是总结? (详见附录 D)
- [ ] **C 连载**: 本集是否完成了自己的单元任务? 五类节点卡是否已更新? 有无
  已到期未回收的线索? 新规则是否在 canon 中登记了触发条件/例外/代价/有效期? (详见附录 C)
- [ ] **D 互动**: 每次只回答当前问题/补充当下需要的规则,绝不提前泄露后续?
  用户的每个问题是否都能在设定卡中找到确定答案(允许"你不知道")?
- [ ] **E 线索包**: 每条线索的渠道是否符合该渠道的真实格式? 拼出的谜题是否有
  唯一可验证解?(允许故意歧义,但必须有至少一条可验证路径)
- [ ] **F 元怪谈**: 元层元素是否只有一处、且从不明说? 常规怪谈基底是否仍然成立
  (元怪谈是加成,不是替代)? 伦理边界是否全部满足? (详见附录 E)

### Step 6: Language Polish

This is the most critical step. Bad language ruins perfect structure.

#### A. Official Document Language (适用文件一/守则/通知/手册)

**公文惯用语 — MUST use these to sound real**:
- 本(手册/守则/店/区域) — not "我们的" or "这个"
- 须/应 — not "请" (use "请" sparingly, only for true optional courtesies)
- 不得/禁止/严禁 — not "不要" or "别"
- 经(店长批准/核实后) — not "在经过...之后"
- 予以(处理/更换) — not "进行处理"
- 自行(判断/安装) — not "自己判断"
- 当班/在岗 — not "上班的时候"
- 擅自 — not "自己随便"
- 如(发现/遇/有) — condition prefix
- 此致/遵照执行/特此通知 — document closers (use one, not all)

**句式变化 — mix these patterns, don't repeat one**:
- 祈使短句: "冷藏柜温度维持 2-4°C。"
- 条件+指令: "如条码污损，手动输入 13 位数字。"
- 禁令: "禁止向桑拿石泼水。"
- 定义+限制: "黄色价签为促销商品，由店长指定。"
- 无主语句: "交班前清点退货篮商品数量。"
- **同一句式不得连续出现3次以上**。写完后逐条检查：如果连续3条都是"如X，Y"→ 重写中间那条。

**句子长度控制**: 两个标点之间连续文字不超过 20 字。超过就断句。短句（≤10字）制造紧张，长句（15-20字）承载信息。相邻句子长度差异应 >5 字——长短交替才有节奏。
- ✗ "如发现瓶装饮料瓶身水珠在室温下持续五分钟以上未蒸发"（23字）
- ✓ "瓶身水珠在室温下超过五分钟不蒸发——该瓶移至冷藏柜底层。"

**删"的"**: 连续出现两个"的"→ 至少删一个。连续三个"的"→ 翻译腔确诊，拆句重写。

**删弱动词**: "进行""实施""加以""作出""给予"→ 直接删掉，把真正的动词提上来。
- ✗ "对商品进行清点" → ✓ "清点商品"
- ✗ "对异常情况加以记录" → ✓ "记录异常情况"
- ✗ "对退货篮中的商品进行每日清点并加以记录" → ✓ "每日清点退货篮商品。记录数量。"

**行业真实用语**: 每个场景有自己的一套术语。写之前搜一下真实文档——
- 便利店: 唱收唱付、先进先出、理货、排面、盘点、报废/报损
- 物业: 报修、巡查、台账、责令整改、限期
- 图书馆: 编目、上架、剔旧、索书号、馆藏
- 用不对术语 = 第一句话就暴露是假的

**朗读测试**: 写完每份文档后逐条朗读。舒服 = 通过。拗口 = 重写。中文是短句的语言。"一个好句子念起来嘴舒服，耳朵舒服，心里也舒服。"（老舍）

**"请"字使用规则**: 每 5 条规则最多用 1 次"请"。其他地方用"须""应""勿""不得"。不是礼貌问题——是真实公文确实很少说"请"。
- ✗ "请勿在夜间进入该区域，请注意安全"
- ✓ "禁止夜间进入该区域。" / ✓ "本区域22:00后关闭。"

#### B. Insider Document Language (适用文件二/三/纸条/便利贴/日记)

**真人字条的特征 — MUST mimic these**:
- 碎片化，不编号。真人在便利贴上不会写"1. 2. 3."
- 跳跃。一句话可以只写半截。
- 有废话和重复。"我跟你说，那个——算了你自己看吧"
- 有错字和涂改痕迹（用~~删除线~~或直接写错不纠正）
- 不确定。用"好像""我也不确定""可能是"
- 口语词：那家店、这边、那边、上次、那次

**反例 vs 正例**:
```
✗ 字条: "第5条手册说黄色价签由店长指定——店长只管白班。夜班的黄色价签在你到岗时已经在了。"
✓ 字条: "手册第5条——黄的价签，别信它说是店长放的。夜班你来的时候就在架子上了。不是我放的。也不是你。就是这么回事。"

✗ 字条: "1. 黄色价签不是店长放的。2. 外面下雨那条是真的。3. 冷藏柜..."
✓ 字条: "黄的价签——不是店长放的。你别管谁放的。反正别碰。
         对了还有那个下雨的事。是真的。
         冷藏柜——算了这个你自己看吧我写不动了"
```

#### C. General Prose Rules

**CRITICAL: Voice Differentiation (声音差异化)** — Each document MUST sound like a different person wrote it. This is the #1 failure mode. Before writing each document, define its voice profile:

| 维度 | 如何差异化 |
|------|----------|
| **句子长度习惯** | 有人爱写短句。三个字。五个字。有人一段话不断气写到页面边缘。人在不同状态下句子节奏不同——慌张的人句子碎，官僚的人句子长而平稳。 |
| **用词范围** | 医生写"体温""体征""预后"。病人写"冷""睡不着""那根体温计"。保安写"巡""查看""记录"。不要所有人共用同一套词汇。 |
| **标点习惯** | 有人只用句号。有人爱用破折号——想到哪说到哪。有人标点规范像印刷品。有人通篇逗号到底。标点本身就是指纹。 |
| **情感外露程度** | 官僚文件：零情感。退休老护士的信：有温度，会叹气。墙上涂鸦：绝望或麻木。CDC报告：纯客观。每份文档的情感温度必须不同。 |
| **口头禅/个人特征** | 老护士的信里可能有"闺女""你干两年就懂了"。病人涂鸦可能在反复写同一个词。官僚文件决不会有口头禅。 |

**Voice audit（写完所有文档后逐份朗读检查）**：
- 遮住文档标题，只读正文。能从语言习惯猜出这是谁写的吗？
- 如果两份文档互换开头两句话——读起来还自然吗？如果自然 → 声音没拉开，重写其中一份。
- 最简测试：文档A的任意一句话，可能出现在文档B里吗？如果可能 → 声音不够差异化。

**Banned AI phrases** (delete on sight):
- 值得一提的是, 综上所述, 总而言之
- 首先...其次...最后
- 需要注意的是, 请务必注意, 特别提醒
- 并, 且, 以及 (replace with commas or split sentences)
- 进行 (replace with specific verb)
- 以确保, 为了避免 → 以防, 免得
- 换句话说, 不难发现, 不得不说, 你会发现
- **不是...是...** — The #1 AI marker. Negation-then-affirmation is AI's compulsion to "balance" every statement. Delete the negation half, keep only the affirmative. "那不是门，是别的什么" → "那扇门不对。" or just describe behavior. "黄色价签不是由普通员工设置，而是由店长指定的" → "黄色价签由店长指定。"
- **孤立破折号"——"** — Use sparingly. 160 dashes per 9 stories = AI using dramatic pauses. Real Chinese documents use dashes rarely. Replace with comma, period, or just let sentences run together naturally.
- **"那是__"作为解释** — "那是安全出口指示灯""那是物业巡查""那是骗你的". AI reflexively explains everything it mentions. Real notices state facts without labeling them: "安全出口指示灯常亮" not "那是安全出口指示灯".
- **孤立"正常。"** — AI's reassurance tic after describing something wrong. If something is wrong, don't say it's normal. Let the reader decide.
- **"不解释"** — AI trying to sound mysterious. Real bureaucrats don't announce they're not explaining. They just don't explain.
- **缺宾语的孤立祈使句** — "别去。""别看。""不要。" — unnatural Chinese. Real people include the object: "别去旧馆。""别看窗外。"
- **"你不会想__的"** — AI melodrama. Just state the fact.

**Anti-AI structural patterns — MUST break these**:
- **禁止三项并列**: AI loves "A...B...C..." triple平行结构. If you have three conditions/items, make them different lengths, different grammatical structures. Break one mid-sentence. Make one a fragment.
- **破坏对称**: If two adjacent paragraphs have similar length → make one shorter or longer. If you listed two causes → don't add a third just to complete a set. Real documents are asymmetric.
- **加入真正的废话**: Real documents have genuinely boring parts. A real驾校须知 spends 200 words on registration fees, ID photos, and driving Test appointment procedures before mentioning anything strange. Include 1-2 genuinely irrelevant rules.
- **打破节奏**: No two consecutive rules should have the same sentence structure. If rule 3 is "如X，Y", rule 4 must be different — a bare command, a definition, a fragment.
- **困惑度思维**: When choosing between two words, pick the LESS predictable one. AI defaults to the statistically safest word. "教练不会追问" → "教练不会再提这件事" or "教练当没听见" or just let it hang without closure.

**Rhythm control**:
- Let sentence length follow the natural rhythm of what's being communicated. A short instruction naturally produces a short sentence. A complex procedure naturally produces a longer sentence with clauses.
- 动物园 NEVER artificially fragments sentences for dramatic effect. "不要投喂兔子。其余的动物都可以。" — short because the idea is simple. "本园安全措施保障绝对没有问题，动物没有出逃的可能性，尤其是小型草食动物大多被关押在不可触摸的封闭性环境里。" — long because it's a bureaucratic assurance.
- **CRITICAL: Do NOT use stand-alone fragments as a horror technique.** "不要看。" as a standalone paragraph is not how real people write. Real people write "不要看窗外" or "不要往那边看" — the object is included, the sentence is complete. Fragments like "不要看。" "没有。" "别去。" are AI trying to sound dramatic. They achieve the opposite.
  - 例外:育英式的"没有。""不要看。"是**列表中的一项**,后面有自然衔接或递进,不是孤立的段落碎片。
- End documents abruptly — no "祝您..." or "谢谢配合", no 温馨/感人/励志/总结性收尾。

**Imperfection principle**: Real found documents have flaws. Add ONE of:
- 被水浸模糊的半行字（用省略号或 ■ 替代）
- 涂改痕迹（~~划掉~~后改写）
- 撕去的页面/撕掉的半句话（"以下两页已缺失"）
- 字迹突然变化（后期字条与前期明显不同）
- 日期缺失或矛盾
- 一个写错的字没改
- 一段写了又划掉重写的内容
Don't overuse. One flaw per document max.

**Revise-and-rewrite check**: After drafting each document, scan for:
- Three items of same grammatical structure in a row → break one
- Two adjacent paragraphs of similar length and structure → make one messier
- Every sentence advancing the plot → add one sentence that doesn't
- "以下文件来自..." → use a different framing or no framing at all

---

## Output Rules

1. **Never output the setting card.** Not even as "author's notes" or spoiler tags.
2. **Never explain the horror.** If the reader asks "what does rule X mean", the answer is "that's for you to figure out."
3. **Output only the rules document(s).** Optional: a 1-line atmospheric scene-setter (e.g. "以下文件发现于XX市第三人民医院档案室，日期不详。")
4. **No post-script analysis.** No "解读", no "真相揭晓", no "作者说".

**Mode-specific output rules**:
- **Mode C (连载)**: The canon sheet IS an author-facing artifact. When the user
  requests it, output it as a separate file (JSON/Markdown table) — never inside the
  reader-facing text, and never inline in the story channel. Each episode delivers
  only the reader-facing documents.
- **Mode D (互动)**: Never dump the full rule set up front. Reveal one rule/one piece
  of paper per interaction, and stay in the fiction's frame ("你发现门后贴着半张纸…").
  If the user asks about something outside the current knowledge, answer with the
  writer's limited knowledge, not the setting card.
- **Mode E (线索包)**: Deliver a channel map (每条线索发在哪个平台/什么格式/什么时间)
  plus the assets themselves. Keep real-world anchors verifiable and fake anchors
  clearly fictionalized to avoid misinformation.
- **Mode F (元怪谈)**: The output is still documents. The meta effect comes from
  versioning, re-read drift, or cross-channel recursion — never from narrating "you
  are now scared".

---

# 附录 A：六种文风模式

六种来自经典作品的文风。生成时选择一种，全文档统一使用。

## 风格一：动物园式（冷感公文）

**来源**：《动物园规则怪谈》十六椰子
**核心特征**：恐怖100%来自内容，0%来自语气。最吓人的信息伪装成最平淡的附加说明。

### 节奏
- 长短句极度变化：三个字一句话（"不要投喂兔子。"），也可能一口气五十字跑句不断气
- 有些句子明显是"写到一半觉得前面没说清楚又往回补"——真实的公文起草痕迹
- 不追求每句话的"精修感"，允许粗糙

### 措辞
- 始终保持标准的游客服务/官方口吻——"亲爱的游客""希望您和您的孩子可以观光愉快"
- 免责声明模式："否则后果自负""本园不对您的安全负责""且无法给您提供解决方案"
- 把致命信息藏在句子的附加位置——"大象是一种体型巨大的生物，而且不是白色的。"
- 偶尔可以有一个错别字（"收货"→"收获"）——增加真实文件的质感

### 指令方式
- 每条规则给出具体物理动作：撕虚线、握住、躲在假山后面、确认蓝色衣服
- 不用抽象警告——"注意安全""避免异常"不出现
- 是什么 + 如果看到什么 + 做什么。三段式。不解释为什么。

### 句式模板
```
"本园/本店/本院 ___。如您___，请___，不要___，尤其是___的时候。"
"___是___的，而且不是___的。请确保你看见的是且只有___。"
"不要___。其余的都可以。"
"如果您触犯了以上任何一条，并且发现自己正在___，请立刻___。不要害怕，这里的___不会___。在这一切之后，立刻___。"
```

### 示例段落
> 本店冷藏柜恒温维持在2-4°C之间，柜内饮料瓶身有水珠凝结属正常现象。理货时如发现某瓶饮料的水珠在室温下长时间不干——具体来说超过五分钟——将该瓶移至冷藏柜最底层。当日不再出售该瓶。不需要向店长报告，也不需要知道原因。

---

## 风格二：大洛山式（民俗对抗）

**来源**：《大洛山规则怪谈》Qsi
**核心特征**：多阵营以物理载体区分（木质告示 vs 金属告示）。道教/民俗词汇自然混入公文。读者通过对比对立告示牌解谜。

### 节奏
- 每种告示有自己的节奏——旧告示（木质）句子偏长，有古意；新告示（金属）短促，像行政命令
- 段落之间有明显的"阵营切换"，读者可以感受到说话的是不同的势力

### 措辞
- 旧阵营：木质、纸质、手写。用词偏传统——"火种""龙吟潭""大洛村"。句子有古意但不文言。
- 新阵营：金属、印刷、塑封。用词偏现代行政——"封闭""禁止进入""按规处理"。
- 民俗词汇自然混入：山神、山鬼、香火、祭祀、龙吟
- 颜色体系作为阵营标记：金色（前台部/轻微腐化）、灰色（后勤部/中度）、白色（餐饮部/重度）、红色（娱乐部/极度）

### 句式模板
```
旧阵营："___是___的居所，不可___。若___，去___，那里的___会告诉你接下来怎么走。"
新阵营："___区域已永久封闭。禁止___。违者按___处理。"
```

### 示例段落
> 木质告示：登山者，此处以上为龙吟潭地界。不可携火种。若听见潭中有水声而潭面平静——那是龙吟。跪下。闭眼。等水声停了再起身。不要看潭水。
>
> 金属告示：龙吟潭观景台已封闭。禁止靠近。护栏后方区域为地质灾害隐患区。进入者后果自负。

---

## 风格三：二级学院式（热血规则）

**来源**：《二级学院规则怪谈》DXt7b4b
**核心特征**：规则之下涌动热血。文档有明确的道德立场——碳笔=可信(保护者)，黑笔=不可信(敌人)。牺牲与传承是核心主题。

### 节奏
- 规则本身是冷静的，但字里行间透出紧迫感和责任感
- 偶尔会有一两句话打破克制——"向它发出勇敢者的一击！"
- 文档之间有"英雄叙事"的底层暗流，但从不明说

### 措辞
- 角色头衔有分量：卫生委员、督察部、校工部、班长
- "镇定等级"——把心理素质量化成规则参数
- 保护性语言："无条件信任""第一时间可以信赖的人""他是班内最忠诚机敏的同学"
- 炭笔写的 = 可信。黑笔写的 = 敌人。蓝色笔写的 = 中立保护者。

### 句式模板
```
"___是你第一时间可以信赖的人。"
"时刻牢记___，不要忘记___。"
"如果你发现___，说明___。那时候，___。"
```

### 示例段落
> 卫生委员行为守则：你唯一可直接信赖的只有班长和辅导员。沟通方式只能通过电子设备。时刻牢记自己是通过正常选举流程选出的卫生委员。教室卫生与本班宿舍卫生由你负责。如有人要求你去指定卫生区打扫——拒绝。要求其出示二级学院文件。

---

## 风格四：E市式（紧急规程）

**来源**：《Espedro市区999接线员紧急时期工作守则》UIaNEIs
**核心特征**：语言本身就是防御工事。反复背诵"人类定义"来维持认知边界。规则承认自身的可腐败性——后期版本否定早期版本。

### 节奏
- 接线员口吻：冷静、专业、分秒必争。句子像无线电通话——短、清晰、不容置疑
- 随着文档版本号推进（第6版→第17版），语气从专业逐渐变为僵硬、机械、像在重复背诵
- 被污染者的文档（笔记本）：编号崩解，内容从完整句子→单词→只剩一个名词

### 措辞
- 版本号本身就是叙事——"第6版""第17版"，每次更新暗示局势恶化
- 人类定义反复出现："人类是具有两只眼睛，两只耳朵，一只鼻子，一张嘴的灵长类生物。"
- 红蓝色频闪灯 = 区分人类与非人的唯一可靠标识
- 守则里出现自我否定——"绝不要相信15号手册"

### 句式模板
```
"本守则第___版。此前版本全部作废。"
"如果您听到___，那不是___。重复：那不是___。"
"___是人类。___不是人类。用___来区分。不要依靠自己的判断。"
```

### 示例段落
> 999接线员守则 第6版：您接听的每一通报警电话都来自人类。如果不是——您会知道的。如果电话那头的声音让您想要挂断——不要挂。继续接听。按标准流程询问地址和情况。保持声音平稳。对方会模仿您的声音，这是正常现象。只要您不停，对方就停。

---

## 风格五：糖果厂式（工业创伤）

**来源**：《切比雪夫糖果厂规则怪谈》
**核心特征**：工业/技术语言包裹历史创伤隐喻。身体恐怖通过日常需求的剥夺来传达（水不可饮用）。时间错位——不同年代的文档并置。

### 节奏
- 生产规范式的冰冷节奏。流水线一样——"第一条""第二条""第三条"，每一条都像机器的齿轮
- 偶尔出现极短的非规则文本——手机短信、空白页涂鸦——打破节奏

### 措辞
- 工业术语：车间、生产线、工号、胸牌、防毒面具、自给式呼吸器
- "水"被反复强调不可饮用——日常需求的剥夺是最基础的恐怖
- 历史时间标记：1922年成立→1930年摧毁→1991年短信→不明确的"现在"
- 柳树、黄绿色液体、淋浴间——日常物通过工业语境被异化

### 句式模板
```
"___生产线采用无水工艺。禁止饮用厂区内任何形式的水。"
"___车间不存在。如果___，那是___。"
"___是甜的。不要吃。"
```

### 示例段落
> 生产人员工作规范 第三条：本厂所有产品均采用无水生产线制造。厂区内不提供饮用水。食堂提供的汤碗中液体呈黄绿色属正常矿物质含量。食用后如出现口渴——正常。不要喝水。第二天口渴感会自行消失。如果第三天仍感口渴——向车间主管报告。不要自行饮水。

---

## 风格六：育英式（极简断裂）

**来源**：《育英中学校园指南》DH6oPBe
**核心特征**：用最少的字制造最大的恐怖。正常列表的末尾滑入不可能存在的项目。句子越来越短直到只剩三个字。

### 节奏
- 从正常长度的规则（15-20字）逐渐缩短
- 最终一条可以是三个字——"不要看。"
- 或者一组规则中突然出现极短的一条——"没有。"

### 措辞
- 省略所有解释。只说"是什么"或"不是什么是"。
- 列表末尾藏恐怖：正常列表→最后一项混入异常——"报告离你最近的老师/清洁工/裁判/奶奶/保安/槐树/刽子手。"
- 否定句的力量："没有操场""没有""没有必要操场"——三条规则共九个字，递进式否定

### 句式模板
```
"___。没有___。没有必要___。"
"不要___。其余的都可以。"  ← 注意：不是孤立的"不要___。"，后面有自然衔接
"___不是___。"
```

**关键警告**：育英式的短不是"刻意断句"。是每个句子表达一个完整但极简的意思。"没有操场"是一个完整的陈述——主语省略因为承前。不是把"不要去旧图书馆"砍成"不要。去。旧。图。书。馆。"那种AI碎片。

### 示例段落
> 操场规则：
> 1. 没有。
> 2. 没有操场。
> 3. 没有必要操场。
>
> 图书馆规则：
> 1. 不要看图书馆里的书。
> 2. 不要看。

---

## 风格选择指南

| 场景特征 | 推荐风格 |
|---------|---------|
| 公共场所（动物园/酒店/商场） | 动物园式 |
| 户外/山区/民俗场景 | 大洛山式 |
| 学校/组织/层级分明的机构 | 二级学院式 |
| 电话中心/调度室/应急服务 | E市式 |
| 工厂/实验室/有历史背景的建筑 | 糖果厂式 |
| 任何需要极致简洁的场景 | 育英式 |

混合使用：主风格用于最官方的文档，辅助风格用于内部文档。例如：官方守则用动物园式，内部纸条用育英式极短句，第三方调查用E市式临床腔。

---

# 附录 B：新媒体格式库 (Format Library)

规则怪谈的"上限"一半在内容，一半在容器。同一个隐藏设定，装进"医院通知"和装进
"外卖订单备注+骑手聊天记录"，恐怖感完全不同。本库收录 25 种文档格式，每种给出:
真实字段与惯例（让文件可信）、恐怖抓手（这个格式独有的吓人角度）、易错点（写崩的
常见原因）。写非经典格式前，先读对应条目，**选定一种格式族**再动手。

通用铁律:
- 格式是容器，不是皮肤。真实性来自字段和习惯，不是加几个"[诡异]"标注。
- 每种格式有自己"不会写的东西"——文档里出现该格式不可能出现的表达，立刻穿帮。
- 格式越普通，恐怖越有效。监控记录里的一句异常备注，比恐怖小说段落更吓人。

## 1. 官方守则/通知
**字段**: 标题、编号(如"〔202X〕X号")、适用范围、条款、落款、公章/盖章说明。
**恐怖抓手**: 致命信息藏在最正常的条款里;后期修订版推翻前期版。
**易错点**: 语气太戏剧化;"请"字泛滥;条款编号混乱。

## 2. 员工手册/岗位规范
**字段**: 岗位职责、考勤、奖惩、保密条款、签署确认页。
**恐怖抓手**: 岗位职责逐步长出不属于该岗位的内容(便利店夜班店员:"清点货架。不点人。");培训期手册 vs 转正后手册不同。
**易错点**: 把员工手册写成冒险指南，忘了大部分条款应该是无聊的。

## 3. 便利贴/匿名纸条
**字段**: 无抬头无落款、碎片化、涂改、写错不纠正、突然换话题。
**恐怖抓手**: 前半张是普通提醒，后半张字迹变样;纸是撕下来的，上面有上一层的字痕。
**易错点**: 编号列表;信息量太大;语气像作者旁白。

## 4. 日记/记事本
**字段**: 日期、天气、流水账、口语。
**恐怖抓手**: 条目从完整句子→短语→单个名词(认知崩解弧线);日期倒跳;某一天的字迹不属于本人。
**易错点**: 把日记写成小说;每天都有大事(真实日记大多无聊)。

## 5. 聊天记录
**字段**: 昵称、时间戳、撤回提示、已读、语音转文字、拼错字、表情包描述。
**恐怖抓手**: 对方撤回的消息是唯一重要的信息;"对方正在输入…"持续四小时;群成员列表比群聊内容更可怕。
**易错点**: 全员打字规范;没有口语;聊天记录像剧本对白。

## 6. 语音转文字记录
**字段**: [背景音]、[停顿]、[听不清]、说话人标注、时间戳。
**恐怖抓手**: 转写错误的地方恰好是关键信息("你们几点走"变成"你们几店走");背景音标注里出现不该有的声音;最后一条是空白的[00:00]。
**易错点**: 转写太干净;标注过度解释。

## 7. 物流/订单追踪
**字段**: 运单号、揽收/中转/派送节点、时间戳、客服工单、签收人。
**恐怖抓手**: 包裹在同一个中转站滞留 30 天后"已签收";签收人不是收件人;客服工单里第一条人工回复是"这不是我们网点的签收"。
**易错点**: 节点太少、时间线不真实;信息增量不足。

## 8. 病历/体检报告
**字段**: 科室、主诉、既往史、检验指标、医嘱、医生签名、复诊日期。
**恐怖抓手**: 主诉栏写着患者的自称描述，但姓名栏已经换过三次;检验项目里出现"本项目不适用人类样本";医生手写批注划掉了标准结论。
**易错点**: 医学术语用错;报告信息量堆满没有留白。

## 9. 监控/值班日志
**字段**: 表格、时间、点位、事件描述、交接班签名、"无异常"重复项。
**恐怖抓手**: 连续 200 行"无异常"之间夹了一行"注意:第14摄像头拍到的不是第14摄像头该拍的位置";交接班签名从两个名字逐渐变成一个名字。
**易错点**: 全是异常没有日常;表格格式不真实。

## 10. 论坛帖子+评论区
**字段**: 楼主(lz)、楼层、时间、引用回复、点赞数、举报记录。
**恐怖抓手**: 主楼是普通求助，一楼开始有人说"这个我知道，别删";帖子被锁后又被顶上来，发帖人变成了另一个人。
**易错点**: 评论区分工太明确，像作者安排好的提示器。

## 11. 弹幕/直播录屏转写
**字段**: 弹幕内容+时间码、观看人数、礼物记录、系统公告。
**恐怖抓手**: 直播间没开，弹幕还在滚;某条弹幕的时间码比直播开始时间早;"管理员已禁言你"而你没发过言。
**易错点**: 弹幕全在解说剧情;没人刷正常弹幕。

## 12. 地图/导航记录
**字段**: 起点、终点、路线方案、播报文本、搜索历史、收藏地点。
**恐怖抓手**: 导航播报里混入非官方语音("前方经过的隧道，不要数灯");收藏列表里有你没收藏过的地方;导航在目的地前 3 公里让你"调头，前往上一个目的地"。
**易错点**: 播报太像解说词;地点真实度不够。

## 13. 打车/出行记录
**字段**: 订单号、车型、车牌、司机评价、行程轨迹、费用明细、客服记录。
**恐怖抓手**: 行程轨迹在两点之间是直线(没有路);司机评价模板里混入一条"乘客下车后，请勿再与我联系";行程结束后订单仍显示"行程中"。
**易错点**: 信息量不够支撑推理;车牌车型太模糊。

## 14. 外卖订单+商家备注
**字段**: 商品、数量、备注、预计送达、配送员、评价、退款记录。
**恐怖抓手**: 同一地址连续三个月每天只点一份，备注从"不要敲门"变成"敲门，敲三次就走";骑手评价里出现"该地址在系统里显示不存在"。
**易错点**: 备注写得太文绉绉;订单时间线不合理。

## 15. 门禁/刷卡/考勤记录
**字段**: 卡号、姓名、时间、门禁点、正常/异常标记。
**恐怖抓手**: 某人的卡在下班后每 7 分钟刷一次同一扇门，直到凌晨;离职员工的卡号仍出现在每日记录里;考勤表最后一列是"备注:夜班不点名"。
**易错点**: 数字全是整数没有真实感(真实数据有 02:17 这种时间)。

## 16. 维修工单/物业台账
**字段**: 报修编号、故障描述、处理人、处理结果、材料费、回访。
**恐怖抓手**: 同一房间被报修 47 次"门从里面打不开"，处理结果每次都是"已更换门锁";第 47 次的回访人签名是第 1 次报修人的名字。
**易错点**: 台账太整洁;物业用语错误。

## 17. 二手交易记录
**字段**: 商品标题、描述、价格、聊天、评价、发货记录。
**恐怖抓手**: 卖家描述里写"卧室的镜子跟家具一起卖，别问为什么拆不下来";买家签收后评价"发货人不是卖家";商品链接已删除但订单还能打开。
**易错点**: 聊天太连贯;描述太像恐怖小说。

## 18. 民宿/酒店评价
**字段**: 评分、标题、正文、房型、入住日期、房东回复。
**恐怖抓手**: 所有好评都复制同一句话;差评被房东回复"您入住时房间编号应该是302，不是203";一条评价说"我住了三年，这里只有三个房型"。
**易错点**: 评价全在讲同一件事;没有正常的好评/差评混杂。

## 19. 智能设备日志
**字段**: 设备名、时间、语音指令记录、触发条件、设备状态。
**恐怖抓手**: 智能音箱半夜录到指令"报一下明天的天气预报"，但家里没人;门锁日志显示开门的人没有授权指纹;手机相册"回忆"功能生成了一段你不认识的家人的合照。
**易错点**: 设备日志太啰嗦;指令内容过于戏剧化。

## 20. 试卷/作业批改
**字段**: 姓名栏、题目、答案、红笔批注、分数、评语。
**恐怖抓手**: 姓名栏被反复涂改;某道题所有人的答案都一样，包括空题;红笔评语写着"此题只有前六排同学需要作答"。
**易错点**: 批注全在推进剧情;正常批改痕迹太少。

## 21. 家书/旧信
**字段**: 称谓、问候、正文、落款、日期、邮戳。
**恐怖抓手**: 字迹到后半页逐渐变成另一种字体;信里反复叮嘱"收到后把这封信烧掉，不要给第三个人看";信封上的寄出日期是 30 年后。
**易错点**: 文言过度;内容太密没有日常。

## 22. 审讯笔录/警方报告
**字段**: 案件编号、当事人、时间、问答记录、签字、涂改。
**恐怖抓手**: 嫌疑人描述的"室友"在警方的户籍系统里不存在;笔录第 14 页被整页涂黑，第 15 页开头是"以上内容已由当事人确认";问讯人对同一问题的回答每次都不一样。
**易错点**: 问询双方都太配合;缺乏笔录的机械重复感。

## 23. 招聘启事/入职协议
**字段**: 岗位、职责、薪资、条款编号、签字页、附件。
**恐怖抓手**: 合同第 47 条小字写着"离职时须归还门禁卡、工牌及上岗期间的记忆";招聘页面的"工作地点"在面试后被划掉改写。
**易错点**: 条款太显眼;不像是被翻到角落发现的。

## 24. 群公告+撤回消息
**字段**: 公告正文、@所有人、撤回记录、历史回执、成员列表。
**恐怖抓手**: 群公告在凌晨 3:17 被修改，修改人一栏是空;被撤回的消息在公告里仍以"已删除"占位显示;成员列表显示 41 人，但只有 3 个人在群里说过话。
**易错点**: 撤回记录解释得太清楚，没有留白。

## 25. 网站条款/隐私政策
**字段**: 条款编号、生效日期、勾选框、更新日志、附录。
**恐怖抓手**: 第 4 页条款说"本协议自您阅读本条时生效";更新日志显示今天的修订在您第一次打开页面之前;附录里的免责声明列出的服务本项目从未提供过。
**易错点**: 条款太短，缺乏真实条款的冗长感。

---

## 渠道适配 (Platform Adaptation)

同一怪谈换渠道要换皮，不是原文直发:

| 渠道 | 形态 | 节奏 | 语言特征 |
|------|------|------|---------|
| 贴吧/A岛 | 帖子+楼层 | 主楼短，靠回帖补信息 | "lz""前排""细思极恐";楼主是当事人 |
| 知乎 | 问题+回答 | 开头给结论，证据链展开 | 问答体;"写这个回答的时候" |
| 小红书 | 图文笔记 | 短句+分段+话题标签 | 生活化，情绪词，字数少 |
| 公众号 | 长文 | 段落标题分隔 | 克制叙述，少量排版 |
| B站 | 弹幕+简介+评论区 | 视频文本/时间戳 | 弹幕互动，评论区补设定 |
| 番茄短篇 | 叙事正文 | 强钩子开头，短段落 | 规则+人物动作，章末钩子 |
| 群聊/直播 | 即时消息 | 一问一答 | 口语，错字，撤回 |

渠道规则:平台限制就是格式的一部分(小红书 1000 字内→分篇连载;知乎回答的
"更新"追加在结尾→制造时间差恐怖)。选渠道要配格式，不要一个文档打天下。

---

# 附录 C：连载引擎 (Mode C: 单篇 → 世界观)

## 为什么单篇设定卡不够

单篇怪谈的设定卡可以一次性设计完。连载不同:写到第 20 集时，作者记不清
某条规则的适用条件、某个角色知道哪些信息、某件物品是否出现过。规则怪谈
的吸引力来自**持续兑现的悬念**，不是不断增加规则数量。规则会过期、角色
的知情度会变化、线索必须被回收——这些只能用结构化的 canon 管理。

本附录给出"五类节点卡 + canon sheet + 每集检查"的最小可行流程。

## 一、五类节点卡

把设定拆成五类节点，每类一张表:

| 节点 | 关键字段 |
|------|---------|
| 人物 | 已知信息、能力、目标、当前状态、污染阶段、知情边界 |
| 规则 | 触发条件、例外、代价、有效期(哪集到哪集)、已知者 |
| 线索 | 首次出现集、关联人物/地点、当前状态、计划回收集 |
| 地点 | 出现条件、关联事件、危险等级、当前状态 |
| 章节/集 | 目标、冲突、伏笔、回收项、本集新增 |

一条"乘客不得提前说出目的地"的规则，不能只写在某一集里。它还要关联:
适用的订单、违反后的后果、主角是否知情、是否与主线线索有关。

## 二、canon sheet 维护流程

每写完一集，更新下列表(建议 Markdown 表格，量大转 JSON):

1. **规则登记表**: 新规则入表，记触发条件/例外/代价/有效期/已知者。
   被推翻或修订的规则标记"已作废，第X集"——后文引用作废规则就是穿帮。
2. **线索状态表**: 每条线索标 开放/推进/回收/逾期。超过 N 集未推进的线索
   要么安排回收，要么明确降级为背景设定。
3. **角色知情表**: 逐角色记录"ta 知道什么、不知道什么、相信什么错的东西"。
   这是防止"角色提前知道不该知道的信息"的唯一办法。
4. **伏笔回收计划**: 列出每个伏笔计划在哪些集回收，写在下一集大纲里。

## 三、单元任务分工

单篇的文档各有任务(建立/误判/推进/揭示/动摇);连载的每一集也要有任务:

- **建立**: 引入一条新规则或一个新概念节点，读者学会用它。
- **误判**: 给出一个看似合理的解释，下一集推翻。
- **推进**: 主线线索前进一格(不一定是真相，可以是新问题)。
- **揭示**: 回收一个伏笔，或展示某个机制的全貌。
- **动摇**: 之前可信的阵营/文档露出破绽——规则系统开始腐败。

一个单元故事只有"再来一次惊吓"是失败任务。30 张订单卡，每张都要有分工:
有的建立规则，有的制造误判，有的推进妹妹线索，有的揭示平台也受规则限制。

## 四、跨篇一致性检查(每集交付前)

把当前集摘要与 canon sheet 一起过四问:

1. **角色知情边界**: 这个角色现在知道的东西，是否符合他经历过的事情?
2. **规则有效期**: 有没有把已作废/已过期的规则当有效规则用?
3. **线索状态**: 本集用到的线索是否登记过?回收的是不是该回收的?
4. **伏笔回收**: 计划回收的伏笔是否落实?逾期未动的线索是否处理?

输出"矛盾 / 待确认 / 可回收项"三类清单。矛盾必须修;待确认是作者故意
的误导(保留但标记);可回收项排进未来大纲。**模型负责查漏，作者负责制造
意外**——"这是不是好反转"永远由作者判断。

## 五、canon sheet 与读者的边界

canon sheet 是作者工具，不是作品的一部分:
- 默认不输出;用户明确要求时，作为独立文件交付(Markdown/JSON)，绝不混进读者正文。
- 交付格式建议:一集一个文件夹(`ep04-rules.md` 规则表 / `ep04-clues.md`
  线索表 / `ep04-characters.md` 知情表)，主索引 `canon.md`。

## 六、连载常见崩盘点

- **设定漂移**: 写到 30 集后规则条件变了没人发现 → 靠规则登记表兜底。
- **重复惊吓**: 每集都是"乘客异常→违规→逃离" → 靠单元任务分工打破。
- **主线停滞**: 支线铺太多，核心问题不推进 → 每集检查主线推进项。
- **万能解释**: 后期为了圆设定发明"其实一切是X" → 底层隐喻必须在前 1/3
  就埋下物理化的概念节点。
- **知情爆炸**: 角色在事件外获得信息 → 严格按角色知情表写作。

---

# 附录 D：叙事融合 (Mode B: 规则 + 主角破局)

## 定位

经典规则怪谈(模式A)只给"被发现的文档"，读者自己拼图。叙事融合(Mode B)让一个
主角活在规则局里:规则仍然具体、仍然不解释本质，但读者跟着主角的动作、试错、
破局前进。适合短篇平台(番茄/知乎/小红书)，核心卖点是**追读感**——读者想
知道"下一条规则是什么，主角怎么活"。

一句话概括:
**把最熟悉的生活场景变成会杀人的规则局，再让主角用身份、常识、民俗或反套路
理解，把规则从死亡陷阱变成破局点。**

## 与模式A的分工

- 模式A: 恐怖来自"读者发现文档之间矛盾"的智力活动。
- 模式B: 恐怖来自"读者和主角一起判断哪条规则能信"的生存压力。
- 模式B仍然遵守本 SKILL 的设定卡、概念节点、留白铁律。规则不能因为有了故事
  就变直白——最知情的角色也只能描述行为，不能陈述本质。

## 一、RSP 选题质检

动笔前用三个问题检验选题，两项及格才写:

- **R (Rule)**: 有没有一条具体、可执行、让人立刻紧张的规则?("先别在答题卡上
  写名字"✓ "这里很危险"✗)
- **S (Scene)**: 场景是否足够熟悉?宿舍、考场、办公室、灵堂、地铁、家族饭局
  都比古堡荒村好——读者每天在这些空间里。
- **P (Payoff)**: 破局点是否清楚?主角靠什么活下来?没有破局点的怪谈只是
  主角被吓到结尾。

## 二、九种叙事原型

正文结构先归原型，再定写法重心:

| 原型 | 核心 | 例子 |
|------|------|------|
| 规则清单型 | 规则给了你，但规则可能骗你 | "以上规则中，有两条是假的" |
| 系统拉入型 | 普通生活被切进副本 | 倒计时、存活率、主线任务 |
| 日常异化型 | 本该熟悉的动作突然变危险 | 写名字、开门、敲门、照镜子 |
| 触发死亡型 | 有人不信规则，死给读者看 | 莽撞配角踩雷，血字更新 |
| 熟人破局型 | 恐怖NPC忽然变成长辈/熟人 | 红衣宿管说"你妈说你蹬被子" |
| 民俗反杀型 | 别人按现代逻辑死，主角按老规矩活 | 一轻两重敲门、礼金单数 |
| NPC反转型 | 主角是副本秩序的一部分 | 玩家以为她是工具，其实她才是中心 |
| 弹幕信息差型 | 观众知道一部分，主角知道另一部分 | 弹幕剧透、唱衰、问号刷屏 |
| 副本升级型 | 当前安全只是边缘 | 核心区开启、规则变异、倒计时 |

## 三、升恐四层(逐层展示)

不要一次报完所有谜底，按顺序升:

1. **异常**: 让读者知道这里不是普通场景(门后贴了十条规则)。
2. **规则**: 让读者知道什么动作会死(其中一条是"以上规则有两条是假的")。
3. **触发**: 让一个人或一件事验证规则的杀伤力(室友踩雷)。
4. **破局**: 让主角用另一套理解活下来(发现假规则是宿管写的，她认出了主角)。

每一层都要改变局势，让读者觉得"我以为这条够危险了，原来下一条更阴"。

## 四、破局逻辑五类

主角的破局必须从推理和证据里长出来，不能作者开挂:

| 类型 | 机制 | 要求 |
|------|------|------|
| 推理型 | 从死亡模式/规则组合反推真相 | 前文线索必须足量且可复查 |
| 博弈型 | 用规则冲突抵消规则惩罚 | 规则矛盾须在设定卡中有解释 |
| 反转型 | 规则的真正含义揭露 | 反转必须回扣前文细节 |
| 代价型 | 部分遵守、牺牲换信息 | 代价要具体，不能免费 |
| 信息差型 | 身份/渠道带来的额外知识 | 信息差来源要交代(职业/亲缘/弹幕) |

反套路提醒:主角不能有"看穿规则"的万能能力;规则不能被无限破解;遵守规则本身
也可以有代价;逃出去不一定结束。

## 五、节奏结构模板

```
【开头】强钩子:规则、血字、系统、撤回消息、熟人NPC —— 100-300 字内
【场景确认】地点/任务/人数/规则清单或第一条规则
【第一次压迫】高跟鞋停在门外/监考站到桌边/主人家端茶
【规则验证】有人踩雷、血字出现、弹幕解释、系统警报
【主角判断】发现漏洞、身份关系、民俗逻辑或信息差
【反差破局】开门认亲、按规矩通关、拒绝签名、身份反转
【新危机】规则变异、核心区开启、熟人身份更大
【段尾钩子】一句新规则/系统警报/熟人台词收束
```

数字建议(可调):单篇 6000-12000 字;开头 100-300 字打出核心钩子;
每 800-1200 字一次规则触发或信息反转;规则不要堆太密，每条都要在剧情中
被验证或制造选择。

## 六、四层自检体系

成稿后必须跑完四层:

**L1 硬性规则**: 第一屏有强钩子?至少一条可见规则+一次可见兑现?
无大段世界观开头、无连续三屏纯氛围无规则、无"我很害怕"空泛心理堆叠?

**L2 风格一致**: 短段落高频换气?规则具体可执行?反转能回扣前文?
恐怖落在物件/声音/动作上而非形容词?

**L3 内容质量**: 真假规则、文字陷阱、时间条件前后一致?主角有主动判断，
不被系统/弹幕推着走?破局依赖前文信息而非作者开挂?代价与风险匹配?

**L4 追读感**: 读完还想看下一条规则/下一个死人/下一次反转?
有没有让人想跳过的一段?结尾是否泄气?

## 七、恐怖/喜剧比例(人的决策)

同一个规则可以写成阴森求生，也可以写成恐怖喜剧("宿管是我大姨")。比例由作者
决定，AI 只给候选。写完必须确认:主角底层人格、破局尺度、规则严谨度、
恐怖边界(死亡/儿童/民俗素材要谨慎，压迫不等于猎奇)。

## 禁区速查

- 慢热世界观开头 ✗
- 规则空泛("不要违反规则") ✗
- 只吓不破局，主角一直逃跑 ✗
- 为反转随意改规则条件 ✗
- 熟人梗还没建立压迫感就认亲 ✗
- 民俗规矩写成百科全书科普 ✗
- 结尾硬讲道理("规则就是人生") ✗

---

# 附录 E：元怪谈 (Mode F: 恐怖越过文档边界)

## 定义

常规怪谈的恐怖来自规则内容。元怪谈的恐怖来自**文本/规则系统本身超出它
应有的边界**:文档会变、规则会传播、读者会成为故事的一部分。元元素是
加成，不是替代——先保证常规怪谈基底成立(设定卡、概念节点、留白)，再
叠一个元元素。

铁律:**每篇只用一个元元素**。两个以上就变成炫技，读者不再害怕。

## 技法 1: 文档自变

文档在读者阅读过程中发生变化，但文本从不声明"它在变":
- 同一份守则，前后两次阅读时条款数量不同(第二次多出一条，多出的那条
  恰好针对读者刚才的想法)。
- 第 17 版守则否定第 15 版，而第 15 版从未在别处出现过——版本号本身
  在撒谎。
- 文件末尾的落款日期晚于读者看到这份文件的日期。

实现提示:通过版本号、修订标记、"本版新增"栏目制造可复查的差异。
不要写"这份文件正在变化"。

## 技法 2: 规则影响读者

规则的生效范围从虚构角色延伸到读者自己:
- 规则说"读到本条的读者请勿在今晚 3:17 看向窗外"——读者的现实动作被
  规则接管。
- 规则的完成时态:文件写"你已经看过了"，而读者确实正在看。

实现提示:用"你"和完成时，把读者的阅读行为变成规则的前提。保持虚构
边界:如果涉及现实世界动作，必须是完全无害的(不看窗外)，不能诱导
危险行为。

## 技法 3: 传播即污染

规则会自我复制，转发就是传播:
- 评论区/群聊里出现新规则，发布者声称"刚看到的"。
- 文档末尾的转发要求藏在正常的"请勿外传"里，而副本数在增加。
- 下一集的怪谈里，上一集的读者留言变成了设定的一部分。

实现提示:适合连载(规则会在集与集之间扩散)和多平台发布(每个平台的
副本状态不同)。

## 技法 4: 渠道即叙事

平台边界就是世界边界:
- 同一个怪谈在 A 平台发布的版本缺了一页，B 平台补全了被删的部分，而
  A 平台随即"更新"出新的缺失。
- 官方的删除通知与怪谈的扩散互相印证——越删越多。

实现提示:适合 Mode E 线索包联动。发布时有意让不同渠道的版本有微小
差异，并在后续版本里让这些差异成为线索。

## 技法 5: 真实性伪造

用证据链制造"这是真的"的错觉:
- 截图时间戳、设备型号、GPS 轨迹、搜索记录等元数据比正文更有说服力。
- 一份"被涂改过的文件"的涂改本身讲述另一个故事。

实现提示:详见附录 B 各格式的字段。真实性是元怪谈的燃料。

## 伦理边界(必须遵守)

- 不制造真实恐慌:元怪谈不能伪装成真实的官方通知、灾情信息或医疗警告。
- 现实锚点必须虚构化或明显可辨识为创作;涉及真实机构/地名先脱敏。
- 不诱导危险行为;不诱导读者骚扰他人;不伪造可能影响声誉的信息。
- 平台发布的"删除/更新"戏码要可控，不能真的欺骗用户或平台。

## 质检

- [ ] 常规怪谈基底独立成立(去掉元元素，故事依然恐怖)?
- [ ] 元元素只有一处?
- [ ] 元效果来自结构(版本/渠道/时间)，不是旁白声明?
- [ ] 读者可以在重读时发现元元素，而不是第一遍就被"剧透"?
- [ ] 伦理边界全部满足?

---

# 附录 F：相邻类型桥接 (Adjacent Genres)

规则怪谈不是孤岛。SCP、后室、ARG、伪纪录片、都市社会派怪谈、反差治愈系
都共享"日常被规则异化"的基因。本附录给每种类型提炼可借鉴的技法、如何
折进规则怪谈、以及禁区。

## 一、SCP / 认知危害

**借鉴点**:
- "展示而非告知"的极致化:文档永远不写"它很可怕"，读者自己得出这个结论。
- 认知危害:某个条目在你反复阅读时发生变化——文档本身是异常的一部分。
- 收容与失效:异常能被描述，但收容条件永远可以被打破。

**折进规则怪谈**:
- 让"知道规则"本身就是风险:越理解，越容易被选中(本 SKILL 的
  "认知即污染"一脉相承)。
- 用"版本自变"做元怪谈:第 17 版守则否定 15 版，读者发现规则系统自己在
  演(见附录 E 技法 1)。

**禁区**: 技术腔过度(专用名词轰炸会失去中式怪谈的日常感);用"权限等级"
掩盖逻辑漏洞。

## 二、后室 / 阈限空间

**借鉴点**:
- 威胁指数:给地点一个量化危险等级，让读者第一眼建立判断，再被打破。
- 空间错位:熟悉的地方出现不熟悉的结构(多出来的门、不存在的楼层)。
- 一致性铁律:内部必须自洽，不能靠"反正是超空间"糊弄。

**折进规则怪谈**:
- 把"空间边界"做成概念节点:门、楼层、走廊长度都是可数可测的物理对象。
- 用楼层平面图/地图做结构组织原则(长篇模式的"结构组织原则"选项)。

**禁区**: 只堆 liminal 氛围没有规则;无限循环解释一切(循环要有代价)。

## 三、ARG(替代现实游戏)

**借鉴点**:
- 现实锚点:规则藏在真实可验证的载体里(网站、电话、地图、邮箱)，
  参与感来自"我真的能找到下一个线索"。
- 跨渠道叙事:不同平台承载不同阵营的信息，平台边界就是世界边界。
- 时间驱动:线索按真实时间放出，等待本身是叙事的一部分。

**折进规则怪谈**: 对应 Mode E 线索包。聊天截图、物流轨迹、门禁记录、
语音转写各自成一条线，读者跨平台拼图。

**禁区**: 不能骗到真人/造成真实恐慌;真实世界锚点必须明显虚构或脱敏;
不诱导读者做危险动作(如半夜去某个地点)。

## 四、伪纪录片

**借鉴点**:
- 转写体:纪录片把"镜头记录"转成文字时，声音和画面的偏差本身就是信息。
- 资料质感:受访者口吻、档案画质、时间码的不连续。

**折进规则怪谈**:
- 语音转文字记录 + 监控值班日志(见附录 B 第 6/9 条)。
- "录像丢失的那 7 分钟"在文字版里表现为缺失的日志条目。

**禁区**: 只在装帧上像纪录片，内容仍是小说腔;转写太干净、标注太刻意。

## 五、都市社会派怪谈

**借鉴点**:
- 规则的背后是系统性压迫:工厂的"水不可饮用"、公司的"离职归还记忆"，
  异常是社会创伤的隐喻。
- 恐怖不靠超自然，靠制度:裁员、拆迁、996、空巢——规则本身就是加害者。

**折进规则怪谈**:
- 让"管理方"成为真正的反派阵营，异常只是管理手段的延伸。
- 底层隐喻层(见 Step 2 真相谱系)可以落在一个真实历史/社会事件上，
  但文档里永不点破。

**禁区**: 说教(规则怪谈不是社论);消费苦难(创伤隐喻要克制、要具体，
  不能拿真实灾难当装饰)。

## 六、反差治愈系 / 恐怖喜剧

**借鉴点**:
- 反差记忆点:恐怖规则 + 日常温情 = 读者忘不掉的场景。
- 规则伤害能力降低:恐怖可以变成"麻烦"，重点转移到人和人的关系。

**折进规则怪谈**: Mode B 的熟人破局型。"宿管是我大姨"式破局需要
先建立压迫感再反转，顺序反了恐怖感会塌。

**禁区**: 纯搞笑(失去怪谈质感);恐怖感提前崩塌;反差用一次是记忆点，
用三次是套路。

## 桥接选择表

| 想要的效果 | 借用类型 | 落到哪个模式 |
|-----------|---------|-------------|
| 文档随阅读改变 | SCP 认知危害 | F 元怪谈 |
| 空间拼图/危险量化 | 后室 | A 经典/C 连载 |
| 读者真的去解谜 | ARG | E 线索包 |
| 资料真实感 | 伪纪录片 | A 经典(格式库) |
| 社会批判厚度 | 社会派 | A 经典(真相谱系) |
| 反差记忆点/轻恐怖 | 治愈系喜剧 | B 叙事融合 |

---

# 附录 G：机械校验清单 (替代 check_rules.py)

> 此处等价于原 `scripts/check_rules.py` 的全部 13 项检查，改为人工执行。
> 用法：写完正文后，逐条扫一遍。**硬错误清零才算通过。**

```
1.  句子长度    : 两个标点之间 >24 字 → 错误;>20 字 → 警告
2.  "请"字密度  : 含"请"的规则行 > 规则行总数÷5+1 → 警告
3.  AI 连接词   : 值得一提的是/综上所述/总而言之/需要注意的是/请务必注意/
                  特别提醒/以确保/为了避免/换句话说/不难发现/不得不说/你会发现 → 错误
4.  弱动词      : 进行/实施/加以/作出/给予 → 错误
5.  "的"字链    : 同一句 ≥3 个"的" → 警告
6.  破折号      : 全文"——" >3 处 → 警告
7.  三项并列    : 同一句 ≥2 个顿号 → 警告
8.  连续条件句  : 连续 ≥3 行以 如/如果/当/若 开头 → 错误
9.  孤立祈使句  : 不要。/不要看。/不要听。/别去。/别看。/别听。/没有。/
                  不解释。/快跑。/活下去。 → 错误
10. 孤儿规则    : 未提及任一概念节点的规则行 >60% → 错误;>40% → 警告
11. 黑名单桥段  : 不要回头/不要相信任何人/镜子里的你不是你/所有人都已经死了 → 错误
12. AI 平衡句式 : "不是…而是…" → 错误;同句"不是"+"是" → 警告(人工复核)
13. 序列套路    : 全文同时出现 首先/其次/最后 → 警告
```

机械校验抓的是眼睛会放过的技术性失误，**不能替代** Step 4 A/B/C 的
设定卡/因果/线索可达性人工审查。

---

# 附录 H：反套路清单 + 烂俗桥段黑名单

## 一、21 条误区速查

| # | 误区 | 表现 | 正确做法 |
|---|------|------|---------|
| 1 | 规则堆砌成说明书 | 开头甩十几条红色大字规则，没节奏 | 规则逐步展开，前几条看起来正常，异常慢慢渗透 |
| 2 | 规则太多太满 | 单份文档 >15 条 | 单份 8-15 条;多文档总数 ≤30;多的拆到别的文档/阵营 |
| 3 | 过度解释 | 描述"它"的外貌习性来源;附"真相解析" | 永远不解释"为什么"，只给"怎么做" |
| 4 | 依赖血腥/怪物 | "地上全是血""怪物有三只眼睛" | 用暗示:"地面最近做了深色重新铺设，不要询问铺设材料的来源" |
| 5 | 情绪过载无缓冲 | 每条规则都生死攸关，直线上升 | 穿插安全区和日常细节;恐怖程度波浪起伏 |
| 6 | 内部逻辑崩坏 | 规则A说某时间安全，规则B在同一时间安排危险事件 | Step 4 逻辑校验逐条执行 |
| 7 | AI 生成套路 | 以"最后，请记住..."结尾;大量"并/且/以及" | Step 6 严格执行;结尾戛然而止 |
| 8 | 直白陈述异常本质 | "雾是活的""他们已经死了"，连内部文档也这么说 | **所有**文档只描述行为:✗"雾是活的" → ✓"雾会等你。你不出门它就在窗外挂着。" |
| 9 | 万能保护物品 | "握紧铁器就行了" | 必须有代价/边界:握太久手失去温度;对已违反规则X的人无效 |
| 10 | 抽象概念节点 | "B849.1类索书号""异常""频率""信号" | 全部换成物理对象:兔子血、瓷砖缝、白手套上的灰斑、水、铁器 |
| 11 | 恐怖天花板太低 | 最坏结果是"感到不安""做噩梦" | 必须涉及身份替代/永久困住/认知不可逆损毁/被置换 |
| 12 | 实体是传统物理威胁 | 靠物理接触/空间接近攻击 | 首选"认知即污染":了解本身就是感染途径 |
| 13 | 文档"叙事化" | 读起来像微型小说，有人物弧光情感高潮 | 文档是"被发现的物件"，不是故事;作者不知道别的文档说了什么 |
| 14 | 陈述违反规则的后果 | "否则你会看到不该看的东西" | 永远不说。✓"握紧墙上的铁质装饰品。等冲动过去。天亮后再做决定。" |
| 15 | 公文"请"字泛滥 | 每条规则都以"请"开头 | 每5条≤1个"请";用须/应/不得/禁止/严禁/勿 |
| 16 | 字条写成编号列表 | 便利贴上出现整洁的"1. 2. 3. 4." | 碎片、跳跃、涂改、突然换话题、半截句子 |
| 17 | 文本太干净 | 完整无缺、字迹工整、无水渍无撕页 | 每份文档最多一处缺陷:水渍/涂改/撕页/字迹变化/日期矛盾 |
| 18 | 句式千篇一律 | 全是"如X，请Y" | 混用五种句式;同一句式不得连续3次以上 |
| 19 | 句子太长 | 两个标点之间 >20 字 | 15-20字断句;相邻句长短相差 >5字 |
| 20 | 翻译腔三件套 | 滥用"的"/弱动词/"不是…而是…" | 删"的"、删弱动词、"不是A而是B"→直接说B |
| 21 | 缺行业真实用语 | 公文像"翻译成中文的外国文件" | 用对术语:便利店(唱收唱付/先进先出/理货/排面/盘点/报损)、物业(报修/巡查/台账/责令/限期整改)、图书馆(编目/上架/剔旧/索书号/馆藏) |

## 二、烂俗桥段黑名单

以下桥段已被无数作品用烂，创作时必须避免（除非你能做出真正新颖的反转）:

1. **"第X条规则不存在"** — 已经被用到失去任何恐怖感
2. **"不要回头"** — 太泛，没有任何信息量
3. **"他们/它们不是人"** — 直接把恐怖说出来了，破坏留白
4. **"如果你看到了这条规则，说明你已经..."** — 老套
5. **午夜/凌晨3点是特殊时间** — 可以用但需要新颖的具体时间（如3:17、2:22）
6. **镜子里看不到自己** — 太常见
7. **所有人其实都已经死了** — 老套的终极反转
8. **结尾"快跑""活下去""不要相信任何人"** — 情感宣泄，消解了冷静的恐怖
9. **规则最后一条是"不要遵守以上任何规则"** — 不负责任的偷懒写法
10. **动辄"立刻离开""立刻逃跑"** — 好的规则怪谈中，异常是可以回避的，规则是用来保护你的

## 三、质量检查清单（Step 5 逐项过）

### 一票否决项
- [ ] **恐怖天花板**: 推完所有线索后最坏结果涉及身份替代/永久困住/认知不可逆损毁/被置换?否则回 Step 2 重做。
- [ ] **认知即污染**: 污染机制与认知行为绑定(看到/读到/理解/认出)?存在"知道越多越危险"悖论?
- [ ] **概念节点物理性 + 符号体系**: 全部是物理对象?每个节点对应污染进程的特定阶段?零抽象编码/分类?

### 恐怖感
- [ ] ≥3 处需要读者自己推理才能体会到的恐怖点?
- [ ] 有一处让读者产生"等等，那如果...的话岂不是..."的自我追问?
- [ ] 读完全文后有"回看前面，细思极恐"的效果?

### 语言
- [ ] 官方文档用了公文惯用语(本/须/应/不得/经/予以)?
- [ ] "请"字每5条规则 ≤1 次?
- [ ] ≥3 种不同句式(祈使短句/条件+指令/纯粹禁令/定义+限制/无主语句)?
- [ ] 字条类文档碎片化、无编号、口语化?
- [ ] 至少一处文本"不完美"(水渍/涂改/撕页/字迹变化)?
- [ ] AI连接词全部删除?结尾戛然而止?
- [ ] 至少一条规则让读者觉得"这是我想不到的设定"?
- [ ] 黑名单桥段全部避开?

### 逻辑
- [ ] 所有规则矛盾在隐藏设定卡中有合理解释?
- [ ] 规则推导可追溯(每条规则 ← 对应设定)?
- [ ] 多条规则之间存在隐含因果关系，而非孤立列表?
- [ ] 保护物品有明确局限性?无"万能解药"?

### 留白
- [ ] ≥30% 关键信息处于 L2 或 L3 披露层级?
- [ ] 存在读者可自行拼凑、文本从未明说的"隐藏故事"?
- [ ] "它"或等价实体从未被直接描述?
- [ ] 所有文档——包括最知情的纸条/日记——都是行为描述而非本质陈述?

### 耦合
- [ ] 核心概念节点 ≤4 个?
- [ ] ≥60% 规则涉及核心概念节点?
- [ ] 概念节点之间有明确关联关系，而非各自孤立?
- [ ] 无"孤儿规则"?

### 信息增量（多文档时）
- [ ] 每份文档贡献了其他文档没有的新信息?
- [ ] 无文档只是复读/加强已有信息?
- [ ] 文档之间存在真正的矛盾，而非只有知情度递增?
