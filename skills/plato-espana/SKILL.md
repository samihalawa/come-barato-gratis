---
name: plato-espana
description: Discover specific dishes, sourced menu prices, public restaurant offers (TheFork, Uber Eats, Just Eat), and on-route Too Good To Go pickup suggestions across Spain, filtered by the user's saved dietary profile and anti-repeat history, with a visual multi-page PDF dining guide.
---

# Plato — Spain Restaurant & Dish Deals

Use the `plato-espana` MCP connector (`https://plato.megawebs.com/mcp`) whenever the user asks for restaurants, specific dishes, cheap meal baskets, discounts, or Too Good To Go options in Spain.

## Workflow

1. **Load saved profile first:** Call `plato_get_profile` to load the authenticated user's saved dietary exclusions, preferred cuisines, default anchors, party size, budget, and output language (`es`, `en`, or `zh`).
   - If the user asks to update preferences or load the `no_red_meat` preset, call `plato_save_profile`.
2. **Find dish deals & generate visual PDF:** Call `plato_find_dish_deals` with the user's location (or saved default anchor), optional `craving`, `party_size`, `budget_eur`, `include_tgtg_on_route: true`, `avoid_repeats: true`, and `generate_pdf: true`.
3. **History & re-exports:** Use `plato_get_history` to list past reports and `plato_generate_visual_report` to re-export an existing report PDF.
4. **Present grounded results:**
   - Lead with the cheapest sourced dish baskets and public offers, showing original Spanish dish names alongside the user's language.
   - Present on-route Too Good To Go options as pickup suggestions and tell the user to confirm live bag availability in the Too Good To Go app unless live stock is explicitly verified.
   - Never invent menu prices, discount terms, allergen safety, or live stock.
   - Provide the clickable **Visual PDF** (`pdf_url`) and **Interactive Web Guide** (`web_url`) returned by the tool, plus Google Maps walking links.
   - When the user visits or rates a restaurant, call `plato_log_feedback` so future searches avoid repeating it.
