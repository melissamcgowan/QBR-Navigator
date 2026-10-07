# QBR Navigator

An interactive quarterly business review that looks forward as well as back. Most QBR decks summarize the last year and stop. This one ties the year in review to the customer's success plan, so the meeting ends with a dated path to where the customer wants to go.

Built with synthetic data. No customer information is included.

## What it does

| Tab | Question it answers |
|---|---|
| Year in review | What happened this year, and how does the success plan look right now? |
| Success plan goals | Is each goal on pace? Where does the current pace actually land by the due date? |
| Roadmap | What happens in the next 12 months, and who owns each step in the next 90 days? |
| Opportunities | Which unused features and teams would move the goals that are behind pace? |
| What if | If we turn these on or invest more in enablement, how does the plan change? |

## How the projections work

For each goal, the app measures progress since the goal's start date, then extends that pace to the due date.

- Share of target reached is (current minus baseline) divided by (target minus baseline). This works for goals where lower is better, such as resolution time.
- Status: on track at 95% or more of target by the due date, at risk from 80% to 95%, off track below 80%, target reached once the target is met.
- Projected finish is the date the current pace reaches the target.
- What-if levers multiply the pace going forward. Each goal has an enablement sensitivity, and each unused feature carries a lift for the goals it supports. These are planning assumptions, so adjust them to match your own results.
- Customer value realized is each goal's annual value multiplied by the share of target reached by the due date.

## Customer-facing by design

The language is written for an executive sponsor and a champion in the room. The Commit buttons on the roadmap collect agreed actions into a summary that can be sent after the meeting.

## Two-layer design

The data layer is one block at the top of the script, marked `DATA LAYER`. It mirrors a customer success platform export: account profile, 12 months of usage, support summary, success plan goals with milestones, agreed actions, feature whitespace and expansion candidates. The rendering layer reads only from that block, so a live CSP connection can replace the data without touching the interface.

It reuses the goal, milestone, owner and due date structure of the Success Plan Generator, so a plan built there can feed this review.

## Run it

Open `qbr-navigator.html` in a browser. There is nothing to install or build. Fonts load from Google Fonts and fall back to system fonts offline.

## Roadmap ideas

- Read the Success Plan Generator's extracted data directly
- Export the commitments summary as a follow-up email draft
- Feed the account list from the Customer 360 capstone
