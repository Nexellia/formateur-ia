# PRD — formateur-ia.fr
*Product Requirements Document — source de vérité fonctionnelle*
*Créé le 2026-05-06*

---

## 1. Problème à résoudre

Les formateurs indépendants expérimentés voient leurs clients leur demander des formations sur l'IA, mais ne savent pas comment les concevoir ni les vendre de façon crédible. Ils ont peur de perdre en légitimité s'ils ne maîtrisent pas le sujet.

**Persona cible — Sophie**
- Formatrice indépendante, 42 ans, 8 ans d'expérience (RH, management, bureautique)
- Filtre décisionnel : *"Est-ce que ça me permet de facturer des missions IA dès le mois prochain ?"*
- Freins : peur du ridicule, manque de temps, pas de background technique

---

## 2. Solution

Site vitrine + blog SEO/GEO servant de tunnel vers des formations payantes :

```
LinkedIn / Google / GEO → Blog → Lead Magnet gratuit → Email → Mini-formation 49€ → M1/M2/M3 → Pack 1490€
```

---

## 3. Pages & fonctionnalités

### Pages obligatoires (Phase 1)
| URL | Rôle |
|-----|------|
| `/` | Homepage — accroche + social proof + CTA lead magnet |
| `/ressources/guide-100-prompts-formateurs/` | Page lead magnet principale |
| `/merci/` | Post-optin + upsell mini-formation 49€ |
| `/a-propos/` | Crédibilité formatrice |

### Pages formations (Phase 2)
| URL | Produit | Prix |
|-----|---------|------|
| `/formations/mini-formation/` | Gateway | 49€ |
| `/formations/m1-ia-generative-prompting/` | M1 (9h) | 490€ |
| `/formations/m2-ia-ingenierie-pedagogique/` | M2 (10h) | 690€ |
| `/formations/m3-innovation-pedagogique/` | M3 (9h) | 790€ |
| `/formations/pack-complet/` | Bundles + Pack | jusqu'à 1490€ |

### Blog (Phase 3 — continu)
6 piliers SEO — voir `ROADMAP.md` pour l'ordre de publication.

---

## 4. Fonctionnalités techniques obligatoires

- **Capture email** : formulaire → `/api/subscribe.ts` → webhook Systeme.io (SSR, variable d'env)
- **SEO** : balises meta, Open Graph, Schema.org Article/Person/Course
- **Performance** : Astro static-first, images optimisées, Core Web Vitals > 90
- **RGPD** : Vercel Analytics (sans cookie), pas de tracking tiers

---

## 5. Hors périmètre

- Espace membre / LMS intégré (formations hébergées sur Systeme.io)
- Blog multiauteur
- Commentaires
- E-commerce natif (paiement via Systeme.io externe)

---

## 6. Critères de succès (3 mois)

| Métrique | Cible |
|----------|-------|
| Leads email capturés | 200 |
| Ventes mini-formation 49€ | 20 |
| Trafic organique/mois | 500 visites |
| Positions TOP 10 sur "IA Qualiopi" | ≥ 3 articles |
