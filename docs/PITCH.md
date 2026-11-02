# Evolve — one-page pitch

## One line

**The product team you can’t afford:** Evolve listens to your customers, watches your competitors, and improves your product every week.

## The problem

Products are supposed to get better from experience. In practice they improve at the speed of the people running the loop: research, prioritisation, testing, learning. Signals grow much faster than headcount. A fast-growing startup gets thousands of reviews, tickets and usage patterns a week and has one or two product managers to read them. A smaller business has none.

The result is guessing. Teams ship what the loudest customer or the latest competitor launch suggests, rarely test it properly, and almost never write down what they learned.

## The solution

A closed loop that runs every week:

1. **Steer.** An AI CPO turns the business goal into a north star, a metric tree and guardrails. A person approves.
2. **Listen and watch.** Users’ words and behaviour, plus competitor moves, become ranked problems with evidence.
3. **Prioritise.** Each problem becomes a testable bet, ranked by impact × confidence ÷ time to ship.
4. **Test.** Every bet is an A/B test with guardrails watched throughout.
5. **Ship or heal.** Launch or roll back; regressions are diagnosed and fixed, reversible ones automatically.
6. **Remember.** Every result changes the confidence of the next cycle’s bets.

Agents do the work; people approve; autonomy is earned one action type at a time.

## Who it’s for first

Companies that have real users and traffic but no full product, research and data team: scale-up startups with one or two PMs, and digital-native businesses where the founder is the product team. *[Wedge segment to be validated with 8–10 customer interviews.]*

## Why now

- Language models can now read unstructured feedback, reason about a metric tree and write a sound experiment, which used to need a researcher and an analyst.
- Coding agents are making v1 cheap. What stays scarce is knowing what to change next and proving it worked.
- Incumbent analytics tools are adding agents that monitor and recommend. The gap is acting end to end, with judgement and guardrails.

## How it’s different

| | Analytics and experiment tools | Evolve |
|---|---|---|
| Output | Insights and recommendations | Tested, shipped changes |
| Goals | You bring them | AI CPO proposes, you approve |
| Competitors | Out of scope | Watched every cycle |
| Learning | Lives in analysts’ heads | Memory raises or lowers confidence each cycle |
| Regressions | An alert to investigate | Diagnosed and healed within earned autonomy |
| Judged by | Seats and usage | North-star lift |

## Moat

- **Memory per customer:** the longer it runs, the better its bets, and the more it costs to leave.
- **Cross-customer priors (with consent):** what worked for similar products seeds new customers, which also solves small samples.
- **Trust design:** guardrails, decision-ready alerts and earned autonomy are hard to bolt onto a dashboard product.

## How we measure success

- Time from a pain signal to a proven fix (target: weeks down to days).
- Win rate: share of tests that move the north star.
- North-star lift per quarter.
- Zero hard guardrail breaches; soft ones healed within a day.

## Business model (draft)

Subscription priced by workspace and connected data sources, with an outcome-linked tier tied to north-star lift. *[Pricing to be tested.]*

## Risks

| Risk | Mitigation |
|---|---|
| Gaming the metric | Hard guardrails beside every north star |
| Correlation mistaken for cause | Every bet tested against a control |
| Alert fatigue | Only decision-ready alerts; low-risk fixes act then tell |
| Privacy | Aggregated signals; customers control what is sent to AI |
| Platform players build it in | Go deeper on judgement, memory and cross-tool coverage than any single platform will |

## Status and next steps

- MVP live: goals, signal intake, problem finding, bets, experiment checks, health and self-heal, memory.
- Next: connectors for analytics and support tools, automatic experiment results, scheduled competitor watch.
- Validation: interviews with 8–10 target customers to confirm the wedge segment and willingness to pay.
