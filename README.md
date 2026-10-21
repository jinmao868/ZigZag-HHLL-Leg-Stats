# ZigZag HHLL

A TradingView (Pine Script v6) indicator that draws a ZigZag and labels every swing point by its role in the market structure, highlights swings formed in overbought/oversold conditions, and shows how long each leg typically lasts on the current timeframe.

<!-- Add a chart screenshot here, e.g. ![chart](screenshot.png) -->

## Features

- **ZigZag swings**: a swing is triggered when the current bar makes the highest high / lowest low of the last N bars (default 10). Highs and lows strictly alternate.
- **6 structure labels**:

| Label | Meaning |
|---|---|
| **HH** | Breaks the previous high, the previous high was High/HH, and the low in between was a Higher Low (trend continuation) |
| **High** | Breaks the previous high, but without a clean uptrend structure before it (often the first sign of a shift) |
| **LH** | Fails to exceed the previous high |
| **LL** | Breaks the previous low, the previous low was Low/LL, and the high in between was a Lower High (trend continuation) |
| **Low** | Breaks the previous low, but without a clean downtrend structure before it |
| **HL** | Holds above the previous low |

- **OB/OS highlight**: a label becomes a filled box when, on the swing bar, both RSI(14) and Stoch RSI %D (3, 3, 14, 14) are ≥ 65 (highs) or ≤ 35 (lows).
- **Leg duration table**: max and average bars per up-leg and down-leg within the displayed range, plus the current leg's length (yellow above average, orange above max).
- **Configurable history**: show the last 52 swings by default, up to 499.
- **Alerts**: New High, Higher High, Lower High, New Low, Lower Low, Higher Low (fired on confirmation).

## Installation

1. Open [`zigzag_hhll.pine`](zigzag_hhll.pine) and copy the full code.
2. In TradingView, open **Pine Editor** → **Create new** → **Indicator**, delete the default code.
3. Paste, save, and click **Add to chart**.

## Repainting note

Confirmed swings never change. The **last leg is live**: its end point and label can still move until price reverses enough to confirm it. Enable *Mark live leg as unconfirmed* to show it as a dashed line with a `?`. Alerts fire only on confirmed swings.

## Credits

The labeling scheme and OB/OS highlight concept are inspired by [Higher High Lower Low - Live](https://www.tradingview.com/script/sZrwXphZ-Higher-High-Lower-Low-Live/) by **LonesomeTheBlue**. This is an independent implementation written from scratch; no code from the original (which is closed-source) is used.

## Disclaimer

This indicator is a tool for analyzing market structure, not a buy/sell signal or financial advice. Use it with your own analysis and risk management.

---

## 中文说明

一个 TradingView 指标：用 ZigZag 识别摆动点，并按市场结构标注 HH / High / LH / LL / Low / HL 六种标签；在 RSI 与 Stoch RSI 同时超买/超卖时用醒目方框突出显示；左上角表格统计当前周期下每段上涨/下跌走势持续的最大、平均 K 线数和当前已持续的 K 线数。

**使用方法**：复制 `zigzag_hhll.pine` 的全部代码 → TradingView 打开 Pine Editor → 新建指标 → 删除默认代码后粘贴 → 保存并添加到图表。

**注意**：已确认的摆动点不会改变，最后一段走势在确认前会随价格移动（可在设置中打开虚线和问号标记）。本指标仅用于结构分析，不构成投资建议。
