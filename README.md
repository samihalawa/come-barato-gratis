# Plato — Spain Restaurant & Dish Deals

Discover specific dishes, sourced menu prices, public restaurant offers (TheFork, Uber Eats, Just Eat, menú del día), and on-route Too Good To Go pickup suggestions across Spain — tailored to your dietary preferences with anti-repeat memory and visual multi-page PDF dining guides.

## Authentication & Setup
- **Remote MCP Endpoint:** `https://plato.megawebs.com/mcp`
- **OAuth 2.1:** Connect directly in ChatGPT or Claude via Megawebs Account (`https://auth.megawebs.com`).
- **Personal Bearer Token:** Manage your saved preferences and optional CLI Bearer tokens at `https://plato.megawebs.com/account`.

## Tools
- `plato_get_profile` — Load your saved dietary exclusions, preferred cuisines, default anchors, language, party size, and budget.
- `plato_save_profile` — Save preferences or load a dietary preset (`no_red_meat` / `default`).
- `plato_find_dish_deals` — Search nearby restaurants, rank dietary-safe dish baskets cheapest-first, surface public deals & on-route Too Good To Go options, and generate a visual PDF.
- `plato_generate_visual_report` — Re-render or export a visual PDF/web guide for an existing report.
- `plato_get_history` — List past visual PDF reports and recent recommendations.
- `plato_log_feedback` — Mark venues as visited, loved, disliked, or blacklisted to prevent repeats.

## Scope & Disclaimers
Plato is an informational discovery tool. It is not affiliated with TheFork, Uber Eats, Just Eat, or Too Good To Go, does not place orders or book tables, and does not guarantee live Too Good To Go stock or allergen-free preparation. Always confirm ingredients and final prices with the venue.

## Links
- Website & Account: `https://plato.megawebs.com`
- Support: `https://plato.megawebs.com/support`
- Privacy Policy: `https://plato.megawebs.com/privacy`
- Terms of Service: `https://plato.megawebs.com/terms`
