# Product brief: Test Plan Studio

## Problem

Most bad A/B test decisions are made before the test starts. Teams launch without a clear hypothesis, without knowing whether they have enough traffic, and without a rule for when to stop. Then they check the dashboard every day and ship the first green number. I wanted one tool that covers the whole life of a test: the hypothesis, the sample size and duration, why early stopping is dangerous, a written plan, and a disciplined reading of the result.

## Users

- Product managers planning an experiment who need to know if it is worth running
- Teams without a data scientist on hand who still want sound test design
- Interviewers and hiring managers checking how I think about experimentation

## Goals for 0.1.0

- Cover the full life of a test in one page
- Make the cost of underpowered and peeked tests visible
- Produce a plan a team can paste into a ticket

## Non-goals for 0.1.0

- Running experiments or assigning users
- Bayesian analysis

## Success measures

| Measure | Definition | Target |
|---|---|---|
| Plans written | Plans copied or downloaded per visit | [target] |
| Tests resized | Share of visitors who change the minimum lift after seeing the duration | [target] |
| Results read | Share of visitors who use the result reader | [target] |
