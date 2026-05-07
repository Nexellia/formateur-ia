# DECISIONS — formateur-ia.fr
*Choix techniques actés + raison*
*Format : [DATE] — Décision — Raison*

---

## Stack

**2026-05-06 — Framework : Astro (hybrid)**
Raison : génération statique par défaut (performance SEO), SSR activable au besoin pour `/api/subscribe.ts`. Courbe d'apprentissage faible, output HTML propre.

**2026-05-06 — Hébergement : Vercel**
Raison : déploiement automatique depuis Git, CDN global, Analytics RGPD-friendly inclus, tier gratuit suffisant pour le trafic initial.

**2026-05-06 — E-commerce + Email : Systeme.io**
Raison : déjà dans la stack Nexellia, tout-en-un (paiement + séquences email + pages de vente), évite d'intégrer Stripe + Mailchimp séparément.

**2026-05-06 — CSS : Tailwind CSS**
Raison : utility-first, cohérence avec les design tokens Nexellia, pas de CSS mort en production.

**2026-05-06 — Contenu blog : Markdown natif Astro**
Raison : simplicité maximale (1 fichier .md = 1 article), pas de CMS externe à gérer, versionnable via Git.

**2026-05-06 — Analytics : Vercel Analytics**
Raison : RGPD-friendly (pas de cookie), intégré à l'hébergement, données suffisantes pour le stade actuel.

---

## Architecture

**2026-05-06 — Webhook Systeme.io côté serveur uniquement**
Raison : `SYSTEMEIO_WEBHOOK_URL` ne doit jamais être exposée côté client. Toute capture email passe par `/api/subscribe.ts` (route SSR).

**2026-05-06 — output: 'hybrid' dans astro.config.mjs**
Raison : pages statiques par défaut (performance maximale), SSR activé uniquement pour les routes `/api/`. Évite de passer tout le site en SSR.

---

## Design

**2026-05-06 — Design tokens : BrandingV2.html comme source de vérité**
Raison : cohérence avec l'identité Nexellia existante. Aucune couleur ne doit être inventée hors de ce référentiel.

---

*→ Ajouter ici tout nouveau choix technique avec sa date et sa justification.*
