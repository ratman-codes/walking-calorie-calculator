https://ratman-codes.github.io/walking-calorie-calculator/

# Walking calorie ledger

A single-file walking calorie calculator that reports **net** calories — the number you can actually add to your TDEE for food tracking — instead of the gross figure most calculators give you.

**Why:** if you walk on an under-desk treadmill during hours already covered by your sedentary TDEE, gross calculators double-count the resting calories you'd have burned anyway. This tool subtracts that resting baseline so the result is safe to add on top of your TDEE.

## How it works

- **Gross burn** uses the ShapeSense cubic equations (derived from Margaria et al., *Energy Cost of Running*) with per-integer-grade coefficients for −5% to +5% grade and linear interpolation between grades, and the ACSM walking equation for +6% to +15%, blended across the 5–6% boundary. Gross output intentionally matches [Omni's walking calorie calculator](https://www.omnicalculator.com/sports/walking-calorie).
- **Net = (gross − resting baseline) × hands discount.** The baseline comes from an optional TDEE field (TDEE ÷ 24 per hour) or falls back to 1 MET (1.05 kcal/kg/hr).
- **Hands-on-desk discount:** Free swing (0%), Typing at desk (−8%), Leaning on desk (−20%, from handrail-support studies). The discount applies only to the activity portion (gross − baseline), never to the resting baseline — supporting your weight reduces the work of walking but can't reduce resting metabolism.
- **Distance / time / speed are linked:** enter any two and the third derives automatically (marked with an "auto" chip). **Steps** work as a fourth entry point: typing steps sets distance via a sex-based stride estimate (male ≈ 2,112 steps/mile from a 2.5 ft stride, female ≈ 2,400 from 2.2 ft); otherwise steps auto-derive from distance. Sex affects only this conversion — the calorie equations are sex-independent.
- Also: imperial/metric toggle, dark mode by default (light optional), slope as a dropdown (−5% to +15%), speed-validity warning outside 0.62–4.66 mph (1–7.5 km/h), a ledger bar visualizing already-counted vs. new calories, a maintenance line (TDEE + net) when TDEE is provided, and a same-scale "two versions of the same day" comparison when TDEE is entered.

## Running it

No build, no dependencies (Google Fonts only). Open `index.html` in a browser, or serve it as a GitHub Pages site.
