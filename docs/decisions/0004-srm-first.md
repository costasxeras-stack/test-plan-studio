# 0004: Sample ratio check before the verdict

**Status:** accepted, 0.1.0

## Context

A broken split usually means an assignment or logging bug, and the result cannot be trusted whatever the p-value.

## Decision

Run a chi-square sample ratio test first and flag p under 0.001.

## Tradeoff

- Adds a step to every reading
- Catches the most common silent failure in experiments
