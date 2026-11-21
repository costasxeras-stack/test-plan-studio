# 0001: Fixed-horizon tests by default, with a peeking demo

**Status:** accepted, 0.1.0

## Context

Sequential methods allow early looks but are harder to explain and to configure. Most teams that peek are using fixed-horizon maths.

## Decision

Size tests for a fixed horizon, read once, and show with a simulation what goes wrong otherwise. Point to sequential tests in the plan for teams that need early looks.

## Tradeoff

- Teams cannot stop early for a winner
- The method stays simple enough to explain in a review
