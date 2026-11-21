# 0002: Round duration up to whole weeks

**Status:** accepted, 0.1.0

## Context

Behaviour differs between weekdays and weekends. A 10-day test overweights weekdays.

## Decision

Show the days needed to fill the sample and plan whole weeks.

## Tradeoff

- Tests run a little longer than the minimum
- Results are less biased by the day of the week
