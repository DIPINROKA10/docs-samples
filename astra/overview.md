# ASTRA — overview

## What it is

ASTRA is a browser-based crime-intelligence dashboard built for the **Karnataka State Police (KSP)
Datathon**. It turns raw KSP crime records into three things a non-technical reader (a duty
officer, an analyst, a journalist) can act on directly in a browser:

1. **What** happened — incident counts, categories, and time trends.
2. **Where** it happened — region/hotspot view.
3. **Patterns** — filters that slice incidents by type, location, and period.

The submission was a **working prototype**, not a slide deck: the judges could open a URL and
click through it.

## The problem it addresses

During the datathon the team was given a CSV of KSP incident records. Reading 40,000 rows of CSV
in a spreadsheet is not feasible in a duty-room context. ASTRA's job is to make that data
*readable in under 30 seconds*: land on the page, see the headline counts, narrow down by
district and crime type, and export the filtered view.

## Design decisions (and why)

- **No server required.** The dataset ships as a cleaned JSON file next to the static assets.
  This removes deployment risk during a datathon and lets anyone review it offline.
- **Plain HTML/CSS/Tailwind instead of a heavy framework.** Faster to debug at 3 AM, and the
  JS stays small enough to read in a single sitting.
- **Google sign-in is optional.** The dashboard renders for anonymous visitors; sign-in only
  gates the (optional) saved-filter feature.

## Audience

- KSP analysts and supervisors during the datathon.
- Hackathon/damage judges reviewing live demos.
- (Self) a portfolio piece that answers "can you read data and explain it simply?".

## Out of scope

- Real-time ingestion from KSP systems — this is a snapshot demo.
- User accounts beyond Google sign-in.
- Mobile-optimised layout — desktop-first for the demo.
