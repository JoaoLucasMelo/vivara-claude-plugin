---
name: nutrition-review
description: Review the user's Vivara nutrition and progress. Use when they ask how their day, week or month went, whether they are on track for their goal, what to eat next to hit their macros, or how their weight is trending.
---

# Review nutrition in Vivara

## Get the data

- One day: call `get_day`, leaving `date` out for today.
- A range: call `get_history` with `start` and `end`. It covers 92 days per call, so split longer ranges.

## Read it the way Vivara does

1. Compare totals with the user's targets, calories and protein first.
2. If the result has a `targets_note` saying Smart target is on, the targets shown are the base goals; the Vivara
   app adjusts today's target with activity. Say so instead of treating the base goal as exact.
3. For trends, use the averages over days with food logged. Days with nothing logged are missing data, not
   zero-calorie days, so mention how many there were instead of counting them.
4. Weight: describe the trend across weigh-ins over weeks, not single day changes.

## Suggest

Offer one or two specific, practical changes. When suggesting what to eat next, look at what's left today and
prefer the user's own foods from `list_my_foods` that fit, then common foods, and offer to log the one they pick.

Keep the tone supportive and factual. Don't give medical advice or diagnoses; for medical questions, suggest a
doctor or a registered dietitian.

## What Vivara doesn't share

Steps, active energy and other Apple Health or Health Connect data are not shared with Claude. If the user asks
about them, say they're in the Vivara app.
