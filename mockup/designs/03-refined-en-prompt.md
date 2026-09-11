# Selected design refinement prompt

Generated with the built-in Image Gen tool on 2026-09-10. The actual input image was [03.png](03.png); the output is [03-refined-en.png](03-refined-en.png).

```text
Use case: ui-mockup, style-transfer and text-localization edit.
Asset type: a refined Liqora desktop LP position detail UI.
Edit target: the attached image is the user's SELECTED THIRD design. Preserve its recognizable asymmetric layout: narrow left position/performance rail, wide right fee statement, assets/range and recent activity. Refine that one selected direction, do not invent a different concept.
Primary request: the user likes this third layout but rejects the saturated green/mint palette. Phase one must be ENGLISH ONLY. Create a premium, restrained, low-saturation financial product UI. Do not print art-direction notes, option labels or hex codes on the screen.

Target dimensions: 1440 x 1024 desktop landscape, natural proportions closely matching the attached source. Render a complete focused viewport, no browser frame, no clipping, no distortion.
Current date anchor: September 10, 2026. The sample data below is deliberately fictional. Keep a clear small 'Demo data' label and sample transaction labels.

Art direction: porcelain/off-white #FAFAF8 main surface, very subtle light mineral gray #F1F1EE left rail, graphite #24272B primary typography, readable neutral gray #64696E secondary copy, hairlines #DDDFDC, charcoal #303438 for the one primary button. Small desaturated sage #52685B positive states and dusty muted red #8A605D negative states only. No green-tinted canvas, no lime, teal, emerald, gold, blue-purple gradient, glow, glassmorphism, or glossy decoration. At least 90 percent of the screen should read neutral. Preserve accessible contrast; low saturation must not mean faint text. Brand wordmark and simple existing source logo become graphite monochrome. Token marks likewise neutral.

Premium feel through exact alignment, strong restrained typography, generous purposeful spacing and disciplined hairlines. Use one Inter-like modern sans-serif type family with tabular numerals. Body 14-16 px equivalent. Key P&L 48 px, supporting values 26-30 px, clear 18 px section labels. No giant marketing headings, serif display type, illustrations, decorative charts, heavy shadows, pill overload or rounded cards inside cards. Use the page surface and horizontal rules. Primary button slightly rounded, not pill. Left rail width about 345-365 px, subtle right border. Right column about 980 px, 40-48 px padding. Keep the existing density legible, do not add features.

ALL VISIBLE COPY MUST BE ENGLISH. Preserve the exact business content but translate and tighten it according to these authoritative labels and sample values:
Header: 'liqora.' logo; single nav 'Current positions'; right 'Robinhood Chain'; wallet '0x71C7...4F2a' and 'Verified'. It is a verified-wallet view showing base LP P&L. No additional navigation, no wallet asset balance.
Under header right: 'As of Sep 10, 2026, 10:00 UTC+8 · Demo data'. Fixed 'USD basis' or 'All values in USD' must be visible.
Left rail:
'Back to positions'
'SPY / USDG'
'Uniswap V4 · No hook · NFT #204801'
'Opened Aug 31, 2026 · 14:20 UTC+8'
'In range' with small subdued status dot
small 'LP P&L', large '+295.00' and small 'USD'
'P&L / total deposits' '+2.95%' with small 'Not annualized'
rule
'Position value' '10,200.00 USD', helper 'Excludes uncollected fees'
'Initial deposit' '10,000.00 USD'
rule
'Fee APR · 24h' '36.50%'
window selector '1h' '24h' '7d' '30d', 24h selected in grayscale, 30d muted
two compact metrics 'Fees earned · 24h' '10.00 USD' and 'Daily average · 24h' '10.00 USD'
'Average capital · 24h' '10,000.00 USD'.

Right main:
Section 'Fees & costs', a quiet caption 'Current LP cycle · USD'.
Neutral surface top summary, not mint: 'Total fees' '100.00' and small secondary copy 'Collected + reinvested at historical value; uncollected at current value.' Avoid the wrong claim that all are current value or all are estimated earned value.
Fee table aligned label / USD value / explanation:
'Collected' '60.00' '0.12 SPY · valued at collection'
'Uncollected' '40.00' '0.04 SPY + 20.202020 USDG · current value'
'Reinvested directly' '0.00' 'Included in position capital'
Hairline row 'LP gas' '5.00' 'Already deducted from P&L'
Hairline row 'Preparation costs' '—' 'None linked' with charcoal primary 'Link preparation costs'.
Add a small 'Fees are already included in P&L.' note if space permits; never add total fees again to P&L.

Section 'Assets & range', no superfluous module:
table headers 'Token' 'Amount' 'Value (USD)' 'Weight'
SPY 10.00000000 5,000.00 49.0%
USDG 5,252.525253 5,200.00 51.0%
Compact range strip label 'Price range · USDG / SPY', endpoints 480.00 and 530.00, current tick 505.05, subtle desaturated bar and graphite marker, explicit 'In range'. This is the only chart-like element.

Section 'Recent activity'
headers 'Time (UTC+8)' 'Action' 'Value (USD)' 'LP gas (USD)' 'Transaction'
row 'Sep 9, 2026 · 12:08' 'Collect fees' '+60.00' '2.00' 'Sample · 0x8a3f...7c21'
row 'Aug 31, 2026 · 14:20' 'Create position' '−10,000.00' '3.00' 'Sample · 0x4d92...a9e5'.

Constraints: A read-only current-LP monitor only. No trade, approve, deposit, liquidity editing, charts of historic P&L, HOLD/ETH switches, projected returns, dark/light theme selector, rewards, or additional routes. No Chinese characters anywhere. Keep the chosen source layout; only localize, remove the strong color cast, correct the stated financial copy, and improve visual refinement. Output a single production-quality screen, no surrounding commentary.
```
