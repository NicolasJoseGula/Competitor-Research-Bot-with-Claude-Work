# Competitor Research Bot with Claude Cowork

![image](./images/logo.png)

An automation project built on top of **Claude Cowork** that generates professional, client-ready competitor profiles for companies in the streaming services market. It's designed for media consulting teams that need concise, consistent strategic analysis backed by verifiable sources.

---

## Overview

The bot uses a **custom skill** (`competitor-research-bot`) that instructs Claude to research streaming-sector competitors following a consulting-grade editorial standard. From a structured prompt, Claude will:

1. Research the company using primary sources and reputable business journalism.
2. Structure the information using a fixed template (`templates/competitor-template.md`).
3. Save the final profile as a Markdown file inside `outputs/`.
4. Cite all sources at the bottom of the document.

The result is a homogeneous deliverable across competitors, making side-by-side comparisons and executive presentations much easier.

---

## Project Structure

```
Competitor Research Bot with Claude Cowork/
├── README.md                     # This file
├── images/                       # Visual assets (logos, screenshots, diagrams)
├── outputs/                      # Generated competitor profiles
│   └── netflix-profile.md        # Example: Netflix profile (Q1 2026)
├── skills/
│   └── skill.md                  # competitor-research-bot skill definition
└── templates/
    ├── competitor-template.md    # Standard template for competitor profiles
    └── file-organizer.md         # Auxiliary prompt for folder organization
```

---

## The Skill: `competitor-research-bot`

File: `skills/skill.md`

Defines Claude's expected behavior when researching a competitor. Key points:

**Editorial standard**
- Professional consulting level, ready for client delivery.
- Clear, neutral, analytical language; no hype or unsupported claims.
- Explicit when a data point cannot be verified.

**Preferred sources (highest priority)**
- Investor relations websites, earnings reports, and call transcripts.
- Official press releases and company blogs/newsroom pages.

**Accepted secondary sources**
- Reuters, Bloomberg, WSJ, NYT, Variety, The Hollywood Reporter, Deadline.

**Sources to avoid as primary evidence**
- Forums, social media, Reddit, aggregator sites.

**Formatting**
- Paragraphs for *Overview*, *Content Strategy*, and *Differentiators*.
- Bullets for *Pricing Tiers*, *Strengths*, and *Weaknesses*.
- Always include date and source on financial or subscriber data.

**Comparison task**
- When comparing multiple competitors, a `outputs/streaming-landscape-summary.md` file is produced with *Market Overview*, a comparison table, and analysis.

---

## The Template: `competitor-template.md`

Every profile follows the same structure:

1. Company Overview
2. Subscription Tiers and Pricing
3. Content Strategy
4. Recent News (Last 90 Days)
5. Subscriber Base and Growth
6. Strengths
7. Weaknesses
8. Key Differentiators
9. Sources

Each file is named using the format `[company-name]-profile.md` (lowercase, hyphenated) and includes the current date in the **Prepared** field.

---

## How to Use It

### Prompts

**Weak prompt** (avoid)

```
Research Netflix for me
```

Doesn't specify format, scope, template, output location, or source requirements.

**Strong prompt** (recommended)

```
Research Netflix as a competitor in the streaming services market.
Use the template in templates/competitor-template.md to structure your output.
Focus on: their subscription tiers and current pricing, content strategy
(originals vs. licensed), any news from the last 90 days, subscriber base
and growth trends, and where they are strong and weak relative to other
major streamers. Save the completed profile as a markdown file in the
outputs folder named netflix-profile.md. Cite your sources at the bottom.
```

The strong prompt anchors the deliverable to the template, defines the analytical focus, fixes the file name and location, and requires citations.

### Supported Request Examples

- *Create a competitor profile for Netflix.*
- *Compare Netflix, Disney+, and Max.*
- *Update the latest subscriber figures for Paramount+.*
- *Summarize the competitive positioning of Apple TV+.*

---

## Example Output

`outputs/netflix-profile.md` contains a complete Netflix profile prepared on April 21, 2026, with updated pricing following the March 2026 increase, Q1 2026 earnings results, content strategy (including the WWE deal and licensing agreements with Paramount/Skydance and Sony), the failed Warner Bros. Discovery acquisition bid, and an analysis of strengths, weaknesses, and differentiators, backed by 18+ cited sources.

That file serves as the *gold standard* for future profiles generated with this bot.

---

## Extending the Bot

To add a new competitor, simply use a structured prompt like the one above, replacing the target company. To extend the scope (other sectors, different metrics, alternative output formats), duplicate and adapt the skill in `skills/skill.md`, or add additional templates inside `templates/`.
