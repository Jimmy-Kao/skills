# K-Line Phase 1 App Profile

## Status
Confirmed from attached Confluence export summary and UI screenshots, with a few items still needing exact wording confirmation from the original requirement source.

## Confirmed Facts
- Product/screen context: spot gold trading chart page labeled 现货黄金.
- Main chart tab: 行情K线.
- Other top tabs: 智能分析, 舆情分析, 数据中心, 产品介绍.
- Timeframe controls shown: 分时, 5分, 30分, 1小时, 日K.
- The page shows a K-line chart with MA/MACD style indicators and price axis labels.
- A first-time guide overlay exists under 新手教学.
- A settings sheet exists with tabs for 指标参数, 画线, K线表, 新手指导.
- There is a one-click open feature labeled 一键开仓.
- Chart display supports current pending orders, current positions, K-line order modification, and stop-loss/take-profit lines.
- Chart display supports current price line and highest/lowest line.
- There are indicator settings for main indicators and sub indicators.
- There are drawing tools for trend lines and shapes.
- There are style settings for K-line theme color, rise/fall color, screen always-on, order filled sound, and order filled vibration.
- The chart page supports direct trading actions from the chart without leaving the page for common adjustment flows.
- Market-close rules block stop-loss/take-profit changes and stop-loss/take-profit setup.
- Timeout feedback uses the text 网络超时，请重试.
- Network disconnect feedback uses the text 网络异常.

## Learned UI Behavior
- K-line table popup offers at least 蜡烛图, 空心阳线, 棒形图, 线形图.
- New user guide has 4 steps:
  - 一键开仓: 一点即成交
  - 拖动挂单: 看准价位，拖动即可下单
  - 拖动止盈止损: 点击K线中当前持仓，拖动即可设置止盈止损
  - 个性设置: 进入设置查看新手指导、选择要显示的订单线和K线样式
- Settings default selections shown in the screenshots:
  - 当前挂单 selected
  - K线改单 selected
  - 现价线 selected
- Stop-loss/take-profit modal supports price and point-based entry.
- Modify order modal supports editing price and volume, with confirm/cancel actions.
- Pending-order and position lines show drag handles, labels, and remove/cancel affordances.
- Crosshair displays candle detail values when enabled or when tapping the chart.
- Indicator parameter screen allows adjustment by line item, with confirm and reset behaviors.
- When the current position line is tapped, the line becomes editable and shows stop-loss / take-profit drag buttons.
- The same drag interaction is used for first-time stop-loss / take-profit setup and for modifying an existing setting.
- After releasing a drag, a confirmation popup appears and shows the target price and expected profit/loss.
- Stop-loss / take-profit drag only supports price-based adjustment, not point-based adjustment.
- When an order is filled, the open line and stop-loss / take-profit line disappear immediately.
- When there are multiple positions of the same product, the default display shows only the latest opened position.
- Selecting a position from the bottom list updates the chart to the selected position's open line and related state.
- Pending-order and position switch lists appear from the bottom area and show all orders for the same product.
- The line delete flow must remove the corresponding stop-loss / take-profit data from the order.

## To Confirm
- Exact default state for first-time users on entry.
- Exact text of each guide step and whether it is forced only once or repeatable.
- Whether one-click open is enabled by default or always optional.
- Whether current pending/current position/K-line modify/SL-TP line settings are multi-select or single-select in all cases.
- Exact loading, empty, and error states for indicator, drawing, and order-line data.
- Exact behavior when switching between current price line and highest/lowest line.
- Whether delete actions always require a second confirmation.
- Whether different order types share the same editable UI state when selected from the chart.

## Risk Areas
- Wrong order-line type shown on chart.
- Incorrect drag target causing unintended order modification.
- One-click open causing accidental execution.
- Wrong default chart display causing user misread of market position.
- Missing or misleading guide text for first-time users.
- Indicator or drawing settings not persisted correctly.
- Confusing or missing distinction between current position and pending-order display states.
- Incorrect handling of no-hold / no-order states.
- Failure to remove stop-loss / take-profit data when deleting.
- Blocked user flow when market-close, timeout, or network-error rules are not surfaced correctly.

## Glossary
- 一键开仓: quick one-tap open feature.
- 挂单线: pending-order line displayed on the chart.
- 持仓线: open-position line displayed on the chart.
- K线改单: modify an order directly from the chart by dragging.
- 止盈止损线: take-profit / stop-loss line on chart.
- 当前挂单: current pending-order display state on the chart.
- 当前持仓: current open-position display state on the chart.
