# K-Line Phase 1 Test Cases

## Scope and assumptions
- Based on the attached Confluence export summary and the UI screenshots in the folder `交易包_安卓_一通智投`.
- The requirement text is partially summarized, so a few verification points are written as observable UI expectations rather than exact business-rule text.
- This set is intended as a team-ready iteration baseline and should be refined after the app profile is updated from execution feedback.
- Where the requirement specifies direct chart manipulation, the test cases assume the user stays on the chart page and does not navigate away.

## Risk-ranked test plan with numeric scoring

| Risk | Impact | Likelihood | Change Size | Exposure | Score | Tier |
|---|---|---:|---:|---:|---:|---|
| One-click open causes accidental trade | 5 | 4 | 5 | 5 | 500 | P1 |
| Dragging pending order to wrong price | 5 | 4 | 4 | 5 | 400 | P1 |
| Dragging stop-loss/take-profit to wrong level | 5 | 4 | 4 | 5 | 400 | P1 |
| Wrong chart line state shown by default | 4 | 4 | 3 | 4 | 192 | P1 |
| Indicator or drawing settings not persisted | 3 | 3 | 3 | 4 | 108 | P1 |
| First-time guide is incomplete or misleading | 3 | 3 | 3 | 3 | 81 | P1 |
| Loading or empty state for chart options fails | 3 | 2 | 2 | 3 | 36 | P3 |

## Positive test cases

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| K线表 | Switch K-line chart type | 1. Open the K线表 selector; 2. Choose 蜡烛图, 空心阳线, 棒形图, or 线形图 | The chart changes to the selected style and the selected card is highlighted | Not Run | P1 |
| 新手教学 | View the first guide sequence | 1. Open the 新手教学 panel; 2. Step through the four tutorial pages | Each page shows the expected title and instruction for 一键开仓, 拖动挂单, 拖动止盈止损, and 个性设置 | Not Run | P1 |
| 一键开仓 | Enable quick open | 1. Open 设置; 2. Turn on 一键开仓; 3. Return to the chart | The one-click open control is enabled and the page reflects the quick-open state; the quick trade affordance is visible on the chart | Not Run | P1 |
| 行情K线 | Show current price line | 1. Open 设置; 2. Enable 现价线; 3. Return to the chart | The chart displays the current price line with the current price label | Not Run | P1 |
| 行情K线 | Show highest/lowest line | 1. Open 设置; 2. Enable 最高/低线; 3. Return to the chart | The chart displays the day high and low reference lines clearly | Not Run | P1 |
| 订单显示 | Show current pending orders | 1. Open 设置; 2. Enable 当前挂单; 3. Return to the chart | Pending-order lines appear on the chart with the correct line style and tags; when disabled they disappear completely | Not Run | P1 |
| 订单显示 | Show current positions | 1. Open 设置; 2. Enable 当前持仓; 3. Return to the chart | Position lines appear on the chart with the correct labels and profit/loss markers; when disabled they disappear completely | Not Run | P1 |
| 画线 | Add a trend line | 1. Open 设置; 2. Go to 画线; 3. Add a horizontal or diagonal line | The selected line is drawn on the chart and is visible after closing the panel | Not Run | P2 |
| 指标参数 | Adjust indicator parameters | 1. Open 指标参数; 2. Select MA; 3. Change a parameter; 4. Confirm | The chart updates with the new indicator parameters and the selection persists | Not Run | P1 |
| 持仓切换 | Show latest open position by default | 1. Create multiple positions for the same product; 2. Open the chart | Only the latest opened position is shown by default | Not Run | P1 |
| 持仓切换 | Switch selected position from bottom list | 1. Open the bottom position list; 2. Select a different position | The chart updates to the selected position and its open line, and the previously visible line is dismissed | Not Run | P1 |
| 持仓线 | Edit current position line | 1. Tap the current position line; 2. Enter edit state | The line becomes editable and shows stop-loss / take-profit drag buttons | Not Run | P1 |

## Negative test cases

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| 一键开仓 | Do not place an order when disabled | 1. Ensure 一键开仓 is off; 2. Tap buy/sell from the chart | The app does not perform one-click direct execution and uses the normal confirmation flow | Not Run | P1 |
| 拖动挂单 | Reject invalid drag placement | 1. Open the drag-order tutorial or pending-order line; 2. Drag to an invalid/off-chart area | The line does not commit an invalid order, and the UI either snaps back or shows a validation message | Not Run | P1 |
| 拖动止盈止损 | Reject invalid SL/TP placement | 1. Open a position line; 2. Drag stop-loss/take-profit beyond the allowed range | The app blocks the invalid placement and keeps the existing protected state unchanged; the target price must stay inside the allowed buy/sell direction rules | Not Run | P1 |
| 当前挂单 | Do not show pending-order lines when unchecked | 1. Disable 当前挂单 in 设置; 2. Return to the chart | Pending-order lines disappear and no stale pending-order label remains | Not Run | P1 |
| 当前持仓 | Do not show position lines when unchecked | 1. Disable 当前持仓 in 设置; 2. Return to the chart | Position lines disappear and the chart no longer shows position tags or related controls | Not Run | P1 |
| 现价线 | Do not show current price line when unchecked | 1. Disable 现价线 in 设置; 2. Return to the chart | The current price line is hidden and only the remaining enabled chart lines remain visible | Not Run | P1 |
| 最高/低线 | Do not show high/low line when unchecked | 1. Disable 最高/低线 in 设置; 2. Return to the chart | The high/low reference line is hidden and no misleading label remains | Not Run | P1 |
| 新手教学 | Prevent guide from breaking chart interaction | 1. Open the guide; 2. Close it; 3. Interact with chart controls | The chart remains usable and no guide overlay blocks normal controls after dismissal | Not Run | P2 |
| 指标参数 | Cancel parameter changes safely | 1. Open a parameter screen; 2. Change values; 3. Cancel instead of confirm | The original indicator settings remain unchanged | Not Run | P1 |
| 休市狀態 | Block SL/TP editing during market close | 1. Enter a market close state; 2. Try to modify or set stop-loss/take-profit | The app blocks the action and does not allow stop-loss/take-profit editing during close | Not Run | P1 |
| 超時處理 | Show timeout message on request failure | 1. Simulate a timeout; 2. Submit modify or SL/TP action | The app shows the timeout message and keeps the original chart state | Not Run | P1 |
| 斷網處理 | Show network error on disconnection | 1. Simulate network disconnection; 2. Submit modify or SL/TP action | The app shows the network error message and keeps the original chart state | Not Run | P1 |

## Regression run set and optimization notes
- Tier 1 core pack should always cover: 新手教学, 一键开仓, current pending orders, current positions, K线改单, stop-loss/take-profit drag, 现价线, 最高/低线, and MA parameter confirm/cancel.
- Tier 2 should cover: line tools, style settings, screen stay-awake, sound/vibration reminders, and other indicator families.
- Tier 3 should cover secondary chart themes and low-risk display preferences.
- Deduplicate by reusing the same chart setup for multiple checks when the same screen can verify both display and behavior.
- When multiple positions exist, reuse the same chart setup to verify both default latest-position display and bottom-list switching.

## Coverage matrix summary

| Requirement area | Coverage status | Notes |
|---|---|---|
| Chart type selection | Covered | K线表 options verified |
| First-time guide | Covered | Four-step tutorial mapped |
| One-click open | Covered | Enable/disable behavior included |
| Pending-order line display | Covered | Visible and hidden states covered |
| Position line display | Covered | Visible and hidden states covered |
| Current price / high-low lines | Covered | Visible and hidden states covered |
| K-line modify flow | Covered | Drag and confirm behavior included |
| Stop-loss/take-profit flow | Covered | Drag, confirm, and cancel behavior included |
| Indicator parameters | Covered | Confirm and cancel behavior included |
| Drawing tools | Partially covered | Need exact shape list and persistence rule confirmed |
| Style settings | Partially covered | Need persistence and per-device behavior confirmed |
| Multiple-position handling | Covered | Default latest-position display and switching covered |
| Market close / timeout / network failure | Covered | Blocking and error recovery included |

## Google Sheets test case table

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| K线表 | Switch K-line chart type | 1. Open K线表; 2. Select 蜡烛图 | Chart switches to candlestick style | Not Run | P1 |
| 新手教学 | Complete guide step for one-click open | 1. Open 新手教学; 2. Go to step 1 | The step explains 一键开仓: 一点即成交 | Not Run | P1 |
| 新手教学 | Complete guide step for drag order | 1. Open 新手教学; 2. Go to step 2 | The step explains 拖动挂单: 看准价位，拖动即可下单 | Not Run | P1 |
| 新手教学 | Complete guide step for SL/TP drag | 1. Open 新手教学; 2. Go to step 3 | The step explains 拖动止盈止损: 点击K线中当前持仓，拖动即可设置止盈止损 | Not Run | P1 |
| 新手教学 | Complete guide step for settings | 1. Open 新手教学; 2. Go to step 4 | The step explains 个性设置: 选择显示的订单线和K线样式 | Not Run | P1 |
| 设置 | Toggle current pending orders | 1. Open 设置; 2. Enable 当前挂单 | Pending-order line appears on the chart | Not Run | P1 |
| 设置 | Toggle current positions | 1. Open 设置; 2. Enable 当前持仓 | Position line appears on the chart | Not Run | P1 |
| 设置 | Toggle current price line | 1. Open 设置; 2. Enable 现价线 | Current price line appears on the chart | Not Run | P1 |
| 设置 | Toggle high/low line | 1. Open 设置; 2. Enable 最高/低线 | High/low reference lines appear on the chart | Not Run | P1 |
| 设置 | Toggle one-click open | 1. Open 设置; 2. Turn on 一键开仓 | Quick-open mode is enabled | Not Run | P1 |
| 指标参数 | Change MA parameters | 1. Open 指标参数; 2. Edit MA; 3. Confirm | MA values update on the chart | Not Run | P1 |
| 画线 | Add a horizontal line | 1. Open 画线; 2. Choose 水平直线; 3. Draw on chart | The horizontal line is added and visible | Not Run | P2 |
| 画线 | Clear drawing objects | 1. Add a line; 2. Use 清空 | Added drawing objects are removed | Not Run | P2 |
| 样式设置 | Change K-line theme color | 1. Open 样式设置; 2. Select a K线主题色 | The selected theme color is applied | Not Run | P2 |
| 样式设置 | Enable sound reminder | 1. Open 样式设置; 2. Turn on 订单成交声音提醒 | The sound reminder toggle is enabled | Not Run | P2 |
| 持倉/掛單 | Open bottom list for same product | 1. Tap the current holding or pending area; 2. Open the bottom list | The bottom list shows all orders for the same product and the chart remains in sync | Not Run | P1 |

## App profile delta
- Capture the exact first-guide wording from the release source if available.
- Confirm whether one-click open is a global setting or chart-specific.
- Confirm whether current pending/current positions/K-line modify/SL-TP lines are independent toggles or grouped states.
- Add exact drawing-tool persistence rules after save/close/return navigation.
- Add exact indicator families and whether each family exposes custom parameter editing.

## Skill Delta for next iteration
- Newly learned behavior: the feature is a chart-centric trading UX with first-time onboarding, direct chart order manipulation, and configurable display layers.
- Questions to ask next: what exact rules control one-click execution, which chart elements are mandatory by default, and whether settings persist per account or per device.
- Assumption: users can modify orders directly from the chart by dragging lines and confirming in bottom sheets.
- Wording to promote into the skill: always verify chart-line visibility, direct-manipulation rollback, guide-step clarity, and settings persistence for any trading-chart feature.
