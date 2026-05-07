# ROADMAP — formateur-ia.fr
*Lots + statuts — mise à jour après chaque lot validé*
*Dernière mise à jour : 2026-05-06*

---

## Légende
- `[ ]` À faire
- `[~]` En cours
- `[x]` Validé

---

## Phase 0 — Plan ✅
- [x] Définition du persona et du tunnel
- [x] Choix de la stack (Astro + Vercel + Systeme.io)
- [x] CLAUDE.md + PRD.md rédigés
- [x] Structure de dossiers créée

---

## Phase 1 — Fondations + Tunnel
*Objectif : site en ligne avec capture email fonctionnelle*

- [ ] **Lot 01 — Init projet Astro**
  - `npm create astro@latest formateur-ia`
  - Packages : tailwind, sitemap, vercel, mdx
  - `tokens.css` depuis BrandingV2.html
  - `astro.config.mjs` en mode `hybrid`

- [ ] **Lot 02 — Layout de base**
  - `BaseLayout.astro`
  - `SEOHead.astro` (meta, OG, canonical)
  - `Header.astro` + `Footer.astro` + `Nav.astro`

- [ ] **Lot 03 — Homepage**
  - Section Hero (accroche + CTA)
  - Section Problème/Solution
  - Section Lead Magnet teaser
  - Section Formations aperçu
  - Section Témoignages (placeholders)

- [ ] **Lot 04 — Tunnel lead magnet**
  - Page `/ressources/guide-100-prompts-formateurs/`
  - `EmailForm.astro`
  - `/api/subscribe.ts` → webhook Systeme.io
  - Page `/merci/` + upsell mini-formation

- [ ] **Lot 05 — Page À propos**
  - Storytelling + crédibilité
  - Photo + bio

---

## Phase 2 — Pages Formations
*Objectif : 6 pages produit avec liens Systeme.io*

- [ ] **Lot 06 — Composants formations**
  - `PricingCard.astro`
  - `ModuleAccordion.astro`
  - `Testimonial.astro`

- [ ] **Lot 07 — 6 pages formations**
  - Mini-formation, M1, M2, M3, Bundles, Pack

- [ ] **Lot 08 — Séquence email Systeme.io**
  - J0 → J14 : 5 emails configurés

---

## Phase 3 — Blog SEO
*Objectif : 6 articles piliers + trafic organique*

- [ ] **Lot 09 — Infrastructure blog**
  - `BlogLayout.astro`
  - Collection Astro + schema Zod
  - Pages index blog + `[...slug].astro`
  - `ArticleCard.astro` + `TOC.astro` + `AuthorBox.astro`

- [ ] **Lot 10 — Article #1 (priorité absolue)**
  - Pilier : Qualiopi
  - Titre : "IA et Qualiopi : ce qui est autorisé, ce qui ne l'est pas en 2026"

- [ ] **Lot 11 → 15 — Articles suivants**
  - 1 article/semaine, ordre : Qualiopi > Prompting > Conception > Animation > ROI > Vente

---

## Phase 4 — Diagnostic interactif
*Objectif : lead magnet haute valeur*

- [ ] **Lot 16 — DiagnosticIA**
  - Modèle : `DiagnosticIA/index.html`
  - Intégration dans `/ressources/diagnostic/`
