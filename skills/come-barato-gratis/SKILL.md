---
name: come-barato-gratis
description: "Come Barato & Gratis — Encuentra restaurantes con ofertas +50%, promos 2x1/gratis, platos baratos y Surprise Boxes (Too Good To Go) a tu alrededor en España (cheap restaurants, 50% off deals, surprise boxes, 西班牙便宜餐厅/半价优惠/惊喜盲盒), con búsqueda en lote, fotos reales verificadas, perfil dietético, historial anti-repetición y guía editorial PDF multipágina."
---

# Come Barato & Gratis (`https://come.cheap`)

## Optimal Agent-First Workflow

1. **Load Profile & Clock (`comebarato_get_profile`)**
   - Always call `comebarato_get_profile` first on a new conversation to get the authenticated user's saved dietary exclusions, cautions, preferred cuisines, default anchors, party size, budget, language, and current Madrid date/time.
2. **Bulk Discovery (`comebarato_search_places`)**
   - Call `comebarato_search_places` with 2–6 targeted queries (e.g., `["poke barato", "cantonese", "thefork -50%"]`) and `sources: ["maps", "web", "thefork", "ubereats", "justeat", "tgtg"]`.
   - Prefer venues with `already_recommended: false` unless the user asks for favorites.
3. **Bulk Menu & Photo Inspection (`comebarato_fetch_pages` + `comebarato_find_dish_images`)**
   - Fetch up to 10 promising menu/TheFork/delivery URLs in parallel via `comebarato_fetch_pages` to verify real dish names and `€` prices.
   - Resolve/verify real non-stock dish photos in parallel via `comebarato_find_dish_images` (pass `candidate_urls` from `fetch_pages` or let it search real dish photos).
4. **Curate & Publish (`comebarato_publish_guide`)**
   - Write an engaging, concise, well-organized Markdown guide in the user's language (preserving original *Spanish dish names* in italics/parentheses for easy ordering), including:
     - Summary comparison table (`Option | Recommended Order | Party Total`)
     - Per-venue sections (`### 1. Venue Name · Cuisine`) with dietary verdicts (`优先/Prefer`, `适量/Moderate`, `避开/Avoid`, `待核实/Verify`), walking navigation links, and verified dish prices
     - On-route Too Good To Go Surprise Boxes without detours
   - Pass `markdown`, `dish_images` (matched to headings), and `venues_to_log` into `comebarato_publish_guide`.
   - Return the permanent clickable `short_url` (`https://come.cheap/r/<id>`) and `pdf_url` (`https://come.cheap/r/<id>.pdf`) — the MCP App also renders the warm-paper guide inline!

## Shortcut & Diagnostics
- For a fast 1-call search without custom editorial curation, use `comebarato_find_deals`.
- Use `comebarato_save_profile` (or `preset: "no_red_meat"`) when updating preferences, `comebarato_log_feedback` to record loved/visited/disliked venues, and `comebarato_get_debug_logs` if a tool fails.
- Never invent prices, fake discounts, or live Too Good To Go stock.
