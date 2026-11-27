---
name: plato-espana
description: Come Barato & Gratis — Encuentra restaurantes con ofertas +50%, promos 2x1/gratis, platos baratos y Surprise Boxes (Too Good To Go) a tu alrededor en España (cheap restaurants, 50% off deals, surprise boxes), filtrado por perfil dietético e historial anti-repetición, con guía visual PDF multipágina.
---

# Come Barato & Gratis — Restaurantes Ofertas +50%, Surprise Boxes y más

Usa el conector MCP `plato-espana` (`https://plato.megawebs.com/mcp`) cada vez que el usuario busque **comer barato**, **restaurantes cerca**, **ofertas hasta -50%**, **descuentos 2x1/gratis**, **menú del día**, **poké/sushi barato** o **Surprise Boxes (Too Good To Go)** en España (incluido en inglés o chino).

## Workflow

1. **Carga el perfil guardado primero:** Llama a `plato_get_profile` para cargar exclusiones dietéticas, gustos, barrios habituales, número de comensales, presupuesto e idioma (`es`, `en` o `zh`).
   - Si el usuario pide cambiar preferencias o cargar el preset sin carne roja/cerdo, llama a `plato_save_profile`.
2. **Busca ofertas de platos y genera el PDF visual:** Llama a `plato_find_dish_deals` con la ubicación (o ancla guardada), `craving` opcional, `party_size`, `budget_eur`, `include_tgtg_on_route: true`, `avoid_repeats: true` y `generate_pdf: true`.
3. **Historial y reexportación:** Usa `plato_get_history` para ver informes previos y `plato_generate_visual_report` para regenerar el PDF/guía web.
4. **Presenta resultados verificados:**
   - Empieza por las cestas de platos más baratas y ofertas públicas verificadas, mostrando el nombre original en español junto al idioma del usuario.
   - Presenta las **Surprise Boxes (Too Good To Go)** de paso indicando confirmar stock en vivo en la app de Too Good To Go.
   - Nunca inventes precios, descuentos ni disponibilidad en directo.
   - Recuerda brevemente confirmar alérgenos/ingredientes y precios finales directamente con el restaurante, y aclara que la herramienta es solo informativa (sin pedidos ni reservas).
   - Incluye los enlaces clicables al **PDF Visual** (`pdf_url`), **Guía Web** (`web_url`) y rutas a pie de Google Maps.
   - Cuando el usuario visite o valore un sitio, llama a `plato_log_feedback` para no repetirlo.
