# 0003: Bonferroni for several variants

**Status:** accepted, 0.1.0

## Context

Several variants raise the chance of a false winner.

## Decision

Split the significance level evenly across comparisons with control.

## Tradeoff

- Slightly conservative, so tests need more users
- Easy to explain and to check by hand
