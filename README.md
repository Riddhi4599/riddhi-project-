# EcoPulse — Carbon Footprint Awareness Platform

A single-page web application that helps individuals understand, calculate, and reduce their personal carbon footprint.

## Chosen Vertical

**Carbon Footprint Awareness & Calculator** — an educational tool that helps individuals understand where their everyday carbon emissions come from and estimate their own weekly and annual footprint.

## Approach & Logic

EcoPulse combines awareness content with an interactive calculator and live dashboard. The goal is to make carbon emissions tangible and actionable for everyday users.

The page is structured into four sections:
1. **Hero** — introduces the concept and directs users to the calculator
2. **Calculator** — collects inputs across transport, energy, food, and goods
3. **Dashboard** — shows Eco Score, monthly CO₂, annual forecast, climate impact, breakdown donut chart, and comparison bars
4. **Education Hub** — three awareness articles on climate change, renewable energy, and recycling

## How the Solution Works

- Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build step, no external dependencies beyond Google Fonts
- The calculator listens for `input` events on all sliders and dropdowns and updates the dashboard live
- Emissions are calculated as follows:
  - **Transport** = (car km × fuel factor) + (transit km × 0.04) + (annual flights ÷ 52)
  - **Home energy** = (monthly electricity × 0.7 ÷ 4.33 + cooking baseline) ÷ household size
  - **Food** = diet baseline × diet factor × waste factor
  - **Goods** = (items × 12 kg avg) ÷ 4.33
- Weekly total × 4.33 = monthly CO₂; weekly × 52 ÷ 1000 = annual tons
- **Eco Score** = 124 − (0.149 × monthly), clamped 0–100, displayed as a CSS conic-gradient donut
- Grade (A+ to D) and impact level (Low / Moderate / High) are derived from the score
- Breakdown donut uses CSS `conic-gradient` with four category segments
- Comparison bars show the user vs a 150 kg/month target and 300 kg/month average

## Assumptions Made

- Emission factors are illustrative averages, not region-specific:
  - Petrol car: 0.192 kg CO₂e/km
  - Diesel: 0.171 kg CO₂e/km
  - Electric car: 0.053 kg CO₂e/km
  - Public transport/rail: 0.04 kg CO₂e/km
  - Grid electricity: 0.7 kg CO₂e/kWh
  - Short-haul flight: ~250 kg CO₂e, long-haul: ~900 kg CO₂e (spread across 52 weeks)
- Reference monthly average used for comparison: 300 kg CO₂e
- Recommended target: 150 kg CO₂e/month
- Household energy is divided equally per person (simplification)
- All calculations run client-side — no data is collected or stored

## Tech Stack

- HTML5, CSS3, Vanilla JavaScript (ES6)
- Google Fonts (Poppins, Inter)
- No external libraries or frameworks

## Accessibility

- Semantic HTML structure
- Visible focus states on all interactive elements
- Fully responsive down to mobile widths
- Respects `prefers-reduced-motion`-