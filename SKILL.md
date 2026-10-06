---
name: rules-horror
description: This skill should be used when the user wants to generate Chinese rules horror
  stories (规则怪谈) — a genre where numbered rules create escalating supernatural horror
  through implication and contradiction. Triggers include: 规则怪谈, 写规则怪谈, 生成规则怪谈,
  规则类怪谈, 恐怖规则, rules horror, creepypasta rules, 续写规则怪谈, 规则怪谈连载,
  互动规则怪谈, 规则怪谈线索, ARG, 叙事型规则怪谈. The skill produces authentic Chinese
  rules horror with strict disclosure control and internal logic consistency, supports six
  generation modes (classic documents, narrative-fusion, serialized canon, interactive,
  clue-package/ARG, and meta-horror).
---

# Rules Horror Generator (规则怪谈)

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

Mode A/B/C 共享本 SKILL 的六步工作流。Mode D/E/F 在六步工作流上叠加各自专用规则
(见 `references/narrative-modes.md`、`references/serialization.md`、
`references/adjacent-genres.md`、`references/meta-horror.md`)。

**强度拨盘 (Intensity Dial)**:用户可指定 1-5。1=细思极恐的日常不适(可发朋友圈),
3=传统怪谈恐怖(默认),5=认知崩解的深层恐惧。强度影响恐怖天花板的设计高度、
留白比例和语言克制度——强度越高,越要克制,越不能用血腥。

**输出渠道 (Platform)**:贴吧/A岛/知乎/小红书/公众号/B站弹幕/番茄短篇。
渠道决定格式、节奏和语言(见 `references/format-library.md` 渠道小节)。

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
  narrative+ rules. For non-classic formats (聊天记录/物流追踪/病历/监控日志/弹幕/语音转写...)
  read `references/format-library.md` and pick ONE format family before drafting.
- **Platform**: Infer from request or ask. 贴吧/A岛/知乎/小红书/公众号/B站/番茄.
- **Length**: User-specified or infer from request. Three modes. (See below)
- **Style**: Pick ONE style mode from `references/style-modes.md`:
  - **动物园式** — Cold bureaucratic. Horror from content, never tone. Fatal info hidden as afterthoughts. Occasional typos.
  - **大洛山式** — Folkloric dual-billboard. Old (wood) vs new (metal) signs. Chinese mythological vocabulary.
  - **二级学院式** — Heroic rules. Moral positions embedded in documents. Sacrifice and legacy themes.
  - **E市式** — Clinical emergency protocols. Language-as-defense. Rules admit their own corruption.
  - **糖果厂式** — Industrial trauma metaphor. Body horror via deprivation. Time-jumping documents.
  - **育英式** — Extreme minimalism. Three-word rules. Lists that end with impossible items.
  - Default for most everyday settings: 动物园式. Match style to the setting's natural voice.
  - Read `references/style-modes.md` before drafting for the chosen style's specific rhythm, vocabulary, and句式模板.

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
- Long-form SERIAL (连载): switch to Mode C and read `references/serialization.md`
  before Step 2 — you will design the canon sheet as a management artifact, not a
  single-piece setting card.

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
- For any format, read its entry in `references/format-library.md` BEFORE drafting —
  each format has real-world conventions (header fields, timestamps, jargon, layout
  artifacts) that make it believable, plus its own 恐怖抓手 and 易错点.
- Platform also dictates language: 贴吧/A岛 用"lz/前排/细思极恐"式帖文体,知乎用
  问答/专栏体,小红书用短句+emoji+话题标签,番茄用强钩子短段落。同一份怪谈换渠道
  要重新换皮,不能原文直发。

**Document information increment principle**: If using multiple documents, each document must contribute information NOT found in others. Documents should not merely confirm or repeat. Think of each document as a puzzle piece from a different angle — the reader needs all of them to see the full shape. A document that only reinforces existing rules is wasted.

**Protection limitation principle**: Every protective measure must have a boundary. Iron wards off X — but it drains body heat, or loses potency after repeated use, or doesn't work if you've already broken a specific rule. Never create a "universal solution" item. The reader should think "iron helps, but at what cost?" not "just hold iron and you're fine."

Escalation is organic, not formulaic. The reader should feel the ground shifting under their feet — not count the paragraphs until the next "scary rule." Some documents should be 90% normal with one wrong sentence. Some should start wrong and get worse.

Rules are written in **official document tone**: calm, procedural, bureaucratic. The contrast between mundane tone and disturbing content creates the horror.

### Step 4: Logic Verification

Run three checks on the draft:

**A. Forward derivation**: For each rule, ask: "Which element in the setting card justifies this rule?" If a rule can't be traced back — cut it or add the justification.

**B. Reverse check**: For each element in the setting card, ask: "Does at least one rule express this?" If an element has zero rules — either add a rule or accept it stays fully hidden (L3 disclosure).

**C. Contradiction audit**: Find all surface contradictions between rules. For each contradiction, verify the setting card has an explanation (different faction, different time, different cognitive state). If a contradiction has no explanation — fix the setting card or remove one side of the contradiction.

**D. Mechanical check (机械校验)**: Run the bundled checker on the finished text:

```bash
python scripts/check_rules.py 输出文件名.md --concepts "兔子血,山羊肉,海洋馆"
```

It scans for sentence length over 20 chars, "请" overuse (每 5 条 >1),
banned AI phrases (值得一提的是/综上所述/需要注意的是/不是…而是… etc.),
weak verbs (进行/实施/加以/作出), "的" chains, dash abuse, triple parallel lists,
three+ identical conditional patterns in a row, and orphan rules (lines mentioning
zero concept nodes, when --concepts is given). Fix every hard-error it reports.
Mechanical checks catch slips the eye forgives; they are NOT a substitute for the
manual canon/causality/clue-access review in A/B/C.

**E. Serial consistency (连载一致性, only Mode C)**: Before delivering a new episode,
load the canon sheet from `references/serialization.md` and check: 角色知情边界
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
- [ ] **创意**: No clichés — avoid the blacklist (see anti-patterns.md). Core concept nodes feel original.
- [ ] **逻辑**: All surface contradictions have hidden-setting explanations. Protective items have limitations. Hidden setting forms a complete, coherent narrative (因果闭环).
- [ ] **留白**: ≥30% of key information is L2 or L3 (not directly stated). Zero direct statements of anomalous nature in ANY document. **Zero stated consequences of rule-breaking.**
- [ ] **文档真实性**: Would a real person in this role actually write these sentences? No winking, no theatricality. Bureaucrats use euphemism. Victims understate.
- [ ] **规则源于事件**: Does each abnormal rule carry the weight of an unstated past incident? Would it read differently if the writer had personally witnessed the consequence?
- [ ] **撰写者有限视角**: Does each document reflect its writer's specific, limited knowledge — not the author's full setting card? Do factions have genuinely incompatible goals?
- [ ] **正常里掺异常**: Is the first document 40-50% genuinely normal rules? Can the reader read 3-4 rules before noticing anything is wrong?
- [ ] **语言**: See Step 6 for full rules. Key checks:
  - Official docs use 公文惯用语 (本/须/应/不得/经/予以), not "请" (max 1 per 5 rules)
  - Insider docs are fragmented, unnumbered, colloquial — real people don't write numbered lists on post-its
  - Sentences vary in length and pattern, not all "如X请Y"
  - At least one document has an imperfection (water damage/strikethrough/missing text)
  - Zero AI connector phrases. Endings are abrupt.
- [ ] **耦合**: Rules orbit 2-4 PHYSICAL concept nodes with high coupling density. Zero orphan rules.
- [ ] **信息增量**: If multi-document, each document contributes information not found in others. No document merely confirms another.
- [ ] **动态安全边界**: Does each protective measure have a specific, inferable collapse condition? Not just "sometimes unsafe" — readers should be able to reason about WHEN it fails.
- [ ] **无知即安全**: Does acquiring knowledge through reading later documents increase danger? Is the most knowledgeable writer the most contaminated?
- [ ] **文本考古学**: Do physical document traces (handwriting changes, torn pages, strikethroughs, margin notes) tell a story beyond the text itself?

**模式专项检查 (run for the selected mode, ignore others)**:
- [ ] **B 叙事融合**: 破局是否只依赖前文已展示的信息?(不能作者开挂) 每 800-1200 字
  是否有一次规则触发/信息反转/身份揭露? 结尾是否停在强钩子上而不是总结?
- [ ] **C 连载**: 本集是否完成了自己的单元任务? 五类节点卡是否已更新? 有无
  已到期未回收的线索? 新规则是否在 canon 中登记了触发条件/例外/代价/有效期?
- [ ] **D 互动**: 每次只回答当前问题/补充当下需要的规则,绝不提前泄露后续?
  用户的每个问题是否都能在设定卡中找到确定答案(允许"你不知道")?
- [ ] **E 线索包**: 每条线索的渠道是否符合该渠道的真实格式? 拼出的谜题是否有
  唯一可验证解?(允许故意歧义,但必须有至少一条可验证路径)
- [ ] **F 元怪谈**: 元层元素是否只有一处、且从不明说? 常规怪谈基底是否仍然成立
  (元怪谈是加成,不是替代)?

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

**删"的"**: 连续出现两个"的"→ 至少删一个。连续三个"的"→ 翻译腔确诊，拆句重写。

**删弱动词**: "进行""实施""加以""作出"→ 直接删掉，把真正的动词提上来。
- ✗ "对商品进行清点" → ✓ "清点商品"
- ✗ "对异常情况加以记录" → ✓ "记录异常情况"

**行业真实用语**: 每个场景有自己的一套术语。写之前搜一下真实文档——
- 便利店: 唱收唱付、先进先出、理货、排面、盘点、报废
- 物业: 报修、巡查、台账、责令整改、限期
- 图书馆: 编目、上架、剔旧、索书号、馆藏
- 用不对术语 = 第一句话就暴露是假的

**朗读测试**: 写完每份文档后逐条朗读。舒服 = 通过。拗口 = 重写。中文是短句的语言。"一个好句子念起来嘴舒服，耳朵舒服，心里也舒服。"（老舍）

**"请"字使用规则**: 每 5 条规则最多用 1 次"请"。其他地方用"须""应""勿""不得"。不是礼貌问题——是真实公文确实很少说"请"。

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
- **不是...是...** — The #1 AI marker. Negation-then-affirmation is AI's compulsion to "balance" every statement. Delete the negation half, keep only the affirmative. "那不是门，是别的什么" → "那扇门不对。" or just describe behavior.
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
- End documents abruptly — no "祝您..." or "谢谢配合"

**Imperfection principle**: Real found documents have flaws. Add ONE of:
- 被水浸模糊的半行字
- 涂改痕迹（~~划掉~~后改写）
- 撕去的页面/撕掉的半句话
- 字迹突然变化
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

