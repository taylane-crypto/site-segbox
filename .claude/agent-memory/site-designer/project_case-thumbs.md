---
name: case-thumbs
description: How the home case-card mockups (assets/cases/*.jpg) were made and the MAPFRE "a confirmar" KPI rule
metadata:
  type: project
---

Home case cards (.cgrid/.cc) use static JPGs in site_segbox/assets/cases/ (mapfre, suhai, capacita, baeta), rendered 2026-09-30 from the hero `.case-hero .win` of each case page (cloned at 547px width, 2x, over the brand color), with the brand bg staying in CSS (.th-mf etc.) so the hover lift still works.

**Why:** the MAPFRE hero KPIs (17.115 / 206 / 21 / 108) are flagged "a confirmar com a MAPFRE" on case-mapfre.html, so they must not appear in destaque; the thumbnail drops that KPI row.

**How to apply:** if a case hero screen changes, re-render the thumbs the same way and keep dropping any "a confirmar" numbers.
