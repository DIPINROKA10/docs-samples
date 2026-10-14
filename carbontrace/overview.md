# CarbonTrace — overview

## What it is

CarbonTrace (internal name "EcoWise AI") is a **carbon-footprint tracker** that turns everyday
activities into an estimated CO2e number and visualises the result on a dashboard.

It was built under the **1M1B AI for Sustainability** internship and presented as the
**CarbonTrace** entry at the **GreenHack Sustainability Hackathon 2026**.

## Why an awareness tool

The product is an *awareness* instrument, not an accounting-grade one. Its audience is people
who don't currently know what a "kg CO2e" means. Three rules follow from that:

1. One number on screen at a time — the headline, not the audit trail.
2. Plain-language labels ("car trip, 10 km") instead of factor codes.
3. Colours that read as "ok / mild / high" without needing a legend.

## What it does

- **Input:** the user logs activities (travel, food, energy use) with a value and unit.
- **Estimate:** each activity is multiplied by a published emission factor.
- **Dashboard:** Chart.js renders the breakdown by category and a running weekly total.
- **Feedback:** colour-coded bands (green / amber / red) against a daily target.

## Out of scope (deliberately)

- Audited corporate reporting.
- Lifecycle analysis of products.
- Per-user accounts or history persistence (state is in-browser today).

## Audience

- Students and individuals.
- Sustainability-event organisers running demo booths.
- Evaluators at GreenHack 2026.
