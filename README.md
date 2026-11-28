# Come Barato & Gratis — Restaurantes Ofertas +50%, promos 2x1/gratis, Surprise Boxes y más

**Website & MCP:** `https://come.cheap` (`https://come.cheap/mcp`)  
**Authentication:** OAuth 2.1 (`auth.megawebs.com`) or personal `cbg_` Bearer token from `https://come.cheap/account`

## MCP Client Configuration

```json
{
  "mcpServers": {
    "come-barato-gratis": {
      "type": "http",
      "url": "https://come.cheap/mcp"
    }
  }
}
```

## Available Tools (11)
- `comebarato_get_profile` — Load saved dietary exclusions, anchors, budget, language & Madrid local time
- `comebarato_save_profile` — Save dietary preferences or load `no_red_meat` preset
- `comebarato_get_history` — View past published guides and 21-day anti-repeat venue history
- `comebarato_log_feedback` — Mark venues as `visited`, `loved`, `disliked`, or `blacklisted`
- `comebarato_search_places` — Bulk-search Google Maps, web menus, TheFork, Uber Eats, Just Eat & Too Good To Go
- `comebarato_fetch_pages` — Bulk-fetch up to 10 restaurant/menu URLs with text & candidate photos
- `comebarato_find_dish_images` — Bulk-verify or discover real non-stock dish photos
- `comebarato_publish_guide` — Compile Markdown + verified dish photos into warm-paper HTML (`/r/<id>`), printable PDF (`/r/<id>.pdf`) & inline MCP App
- `comebarato_find_deals` — One-call search + PDF shortcut
- `comebarato_generate_pdf` — Re-render PDF for an existing guide
- `comebarato_get_debug_logs` — Inspect tenant-scoped tool telemetry and correlation IDs
