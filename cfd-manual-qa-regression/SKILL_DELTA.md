# CFD Manual QA Skill Delta

## Purpose
- Capture the new information learned in the current iteration.
- Record what should be merged into the next skill revision.
- Record gaps and follow-up questions for the next run.

## Iteration Summary
- Date: 2026-08-04
- Requirement source: 一通金业 180版本需求（K线一期）
- UI source: 交易包_安卓_一通智投 (1) 及本轮附件截图
- Scope: K线一期交互、交易、设置、教学、指标、埋点相关功能

## Newly Learned Behavior
- K线页不只是展示图表，而是承接持仓查看、挂单查看、改价、止盈止损设置、一键开仓和教学。
- 拖动止盈止损与拖动挂单都是图表内直接操作，且不能阻断实时行情刷新。
- 多笔持仓和多笔挂单都只默认展示最新一笔，但底部列表允许切换单笔目标进行可视与编辑。
- 一键开仓默认开启，且 KYC 成功后默认进入 K 线页并引导交易教学。
- 埋点是本轮明确需求的一部分，不是可选覆盖项。

## Default States and Visibility Rules
- 当前挂单、当前持仓、现价线默认开启。
- 无持仓时，持仓线、止盈线、止损线均不显示。
- 无有效挂单时，不显示任何挂单线。
- 多笔持仓/挂单时默认只展示最新一笔。
- 订单平仓、挂单成交、挂单撤销或过期后，对应线条立即消失或切换。

## Negative and Boundary Conditions
- 止盈止损价格不得超出系统范围。
- 买卖方向对应的止盈/止损区域必须按 Bid/Ask 方向规则校验。
- 产品休市不可新建挂单，也不可修改或设置止盈止损。
- 删除止盈止损失败时线条恢复实线并提示原因。
- 修改请求超过 5 秒提示“网络超时，请重试”；网络中断提示“网络异常”。
- 可用资金不足不影响挂单，仅影响开仓。

## Coverage Gaps
- 拖动改价章节存在空白编号，需补齐更细的交互约束。
- 指标参数具体范围和说明文案需从最终指标文档再确认。
- 暗黑/亮色主题下所有设置与弹窗的状态一致性仍需补图验证。

## Questions for Next Iteration
- K线改单默认开关是否必须默认开启？
- 止盈止损线默认开关是否与当前持仓一同默认开启？
- 挂单撤销二次确认开关的后台配置名称与默认值是什么？
- 埋点统计报表字段是否已有 MIS 落地定义？

## Assumptions Used
- 未补充说明的 UI 交互以附件截图当前展示状态为准。
- K线表、设置、样式设置存在明暗两套主题，但功能一致。
- 本轮测试用例以安卓端为主。

## Wording to Promote
- 对所有“默认开启/关闭”规则，必须生成独立展示类测试用例。
- 对所有“线条消失/切换/恢复”规则，必须生成状态转换后的结果验证。
- 对所有“拖动+确认弹窗”规则，必须生成拖动前、拖动后、确认后、失败后四段验证。

## Merge Notes
- Keep fixed workflow rules in the skill.
- Keep app-specific facts in app profile.
- Keep this file for round-specific additions only.