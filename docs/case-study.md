# Case study: Test Plan Studio

## The question

Most bad A/B test decisions are made before the test starts. Teams launch without a clear hypothesis, without knowing whether they have enough traffic, and without a rule for when to stop. Then they check the dashboard every day and ship the first green number. I wanted one tool that covers the whole life of a test: the hypothesis, the sample size and duration, why early stopping is dangerous, a written plan, and a disciplined reading of the result.

## Approach

I listed the decisions a PM has to make before, during and after a test, then built one tab for each stage. I used standard, explainable methods (two-proportion and normal approximations, Bonferroni, chi-square for the split) and checked the sample sizes against SciPy. The peeking tab runs A/A simulations in the browser with a fixed random seed, so every visitor sees the same result for the same inputs.

## Findings

### 1. Checking daily and stopping at the first win multiplies false winners (from the simulator, not real data)

With the sample inputs (3.2% baseline, 2,000 users a group a day, 28 days, 5% significance), 1,000 A/A tests gave 4.4% false winners when read once at the end and 26.1% when stopped at the first significant day: about six times more. The exact numbers change with your inputs and the random seed. The direction does not.

## Decisions

### Fixed-horizon tests by default, with a peeking demo

Sequential methods allow early looks but are harder to explain and to configure. Most teams that peek are using fixed-horizon maths.

**Decision:** Size tests for a fixed horizon, read once, and show with a simulation what goes wrong otherwise. Point to sequential tests in the plan for teams that need early looks.

Full record: [decisions/0001-fixed-horizon.md](decisions/0001-fixed-horizon.md)

### Round duration up to whole weeks

Behaviour differs between weekdays and weekends. A 10-day test overweights weekdays.

**Decision:** Show the days needed to fill the sample and plan whole weeks.

Full record: [decisions/0002-whole-weeks.md](decisions/0002-whole-weeks.md)

### Bonferroni for several variants

Several variants raise the chance of a false winner.

**Decision:** Split the significance level evenly across comparisons with control.

Full record: [decisions/0003-bonferroni.md](decisions/0003-bonferroni.md)

### Sample ratio check before the verdict

A broken split usually means an assignment or logging bug, and the result cannot be trusted whatever the p-value.

**Decision:** Run a chi-square sample ratio test first and flag p under 0.001.

Full record: [decisions/0004-srm-first.md](decisions/0004-srm-first.md)

## What I learned as a PM

- The most valuable output is the written plan, not the sample size: it fixes the decision rule before anyone sees data
- Showing the cost of peeking with a simulation persuades better than a rule
- A minimum lift has to be a business choice. The duration curve turns it into a visible trade-off

## Limits

- Normal approximations are less accurate for very small samples or rates near 0% or 100%
- Only one variant can be read at a time in the result reader
- No sequential testing or variance reduction yet

## What I would do next

1. Add a sequential test option with adjusted thresholds
2. Add a variance reduction estimate (CUPED) using pre-period data
3. Save plans in the browser and compare the plan with the result automatically

## My role

I framed the problem, made the product calls, checked every number and wrote the conclusions. Claude (Anthropic) wrote the code with me. 
