---
name: log-meal
description: Log food or water to the user's Vivara diary. Use when the user says they ate or drank something, shares a photo of a meal, mentions a saved meal or recipe, or asks to log, add or track food or water in Vivara.
---

# Log food and water to Vivara

Vivara logs to the user's diary for today, on their local date. Past days are edited in the Vivara app, so if the
user wants to log yesterday, say that and offer to log it as today only if they want that.

## Food

1. **The user's own foods first.** When they name something they may have saved ("my usual breakfast", "my protein
   shake", a recipe name), call `list_my_foods` with one distinctive word from it. If a result fits, log it with its
   `my_food_id`, and set `servings` when they had more or less than one. A saved meal logs every food in it at once.
2. **Otherwise search.** For each food, call `search_foods` with the brand and the food when the user named a brand
   (for example "chobani greek yogurt"). Pick the closest match and log it with its `food_id`, plus `servings` or
   `grams`. `grams` only works with a `food_id`.
3. **Estimate only as a last resort.** If nothing fits, log the item by `name` with your best `calories`,
   `protein_g`, `carbs_g` and `fat_g`, and tell the user the numbers are an estimate.
4. **Photos.** Name each item and its portion from the photo, then follow steps 1 to 3 for each one, in one
   `log_food` call.
5. **Meal.** Pass `meal` (Breakfast, Lunch, Dinner or Snack) when the user says one. Otherwise leave it out and Vivara
   picks the meal for the time of day.
6. **Portions.** Ask only when the portion changes the numbers a lot and the user gave no hint ("a bowl of pasta").
   Otherwise use the default serving and say which serving you used.

## Water

Call `log_water` with the amount in the unit the user said, `ml` or `oz`. If they gave no unit, leave `unit` out and
Vivara uses the unit they picked in the app. Log one drink per call.

## Mistakes and repeats

- `remove_logged_food` removes a food logged from Claude today, using the id `log_food` returned. Foods logged in the
  Vivara app are removed in the app.
- Vivara ignores the exact same `log_food` or `log_water` call made again within 10 minutes, so a retry never logs
  twice. If the user really had a second one, call it again with `allow_duplicate` set to true.

## Reply

Keep it short: what was logged (name, calories and protein), then how many calories and how much protein are left
today, from the tool's `remaining`. Don't paste the raw tool output.
