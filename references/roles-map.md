# 角色全景与出处

这份文件回答两个问题：**一个开发团队有哪些角色**，以及**本 skill 的九个角色为什么这样划分**。

角色划分不是凭感觉编的。下面的每一条都取自被行业认可的实践，出处附在文末。

## 一、按职能分组的角色

### 发现与定义 —— 做什么、为什么

| 角色 | 职责 | 出处 |
|---|---|---|
| Product Owner | 排序工作、决定价值与优先级 | Scrum（团队三大职责之一） |
| Customer | 提需求、定优先级、**验收** | XP：要求"始终在场"，**是团队成员** |
| Shaper | 划定问题范围、定 appetite（愿意花多少时间） | Shape Up |
| UX / Designer | 交互与视觉 | Shape Up 的固定成员；Google 团队常见 |
| End User / Usability Participant | 只通过公开产品入口完成真实任务，暴露可发现性、操作成本和恢复问题 | W3C WAI 的用户参与评估实践 |
| BA / SME | 需求细化、领域知识 | 通识，最小团队里被前几者吸收 |

### 结构与技术方向 —— 怎么做、边界在哪

| 角色 | 职责 | 出处 |
|---|---|---|
| Tech Lead | 定技术方向、拆解、技术决策 | Google：与 Manager **并列的两种领导角色**，多数 TL 仍是 IC |
| Manager / EM | 人的绩效、产出、成长 | Google |
| Architect | 结构、接口、非功能约束、跨团队一致性 | 通识（Solution → Enterprise → Chief 的阶梯） |
| Program Manager | 流程、协调、进度 | Google：辅助 TL/EM |

### 实现

| 角色 | 职责 | 出处 |
|---|---|---|
| Programmer / Developer | 把东西做出来 | Shape Up 就叫 programmer；Scrum 的 Developers |
| Data / Platform / DevOps | 数据、平台、交付流水线 | 通识，小团队里由工程师兼 |

### 质量与对抗 —— 证明它不成立

| 角色 | 职责 | 出处 |
|---|---|---|
| Tester / QA | 尝试破坏 | **XP 有独立的 Tester 角色**；Scrum 把质量放进 Definition of Done |
| Reviewer | 以非作者视角审查 | **Google 强制 code review**；XP 用结对编程 |
| Coach / Tracker | 流程守护与进度跟踪 | XP |
| Scrum Master | 保障流程被遵守 | Scrum 三大职责之一 |
| Security / Performance | 专项对抗 | 通识，按需 |

### 运行

| 角色 | 职责 | 出处 |
|---|---|---|
| SRE / On-call | 可靠性、可观测性、故障响应 | Google 独立职能 |
| Release / Incident | 版本发布、回滚、事故指挥 | 通识，小团队由工程师兼 |

### 协作结构（不是个体角色）

Team Topologies 描述的是团队**类型**与**交互模式**，不是个人角色，但对"该怎么和既有系统相处"很有用：

- 四种团队类型：stream-aligned / platform / enabling / complicated-subsystem
- 三种交互模式：**Collaboration**（一起探索）／**X-as-a-Service**（消费现成的）／**Facilitating**（临时被指导）

面对既有组件时先判断属于哪种交互：**消费它**、**和它一起改**、还是**先被它教一遍**——
这决定了你要读多少、改多少。

## 二、三条共识

**1. 最小可行团队是 2–3 人，角色必然合并。**
Scrum 说团队"small enough to remain nimble"，通常 ≤10 人，且越小沟通越好；
Shape Up 的最小可交付单元是**1 名 designer + 1–2 名 programmer**；
Google 说小团队"**默认是 TLM**：一个人同时承担人的需求与技术的需求"。

**2. 定义权必须独立于实现权。**
Scrum 单设 Product Owner；XP 把 Customer 放进团队并要求"始终在场"；Shape Up 单设 Shaper。
三个来源用三种办法做同一件事：**不让写代码的人独自决定做什么**。

**3. 独立挑战能发现作者共享盲点。**
XP 设独立 Tester 并用结对编程；Google 要求 code review，关键在“**非作者**”；
Scrum 把质量写成 Definition of Done 由团队共担。
共同的判断不是“作者证据一律无效”，而是：作者测试能证明已观察到的行为，
却不能证明作者没有遗漏；风险越高，越需要非作者视角。

## 三、从角色到本 skill 的九个角色

按角色所需视角分三类，这是划分的核心依据：

| 类别 | 特征 | 能否合并 | 本 skill 的处理 |
|---|---|---|---|
| **能力型**：Architect、Engineer、DBA、UX、Writer | 区别在"知道什么" | ✅ 可合并 | 归入角色 1/2/3/4/7/8，由同一 agent 按顺序承担 |
| **对抗型**：Tester、Reviewer、Security、SRE/on-call 中的怀疑面 | 区别在**激励相反** | ⚠️ 作者可自查，但不能冒充独立视角 | 角色 5/6 按风险引入独立 agent |
| **体验型**：最终用户、可用性测试参与者 | 实现知识会污染发现过程 | ❌ 不能由开发者扮演 | 角色 9 使用多个新上下文的用户 agent，只接触公开产品入口 |

因此九个角色里，5 与 6 对独立性最敏感，但不应让低风险任务为了形式强制派发。
轻档允许作者自查；标准档在契约、共享状态或共同盲点明显时使用一个独立挑战者；
高风险档在环境支持时要求独立验证与复查。角色 1 的独立性不同——它要求把业务定义权
交给用户，同时保留工程方应承担的技术判断。角色 9 也不同：它不是寻找实现缺陷，而是
观察一个不知道内部结构的人能否只靠公开工具顺利完成目标。面向用户的产品实现后，应由
至少两个彼此独立的用户 agent 体验；开发者、验证者或已读过源码的 agent 不能替代。

| 本 skill 的角色 | 吸收了哪些职能 |
|---|---|
| 1 定义 | Product Owner、Shaper、BA、Customer(XP) |
| 2 架构 | Solution/Enterprise Architect 的落地侧、Tech Lead 的技术方向 |
| 3 计划 | Tech Lead 的拆解、Program Manager |
| 4 实现 | Programmer / Developer、Data / Platform Engineer |
| 5 验证 | Tester / QA / SDET、Security / Performance 的对抗面 |
| 6 复查 | Code Reviewer（必须非作者） |
| 7 运行 | SRE、Release Manager、Incident 角色 |
| 8 交付 | Technical Writer、Release Manager 的发布说明面 |
| 9 用户体验 | End User、Usability Testing Participant；只操作公开产品入口 |
| —— | Scrum Master / Coach 不单列：它分散为四条铁律与分诊 |

## 出处

- Scrum Guide（2020，Schwaber & Sutherland）：<https://scrumguides.org/scrum-guide.html>
- Basecamp / 37signals, *Shape Up*：<https://basecamp.com/shapeup/1.2-chapter-03>
- *Software Engineering at Google*, Ch.5 "How to Lead a Team"：<https://abseil.io/resources/swe-book/html/ch05.html>
- Extreme Programming（角色与客户在场要求）：<http://www.extremeprogramming.org/rules/customer.html>
- Team Topologies（团队类型与交互模式）：<https://teamtopologies.com/key-concepts>
- Google SRE Book（可观测性、Toil、复盘）：<https://sre.google/sre-book/table-of-contents/>
- Michael Nygard, *Documenting Architecture Decisions*：<https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>
- ISTQB Certified Tester Foundation Level Syllabus（测试原则）：<https://istqb.org/certifications/certified-tester-foundation-level-ctfl-v4-0/>
- W3C WAI, *Involving Users in Evaluating Web Accessibility*：<https://www.w3.org/WAI/test-evaluate/involving-users/>
- SFDIPOT：James Bach 的 Heuristic Test Strategy Model
- Semantic Versioning：<https://semver.org/>

以上仅为**引用**，不转载原文。若后续需要把某段原文并入本 skill，再单独处理署名与许可。
