# Ship or Skip: a Bayesian launch room

**Live demo:** https://shriyashekatkar25-byte.github.io/ship-or-skip/

An interactive product-decision prototype. An AI analytics assistant (think natural-language BI tools like Databricks Genie) changed how it ranks candidate answers. Should the change ship to every workspace?

The page makes that call the way a product director would:

- **Frames the decision:** customer problem, the change, the success metric (answer acceptance rate) and four guardrails (latency, cost per answer, governance, rephrase rate).
- **Runs a live A/B test** on simulated traffic, updating a Beta posterior for each arm as questions come in.
- **Uses Monte Carlo** (20,000 simulated worlds) to compute the two numbers leadership needs: the probability B beats A, and the expected loss if we ship and are wrong.
- **Writes the memo:** a director-style launch memo that rewrites itself from the evidence, covering decision, risks, staged rollout and next step.
- **Shows the production path:** the SQL and Python I'd run against real event logs in a lakehouse.

## Why this matters for product management

Most launch reviews stall on "is it statistically significant?" This prototype replaces that with a decision rule built on risk: ship when B is very likely better **and** the expected cost of being wrong is below a limit the team agreed on in advance. That makes the decision explainable to engineers, executives and customers.

## Methods (UCLA Stats 102C, Monte Carlo Methods)

| Method | Where it's used |
|---|---|
| Beta-Binomial conjugate updating | Each arm's belief about its true acceptance rate |
| Informative vs flat vs skeptical priors | How much past launches should count |
| Monte Carlo estimation | P(B > A), expected loss, credible range of the lift |

## Try it

Pick what's secretly true (B better, barely better, no difference, worse) and a prior, then run days of traffic. Watch when the room says **Ship it**, **Keep testing** or **Skip it**, and how the memo changes.

---

Built by **Shriya Shekatkar** as part of APM Lab, a series of product prototypes applying Monte Carlo methods to real product decisions. Unofficial concept prototype: all data is simulated and it is not affiliated with any company.
