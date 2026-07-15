---
name: cfd-manual-qa-regression
description: 'Manual QA workflow for Contract for Difference (CFD) trading product releases: test planning, risk-based positive and negative test case design, full manual regression execution with efficiency tactics, release sign-off readiness, coverage tracking, and iterative app knowledge capture. Use when preparing or executing manual test cycles, refining a shared app profile from requirement docs, and reducing repetitive regression effort.'
argument-hint: 'Feature or release scope to test, risk areas, and timeline'
user-invocable: true
disable-model-invocation: false
---

# CFD Manual QA Regression
# CFD 手动 QA 回归测试

## What This Skill Produces
## 该 Skill 产出
- A focused manual test plan for the release scope
- Positive and negative test cases prioritized by risk
- A regression set split into must-run and conditional cases
- Coverage tracking against requirements and risk areas
- A clear sign-off recommendation with blockers and residual risks
- A reusable iterative skill update for the next run

**中文翻译：**
- 针对版本范围的聚焦性手动测试计划
- 按风险优先级排序的正向和负向测试用例
- 分为必须运行和条件运行的回归测试集合
- 针对需求和风险区域的覆盖追踪
- 包含阻碍项和残留风险的明确签字建议

## When to Use
## 使用时机
- Planning manual QA for a new CFD feature or release
- Building or refining test cases for critical trading flows (order lifecycle, pricing, P&L, margin, risk controls)
- Running regression under time constraints
- Preparing go or no-go QA sign-off before release
- Iterating a shared skill from a requirement document, with optional UI if available

**中文翻译：**
- 为新的 CFD 功能或版本规划手动 QA
- 为关键交易流程（订单生命周期、价格、P&L、保证金、风控）构建或优化测试用例
- 在时间紧张的情况下执行回归测试
- 在版本发布前准备 QA 通过或拒绝的签字

## Inputs To Request
## 需要请求的输入
- Requirement document content or readable extract
- Optional UI design content or readable extract
- Release scope and changed components
- Requirements, acceptance criteria, and known risks
- Environments, build details, and test data availability
- Timeline and execution capacity
- Severity definitions and release gate criteria

**中文翻译：**
- 发布范围和变更的组件
- 需求、验收标准和已知风险
- 环境、构建细节和测试数据的可用性
- 时间表和执行能力
- 严重性定义和发布门槛标准

## Mandatory Inputs Contract
## 强制输入契约
- Required:
   - Requirement document content or readable extract
   - Release scope, impacted modules, and in-scope/out-of-scope boundaries when available
   - Acceptance criteria per requirement when available
   - Build version, environment, and data readiness when available
   - Defect severity policy for sign-off when available
- Optional:
   - UI design content or readable extract
   - Historical incidents and escaped defects
   - Customer usage hotspots
   - Previous regression duration baseline
   - Current app profile or prior iteration notes when this skill is being refined
- Fallback behavior:
   - If the requirement document is missing, ask for it before generating final test cases.
   - If UI is missing, continue with the requirement document alone.

## Team Deployment And Iteration
## 團隊部署與迭代
- Best shared location for team use: `.github/skills/cfd-manual-qa-regression/` inside the team repo.
- Reason: this location is versioned in Git, works across Hong Kong, Shenzhen, and Taiwan team members, and keeps the skill aligned for everyone after each pull.
- Do not use a personal user-level skill path for team sharing unless the intent is a private experiment.
- Keep a companion knowledge file next to the skill, for example `APP_PROFILE.md`, and update it after each iteration.
- Treat the companion file as the living memory for the app. The skill should read it before generating test cases whenever it exists.

## Iteration Contract
## 迭代契約
When the user supplies a requirement document, do all of the following:
1. Distill the app behavior, user roles, screens, workflows, validations, and boundary rules from the document.
2. Update the current app profile with new facts, new terminology, and newly confirmed risk areas.
3. Produce test cases that reflect both the requirement document and any provided UI.
4. Emit a Skill Delta section that can be merged into the next revision of this skill.

The Skill Delta must include:
- Newly learned app behavior
- Rules or edge cases that should be added to the app profile
- Coverage gaps discovered during generation
- Questions to ask on the next iteration
- Any assumptions that were required
- Any wording that should be promoted into the skill itself

## App Profile Inputs
## App 資訊輸入
Before generating test cases, collect and reuse these app facts when available:
- Product purpose and target users
- Main modules and screen names
- Roles and permissions
- Key business rules and calculation rules
- Critical validations and error states
- Known production issues and escaped defects
- Environment-specific behavior and data constraints
- Glossary and business terminology

## Iteration Sequence
Use this order every time:
1. Read the new requirement source.
2. Read the current app profile when available.
3. Merge new facts into the app profile.
4. Generate or update the test cases.
5. Write back the Skill Delta for the next run.

## Skill Delta Content
The Skill Delta must capture:
- Confirmed app behavior learned this round
- Default states and visibility rules learned this round
- Negative and boundary conditions learned this round
- Gaps that still need confirmation
- Exact wording or labels that should be reused later
- Notes for the next iteration so the skill becomes more accurate

**中文翻译：**
- **必需：**
   - 发布范围、受影响的模块、范围内和范围外的边界
   - 每个需求的验收标准
   - 构建版本、环境和数据就绪状态
   - 签字的缺陷严重性政策
- **可选：**
   - 历史事件和逃逸的缺陷
   - 客户使用热点
   - 之前的回归测试持续时间基线
- **回退行为：**
   - 如果任何必需输入缺失，在生成最终测试用例之前提出有针对性的澄清问题。

## CFD Risk Taxonomy
## CFD 风险分类体系
Always map scope to these risk buckets before case design:
- Order lifecycle: place, modify, cancel, partial fill, reject
- Pricing and market data: quote delay, stale feed, spread anomalies
- Margin and leverage: margin check, margin call, stop-out
- P&L and financing: unrealized/realized P&L, rollover/swap
- Risk controls and permissions: account limits, trading session permissions
- Session and market boundaries: open/close, holidays, maintenance windows
- Reliability: timeout, retry, dependency failure, stale cache

**中文翻译：**
在设计用例前，始终将范围映射到这些风险桶中：
- 订单生命周期：下单、修改、取消、部分成交、拒绝
- 价格和市场数据：报价延迟、陈旧数据源、点差异常
- 保证金和杠杆：保证金检查、追证、强平
- P&L 和融资：未实现/已实现 P&L、展期/掉期
- 风控和权限：账户限额、交易时段权限
- 会话和市场边界：开盘/闭盘、假期、维护窗口
- 可靠性：超时、重试、依赖失败、缓存过期

## Procedure
## 执行步骤
1. Define test mission and release risk profile.
2. Break scope into testable units and map each unit to expected behavior.
3. Build a coverage matrix:
   - Requirement coverage
   - Risk coverage
   - User-journey coverage
   - Data/boundary coverage
4. Design positive tests for each primary workflow and acceptance path.
5. Design negative tests for validation, boundary, error handling, permissions, stale data, and dependency failures.
6. Prioritize all tests with a numeric score:
   - Score = Business Impact x Failure Likelihood x Change Size x Customer Exposure
   - Use 1-5 for each factor.
   - Tier thresholds:
     - Tier 1: score >= 80
     - Tier 2: score 40-79
     - Tier 3: score < 40
   - Apply expert override only with written rationale.
7. Execute full manual regression for each release and optimize effort within the run:
   - Always run a canonical core pack for critical CFD flows
   - Run full-depth checks for high-change/high-risk modules
   - Deduplicate overlapping checks
   - Convert repeated low-value checks into spot checks only for low-risk areas
8. Execute in tier order and log concise evidence for each result.
9. Triage defects quickly with reproducible steps, observed behavior, expected behavior, impact, and probable affected scope.
10. Run focused retests for fixes, then run impact-based regression around touched areas.
11. Prepare sign-off summary:
   - Coverage achieved vs planned
   - Open defects by severity and business impact
   - Known limitations and residual risks
   - Final recommendation: go, conditional go, or no-go

**中文翻译：**
1. 定义测试使命和发布风险等级。
2. 将范围分解为可测试的单元，并将每个单元映射到预期行为。
3. 构建覆盖矩阵：
   - 需求覆盖
   - 风险覆盖
   - 用户旅程覆盖
   - 数据/边界覆盖
4. 为每个主要工作流和验收路径设计正向测试。
5. 为验证、边界、错误处理、权限、陈旧数据和依赖失败设计负向测试。
6. 使用数值分数优先级处理所有测试：
   - 分数 = 业务影响 × 失败概率 × 变更规模 × 客户暴露度
   - 每个因素使用 1-5 的数值。
   - 分层阈值：
     - Tier 1: 分数 >= 80
     - Tier 2: 分数 40-79
     - Tier 3: 分数 < 40
   - 仅在有书面理由的情况下应用专家覆盖。
7. 为每个版本执行完整的手动回归，并在运行中优化工作量：
   - 始终为关键 CFD 流程运行标准核心包
   - 对高变更/高风险模块进行完整深度检查
   - 消除重叠检查的重复
   - 将重复的低价值检查转换为仅针对低风险区域的抽样检查
8. 按分层顺序执行，并为每个结果记录简洁的证据。
9. 快速对缺陷进行分类，包含可重现步骤、观察到的行为、预期行为、影响和可能的受影响范围。
10. 对修复运行集中重测，然后对触及的区域运行基于影响的回归。
11. 准备签字总结：
   - 达成的覆盖 vs 计划的覆盖
   - 按严重性和业务影响分类的开放缺陷
   - 已知限制和残留风险
   - 最终建议：通过、条件通过或不通过

## Test Case Design Heuristics
## 测试用例设计启发式
- Positive cases:
   - Golden path for each key user journey
   - High-frequency usage path per module
   - Session transition behavior (market open/close)
   - **UI display/format verification for every display rule** (label text, format, position, color)
   - **Static exhibition checks must have independent assertions**, not just be implicitly covered by interaction tests
- Negative cases:
   - Invalid input and boundary values
   - Stale/late quote handling
   - Insufficient margin and stop-out edge conditions
   - Permission denial and role restrictions
   - Upstream dependency timeout/failure behavior

## Test Case Output Format Standard
## 测试用例输出格式标准

### Google Sheets Output Format
When the user asks for test cases, always provide a Google Sheets-ready table using these columns in this exact order:

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|

Generation rules for this table:
- Subjective should be a clear test objective sentence.
- Steps must be numbered and concise in one cell.
- Verify must state observable expected behavior and key business check.
- Result should default to Not Run when generating pre-execution cases.
- Priority mapping: P1 for Tier 1, P2 for Tier 2, P3 for Tier 3.

## Requirement-to-Case Completeness Rule (MANDATORY)
## 需求到用例完整性规则（强制）
After generating test cases, perform a mandatory line-by-line requirement audit:
1. Extract every numbered rule/sub-point from the requirement document.
2. For each rule, verify at least one test case explicitly asserts that rule's expected behavior in its "Verify" / "预期结果" column.
3. "Implicitly covered" is NOT acceptable — if a rule describes a display format, label content, position, or static state, it MUST have a dedicated test case with an explicit assertion.
4. Flag any requirement rule that lacks a direct test case and generate supplementary cases immediately.

Common miss patterns to guard against:
- **Display/format rules**: label text format, color, position (left/right), numeric precision
- **Default state rules**: initial toggle states, default selections, first-load behavior
- **Transition aftermath rules**: what disappears, what appears, what updates after a state change
- **Negative exhibition rules**: "when X is off/empty, Y should NOT display"

## Output Format
Use this structure in responses:
1. Scope and assumptions
2. Risk-ranked test plan with numeric scoring
3. Google Sheets-ready test case table
4. Iterative skill update for the next round

The user-facing output must stay focused on only the test cases and the skill update. Internal app-profile learning can be retained as working memory, but it should not introduce extra user workflow steps.

**中文翻译：**
生成测试用例后，执行强制性的需求逐条审计：
1. 从需求文档中提取每一条编号规则/子点。
2. 对每条规则，验证至少有一条测试用例在其"预期结果"列中显式断言了该规则的预期行为。
3. "隐含覆盖"不可接受——如果规则描述了展示格式、标签内容、位置或静态状态，必须有专用测试用例并包含显式断言。
4. 标记任何缺少直接测试用例的需求规则，并立即生成补充用例。

需防范的常见遗漏模式：
- **展示/格式规则**：标签文案格式、颜色、位置（左/右）、数值精度
- **默认状态规则**：初始开关状态、默认选项、首次加载行为
- **状态转换后果规则**：什么消失、什么出现、什么在状态变更后更新
- **反向展示规则**："当X关闭/为空时，Y不应显示"

**中文翻译：**
- **正向用例：**
   - 每个关键用户旅程的黄金路径
   - 每个模块的高频使用路径
   - 会话转换行为（市场开盘/闭盘）
   - **每条展示规则必须有独立的UI展示/格式验证用例**（标签文案、格式、位置、颜色）
   - **静态展示检查必须有独立断言**，不能仅靠交互测试隐含覆盖
- **负向用例：**
   - 无效输入和边界值
   - 陈旧/延迟报价处理
   - 保证金不足和强平边缘条件
   - 权限拒绝和角色限制
   - 上游依赖超时/失败行为

## Severity-To-Impact Matrix
- Blocker: trading unavailable or data corruption risk; always no-go
- Critical: wrong execution or severe financial risk; always no-go
- Major: core behavior degraded with workaround; conditional go only with approval
- Minor/Trivial: low business impact; can go with documented backlog

**中文翻译（严重性到影响矩阵）：**
- **阻碍（Blocker）**：交易不可用或数据损坏风险；总是不通过
- **严重（Critical）**：执行错误或严重财务风险；总是不通过
- **主要（Major）**：核心行为降级但有解决方案；仅在审批后条件通过
- **次要/微小（Minor/Trivial）**：业务影响低；可以通过并记录待办项

## Sign-Off Gate Checklist
- Gate A: 100% Tier 1 executed and passed, or approved waiver per case
- Gate B: No open Blocker/Critical defects
- Gate C: Open Major defects have workaround, owner, and target fix date
- Gate D: Residual risk explicitly accepted by stakeholders

**中文翻译（签字门槛检查清单）：**
- **门槛 A**：100% 的 Tier 1 已执行且通过，或每个用例有批准的豁免
- **门槛 B**：没有开放的阻碍/严重缺陷
- **门槛 C**：开放的主要缺陷有解决方案、负责人和目标修复日期
- **门槛 D**：残留风险已被利益相关者显式接受

## Decision Points
- If requirements are ambiguous, pause full execution and create clarification questions before continuing.
- If time is constrained, protect Tier 1 coverage first and explicitly document deferred Tier 2/Tier 3 areas.
- If a blocker defect appears in a critical path, switch to containment: verify blast radius and pause sign-off recommendation until disposition.
- If environment/test data is unstable, run a smoke confidence subset first before deep execution.
- If open defects include Blocker or Critical severity, recommendation must be no-go until closure or accepted business waiver.
- If open defects are Major only, use conditional go with explicit impact statement and stakeholder approval.

**中文翻译（决策点）：**
- 如果需求不明确，暂停完整执行并在继续前创建澄清问题。
- 如果时间受限，首先保护 Tier 1 覆盖并显式记录延迟的 Tier 2/Tier 3 区域。
- 如果在关键路径中出现阻碍缺陷，切换到遏制：验证影响范围并暂停签字建议直到解决。
- 如果环境/测试数据不稳定，在深度执行前先运行烟雾信心子集。
- 如果开放缺陷包含阻碍或严重严重性，建议必须是不通过直到关闭或获得可接受的业务豁免。
- 如果开放缺陷仅是主要缺陷，使用条件通过并提供显式影响说明和利益相关者批准。

## Quality And Completion Checks
- Every in-scope requirement is mapped to at least one test case.
- High-risk areas include both positive and negative coverage.
- Regression execution covers the full planned manual suite for the release.
- Negative test ratio target: at least 30% of total designed cases.
- Boundary/data variation coverage is explicitly listed.
- Deferred coverage is explicitly listed with risk impact.
- Sign-off recommendation is evidence-based and traceable to executed tests and open defect status.

**中文翻译（质量和完成检查）：**
- 每个范围内需求至少映射到一个测试用例。
- 高风险区域包括正向和负向覆盖。
- 回归执行覆盖版本的完整计划手动套件。
- 负向测试比率目标：至少占设计用例总数的 30%。
- 边界/数据变化覆盖明确列出。
- 延迟覆盖明确列出及其风险影响。
- 签字建议基于证据且可追踪到已执行的测试和开放缺陷状态。

## Test Case Output Format Standard
## 测试用例输出格式标准

### Excel 输出格式（最终交付物）
Excel 列定义（按此精确顺序）：

| 模块 | 標題 | Precondition | 步驟 | 驗證 | 備註 |
|------|------|-------------|------|------|------|

各列规则：
- **模块**：对应需求模块名（如"拖动止盈/止损"、"拖动挂单"、"一键开仓"）。去除字母前缀和点（如"A."），去除括号内的方法说明。相同模块的用例排列在一起。
- **標題**：简短场景描述，格式为"场景-操作"（如"持仓买单-设置止盈"、"新建挂单-完整流程"、"一键开仓-余额不足"）。不使用用例ID作为标题。
- **Precondition**：测试前置条件。
- **步驟**：编号步骤，每步独占一行（Excel单元格内换行）。编号格式为"1、步骤A\n2、步骤B\n3、步骤C"。单步操作无需编号。
- **驗證**：预期结果/验证点。
- **備註**：备注信息（默认为空）。

### Excel 结构
- **Sheet1: 需求功能点拆解**（模块 | 子功能 | 关键业务规则）
- **Sheet2: 测试用例**（正常+异常合并在同一张 sheet，按模块分组排列）
- 不包含设计方法覆盖矩阵 sheet

### Markdown 文档格式（工作底稿）
Markdown 用例表列：

| ID | 设计方法 | 前置条件 | 步骤 | 预期结果 | 优先级 |
|---|---|---|---|---|---|

- 步骤多步时使用 `<br>` 换行：`1、步骤A<br>2、步骤B<br>3、步骤C`
- 编号使用中文顿号"、"
- 用例按 ### 子模块标题分组

### 用例编号规则
- 正常用例：`TC-N-01` 起始递增
- 异常用例：`TC-E-01` 起始递增

### 模块排序
Excel 中模块按此顺序排列：
1. 核心交互功能（如拖动止盈/止损、拖动挂单）
2. 组合场景（如挂单与持仓共存）
3. 配置类（如设置）
4. 展示状态
5. 异常状态
6. 扩展功能（如一键开仓）
7. 非功能性（如埋点）

### 示例

**Excel 输出：**
| 模块 | 標題 | Precondition | 步驟 | 驗證 | 備註 |
|------|------|-------------|------|------|------|
| 拖动止盈/止损 | 持仓买单-设置止盈 | 买单持仓1笔；"当前持仓"开关开启 | 1、点击持仓线\n2、虚变实\n3、向上拖动止盈按钮至有效价位\n4、松开\n5、确认 | 止盈设置成功；图上显示止盈线 | |

## Continuous Improvement
- After each release, compare escaped defects against executed coverage.
- Promote missed-risk scenarios into Tier 1 canonical regression pack.
- Update scoring weights if production incidents show different risk reality.

**中文翻译（持续改进）：**
- 每次发布后，将逃逸的缺陷与已执行的覆盖进行比较。
- 将遗漏的风险场景晋升到 Tier 1 标准回归包。
- 如果生产事件显示不同的风险现实，更新评分权重。

## Output Format
Use this structure in responses:
1. Scope and assumptions
2. Risk-ranked test plan with numeric scoring
3. Positive test cases
4. Negative test cases
5. Regression run set (Tier 1/2/3) and optimization notes
6. Coverage matrix summary and threshold status
7. Google Sheets test case table (Module/Subjective/Steps/Verify/Result/Priority)
8. Defect and retest focus
9. Sign-off recommendation and residual risk
10. Skill Delta for next iteration

**中文翻译（输出格式）：**
在响应中使用此结构：
1. 范围和假设
2. 按风险排序的测试计划及数值评分
3. 正向测试用例
4. 负向测试用例
5. 回归运行集（Tier 1/2/3）和优化备注
6. 覆盖矩阵摘要和阈值状态
7. Google Sheets 测试用例表（模块/测试目标/步骤/验证/结果/优先级）
8. 缺陷和重测重点
9. 签字建议和残留风险
