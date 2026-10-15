# Vivara for Claude

Use [Vivara](https://get.vivaralifestyle.com), the nutrition and fitness tracker for iPhone and Android, from a
conversation with Claude. Ask how your day is going, log a meal or a glass of water in plain words, log the meals and
recipes you already saved in Vivara, and review how your calories, protein and weight have moved over the past weeks.

## What's in the plugin

- **The Vivara connector** (`.mcp.json`): Vivara's remote MCP server at `https://mcp.vivaralifestyle.com/mcp`. You sign
  in with your Vivara account the first time you connect.
- **Two skills** that tell Claude how to use it well:
  - `log-meal`: logs food from your saved foods, meals and recipes first, then from Vivara's food database, and logs
    water in the unit you use.
  - `nutrition-review`: reads your day or a date range, compares it with your Vivara goals, and suggests what to eat
    next.

The skills are Markdown instructions only. The plugin contains no scripts, hooks or other code.

## What you need

A Vivara account, free on the [App Store](https://apps.apple.com/app/id6759578335) and
[Google Play](https://play.google.com/store/apps/details?id=com.melo.stronglifestyle). When you connect, sign in the
same way you do in the app (Apple, Google or email). The connector is free on every Vivara plan.

## What it accesses

The plugin talks only to `https://mcp.vivaralifestyle.com/mcp`, and only after you sign in and approve access on
Vivara's own consent page. With that access Claude can:

- See your food diary, saved foods, meals and recipes, calorie and macro goals, water, weight check-ins, workouts,
  fasting and your weight goal.
- Search Vivara's food database.
- Add foods and water to today's diary, and remove foods it added today. It can't change anything you logged in the
  Vivara app.

Apple Health and Health Connect data, such as steps and active energy, is not shared. Vivara logs only which tool ran,
whether it worked and how long it took, never what you asked or what was returned. What Claude does with the data is
covered by Anthropic's privacy policy; what Vivara does is covered by the
[Vivara privacy policy](https://sites.google.com/view/vivara-app-privacy/home).

## Try asking

- "How much protein do I have left today?"
- "Log my usual breakfast and a 500 ml bottle of water."
- "How did my calories look over the last two weeks?"

## Disconnect

In the Vivara app, open Profile, then Use Vivara in Claude, and select Disconnect. You can also remove the connector
in Claude under Customize, then Connectors. Deleting your Vivara account disconnects it too.

## Support

Setup guide: [mcp.vivaralifestyle.com](https://mcp.vivaralifestyle.com/). Questions or problems:
[john@vivaralifestyle.com](mailto:john@vivaralifestyle.com).

## License

MIT. See [LICENSE](LICENSE).
