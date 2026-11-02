# Evolve

**The product team you can’t afford.** Evolve listens to your customers, watches your competitors, and improves your product every week.

Evolve is a self-evolving product loop. You give it a business goal. It turns that goal into a north star and guardrails, reads what users and the market are saying, ranks the fixes worth making, checks your A/B results, heals regressions, and remembers what every cycle taught it. A person approves every launch until the system has earned the right to act alone.

> Anyone can build v1 now. The winners make v2, v3 and v50 better.

---

## Why this exists

Every product should keep getting better, shaped by experience the way a person is. In practice, the loop that makes that happen (research → prioritise → build → test → learn) runs at the speed of human teams: slow, expensive and inconsistent.

Large companies throw product managers, researchers and data scientists at the problem. Most companies can’t. They have more signals than people to act on them, so they guess, ship, and rarely find out what worked.

Analytics and experimentation tools help a team that already exists make decisions. Evolve does the deciding work for the team you don’t have yet.

## How the loop works

```
   ┌──────────┐   ┌──────────┐   ┌────────────┐   ┌──────────────┐   ┌──────────┐
   │ 1 Steer  │ → │ 2 Listen │ → │ 3 Bets     │ → │ 4 Experiment │ → │ 5 Health │
   │ AI CPO   │   │ users +  │   │ impact ×   │   │ launch or    │   │ guardrail│
   │ sets the │   │ market   │   │ confidence │   │ roll back    │   │ breaches │
   │ goals    │   │          │   │ ÷ weeks    │   │              │   │ → heal   │
   └──────────┘   └──────────┘   └────────────┘   └──────────────┘   └──────────┘
        ▲                                                                  │
        └──────────────────────── 6 Memory ◄───────────────────────────────┘
                every decision updates the next cycle’s confidence
```

| Stage | What Evolve does | What you do |
|---|---|---|
| **Steer** | The AI CPO turns your business goal into a north star metric, the drivers that move it (a metric tree), and hard and soft guardrails. | Describe the product and goal. Approve or ask again. |
| **Listen** | Groups survey answers, support tickets, reviews, interview notes, telemetry observations and competitor launches into ranked problems with quotes as evidence. A competitor move only counts when users show the same need. | Paste signals or import a CSV. |
| **Bets** | Proposes one testable fix per problem, estimates impact, confidence and weeks to ship, and ranks them by the steepest step per week of work. Reserves one slot for a bolder exploration bet. Confidence reflects what earlier cycles learned. | Edit any estimate. Start a test. |
| **Experiments** | Takes your A/B counts and reports the chance the variant beats control, with a launch, wait or roll-back recommendation. | Run the test in your own product. Enter counts. Decide. |
| **Health** | Watches the north star and guardrails. When one breaks, the AI diagnoses the likely cause (recent launches, your notes) and proposes the safest, most reversible fix. | Log a weekly reading. Apply the fix. |
| **Memory** | Records every approval, launch, rollback and heal. Every AI step reads it. You can also ask the AI CPO anything about your workspace. | Add notes. Ask questions. Export. |

### Principles

- **Agents propose, people approve, autonomy is earned.** Reversible, low-risk actions (a rollback, a micro-survey) can eventually run on their own. Launches ask first. Pricing always asks.
- **Learning velocity, not shipping velocity.** Measure the time from a pain signal to a proven fix, and the share of tests that move the north star. Shipping fast in the wrong direction is faster waste.
- **Guardrails beside every goal.** A loop that optimises one number will game it. Hard limits stop that.
- **Competitors raise priority; they never set the roadmap.** “A rival did X” matters only when “our users want X” is also true.

## Try it

### Run it locally

No build step and no dependencies. It is one HTML file.

```bash
git clone https://github.com/AgarwalVedika/evolve.git
cd evolve
python3 -m http.server 8000
# open http://localhost:8000
```

Click **Load example** to explore a pre-filled workspace for an AI email assistant (invented data), including a guardrail breach waiting in Health. Or start in **Steer** with your own product.

To turn on AI, paste an Anthropic API key into the banner. The key stays in your browser’s local storage and is sent only to `api.anthropic.com`. Without a key, every step still works by hand.

### Host it on GitHub Pages

Settings → Pages → deploy from the `main` branch, root folder. The app and the example load as static files.

### Inside claude.ai

The same app runs as a Claude artifact, where the workspace is stored server-side and shared with whoever you share the page with, and AI runs on each viewer’s own Claude account. No API key needed.

### The two-minute concept demo

[`demo/`](demo/index.html) is a scripted, fully simulated walk through one cycle (approve goals → test a bet → launch → roll back → self-heal). It is useful for explaining the idea in a meeting; the app in `index.html` is the real product.

## What’s in the repo

```
index.html                       the Evolve app (self-contained)
demo/index.html                  scripted concept demo on simulated data
examples/example-workspace.json  invented example workspace (AI email assistant)
examples/example-signals.csv     sample CSV for the Listen import
docs/PITCH.md                    the one-page pitch: problem, customer, moat, roadmap
```

## How it’s built

- **One file, no framework.** Plain HTML, CSS and JavaScript. Fonts from Google Fonts.
- **Storage.** Inside claude.ai: the artifact’s document store. Self-hosted: `localStorage` in your browser. Export the whole workspace as JSON from the Memory tab.
- **AI.** Every AI step sends a single prompt containing the workspace context (goals, guardrails, recent memory, bet history) and asks for a strict JSON shape, which the app validates before saving. Steps: propose goals, cluster signals into problems, generate and score bets, diagnose a guardrail breach, answer questions. Models: Claude Sonnet by default.
- **Statistics.** Experiment results use a two-proportion comparison (normal approximation) to estimate the chance the variant beats control. Fewer than 200 users per arm is reported as too early to call.

## Data and privacy

- Self-hosted, nothing leaves your browser except the AI prompts sent to Anthropic with your key.
- Prompts contain the signals and workspace text you entered. Don’t paste personal data you aren’t allowed to process with a third-party AI service.
- Calling the Anthropic API directly from a browser exposes the key to anyone with access to that browser. That is fine for a personal MVP; a team deployment should proxy AI calls through a small server.

## Roadmap

1. **Connectors for signals and metrics:** product analytics, app-store and review sites, support desks, survey tools, Stripe or Shopify, so Listen and Health fill themselves.
2. **Experiment platform integration:** start tests and pull results automatically instead of typing counts.
3. **Competitor watch:** monitor rivals’ changelogs, pricing pages and reviews on a schedule.
4. **Earned autonomy ladder:** per action type, track the loop’s record and let owners raise autonomy once it has earned it.
5. **Cross-customer learning:** with consent, priors from what worked for similar products, which solves cold start and small samples.
6. **Server mode:** shared team workspaces, API-key proxy, audit log.

## Origin

In 2023, as a product case study for an AI catalog-intelligence team at a delivery marketplace, I drew the end-to-end pipeline for a suite of ML products, with a dashed line from product metrics back to the start. Evolve is that dashed line turned into the product.

## Status

Early MVP, built to test the idea with real products. Feedback, issues and pull requests welcome.

No licence has been chosen yet, so all rights are reserved by the author for now.
