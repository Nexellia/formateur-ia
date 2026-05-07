# CLAUDE.md — Site Formateur-IA.fr
*Document de gouvernance du projet — lire avant toute action*
*Créé le 5 mars 2026*

---

## 0. DÉMARRAGE DE SESSION — Protocole

**À chaque nouvelle session sur ce projet :**

1. Lire ce fichier intégralement
2. Vérifier l'état du dossier (`ls` du répertoire projet)
3. Identifier la phase en cours (voir § 7)
4. Consulter le plan de référence si besoin : `C:\Users\nexel\.claude\plans\sprightly-discovering-rain.md`

---

## 1. Contexte Projet

**Site** : formateur-ia.fr (domaine à confirmer/acheter)
**Propriétaire** : Nexellia — Freddy, formatrice IA indépendante
**Mission** : Site vitrine + blog SEO/GEO → tunnel vers formations payantes pour formateurs qui intègrent l'IA
**Concurrent de référence** : `https://www.devenir-formateur-ia.fr/` (Vincent Lafeuillade, sur Podia)

### Tunnel cible
```
LinkedIn / Google / GEO → Blog → Lead Magnet gratuit → Email → Mini-formation 49€ → M1 490€ → M2 690€ → M3 790€ → Pack 1490€
```

### Persona Sophie
Formatrice indépendante, 42 ans, 8 ans d'expérience (RH, management, bureautique). Ses clients lui demandent des formations IA. Peur de perdre en crédibilité. Filtre : "Est-ce que ça me permet de facturer des missions IA dès le mois prochain ?"

---

## 2. Stack Technique

| Élément | Choix |
|---|---|
| Framework | **Astro** (output: hybrid) |
| Hébergement | **Netlify** (gratuit) |
| Repo | **GitHub** — compte `nexellia` (https://github.com/nexellia) |
| Commerce + email | **Systeme.io** (déjà en stack) |
| Styling | **Tailwind CSS** |
| Analytics | **Netlify Analytics** ou Plausible (RGPD-friendly) |
| Contenu blog | Fichiers **Markdown (.md)** dans `src/content/blog/` |

**Règle** : Ajouter un article = créer un fichier `.md` dans le bon dossier pilier. C'est tout.

---

## 3. Structure du Dossier Projet

```
Création_SiteFormateur/
├── CLAUDE.md                        ← ce fichier
├── www.devenir-formateur-ia.fr.url  ← concurrent de référence
└── formateur-ia/                    ← projet Astro (à créer)
    ├── src/
    │   ├── components/
    │   │   ├── layout/              ← Header, Footer, Nav
    │   │   ├── ui/                  ← Button, Card, Accordion, Badge
    │   │   ├── seo/                 ← SEOHead, SchemaOrg, Breadcrumb
    │   │   ├── blog/                ← ArticleCard, TOC, AuthorBox
    │   │   ├── tunnel/              ← LeadMagnetCTA, EmailForm, StickyBar
    │   │   └── formations/          ← PricingCard, PricingTable, Testimonial
    │   ├── content/
    │   │   ├── config.ts            ← Zod schema collection blog
    │   │   └── blog/{pilier}/       ← Articles .md par cluster thématique
    │   ├── layouts/
    │   │   ├── BaseLayout.astro
    │   │   ├── BlogLayout.astro
    │   │   ├── LandingLayout.astro
    │   │   └── FormationLayout.astro
    │   ├── pages/
    │   │   ├── index.astro          ← /
    │   │   ├── formations/          ← hub + mini + m1 + m2 + m3 + pack
    │   │   ├── blog/                ← index + [...slug].astro
    │   │   ├── ressources/          ← guide-100-prompts + checklist
    │   │   ├── a-propos.astro
    │   │   ├── merci.astro          ← post-optin + upsell
    │   │   └── api/subscribe.ts     ← POST → webhook Systeme.io (SSR)
    │   └── styles/
    │       ├── tokens.css           ← Design tokens Nexellia
    │       └── global.css
    ├── astro.config.mjs
    └── package.json
```

---

## 4. Design System

**Source de vérité** : `D:/ClaudeProject/Contenus/Branding/BrandingV2.html`

**Ne jamais inventer de couleurs.** Toujours utiliser les tokens Nexellia :

```css
--color-primary:    #3E5641;   /* Vert Canopée */
--color-secondary:  #5B753C;   /* Vert Sève */
--color-accent:     #906300;   /* Ambre Solaire */
--color-text:       #2C3E2D;   /* Humus Profond */
--color-bg:         #FDFEF9;   /* Ivoire Nexellia */
--color-bg-soft:    #F0F2EB;   /* Brume de Forêt */
--font-body:        'Inter', system-ui, sans-serif;
--font-heading:     'Poppins', system-ui, sans-serif;
```

---

## 5. Produits & Pricing

| Produit | Prix | URL page |
|---|---|---|
| Mini-formation (gateway) | **49€** | `/formations/mini-formation/` |
| M1 — Maîtriser l'IA générative et le prompting (9h) | **490€** | `/formations/m1-ia-generative-prompting/` |
| M2 — IA et ingénierie pédagogique (10h) | **690€** | `/formations/m2-ia-ingenierie-pedagogique/` |
| M3 — Innovation pédagogique : multimédia et automatisation (9h) | **790€** | `/formations/m3-innovation-pedagogique/` |
| Bundle M1+M2 | **990€** | `/formations/pack-complet/` |
| Bundle M2+M3 | **1190€** | `/formations/pack-complet/` |
| Pack Complet | **1490€** | `/formations/pack-complet/` |

Toutes les pages formations ont un CTA vers **Systeme.io** (page paiement externe).

---

## 6. Blog — 6 Piliers SEO

| # | Pilier | Angle différenciant | Priorité |
|---|---|---|---|
| 1 | Prompting formateurs | Prompts métier spécifiques | Haute |
| 2 | Conception avec IA | ROI chiffré ingénierie péda | Haute |
| **3** | **IA + Qualiopi** | **Gap SERP massif — personne ne traite ça** | **Absolue** |
| 4 | Animation IA | Formateurs non-tech | Haute |
| 5 | Créer/vendre sa formation IA | Angle entrepreneurial absent | Moyenne |
| 6 | ROI concret | Avant/après, chiffres réels | Moyenne |

**Premier article à rédiger** : "IA et Qualiopi : ce qui est autorisé, ce qui ne l'est pas en 2026"

**Schema Zod article** (frontmatter obligatoire) :
```yaml
---
title: ""
description: ""          # max 160 caractères
pubDate: 2026-03-05
pilier: qualiopi          # prompting | conception | qualiopi | animation | vente | roi
keywords: []
featured: false
draft: false
leadMagnet: true
---
```

---

## 7. Lead Magnets

| # | Nom | Format | Phase |
|---|---|---|---|
| **LM1** | "Le Guide des 100 Prompts pour Formateurs" | PDF téléchargeable | Phase 1 |
| LM2 | "Checklist : intégrer l'IA dans une séance en 7 étapes" | Page interactive HTML | Phase 2 |
| LM3 | "Diagnostic : es-tu prêt à intégrer l'IA ?" | App interactive (modèle DiagnosticIA) | Phase 3 |

**Page lead magnet principale** : `/ressources/guide-100-prompts-formateurs/`
**Après opt-in** : redirect → `/merci/` → upsell mini-formation 49€

---

## 8. Capture Email — Architecture technique

```
EmailForm.astro (client)
  → fetch POST /api/subscribe.ts
      → webhook SYSTEMEIO_WEBHOOK_URL (variable d'env Netlify, jamais exposée)
          → Systeme.io : tag "lead-formateur" + séquence J0→J14
```

**Variable d'env Netlify** : `SYSTEMEIO_WEBHOOK_URL` — à définir dans Netlify → Site settings → Environment variables

---

## 9. Git & Déploiement

### Dépôt GitHub
- **Compte** : `nexellia` (https://github.com/nexellia)
- **Repo** : `formateur-ia` (à créer)
- **URL** : https://github.com/nexellia/formateur-ia

### Stratégie de branches
```
main      ← Production → Netlify production (domaine futur)
           Protected : PR obligatoire depuis develop, 1 review minimum
           
develop   ← Intégration → Netlify deploy preview automatique
           Reçoit les merges de feature/*
           
feature/* ← Nouvelles fonctionnalités (ex: feature/blog-qualiopi)
           Merge → develop via PR
```

### Workflow quotidien
```
feature/xxx → PR → develop → tests/review → PR → main → Netlify prod
```

### Connexion Netlify
- Branch de production : `main`
- Branch de preview : `develop` (deploy preview automatique)
- Build command : `npm run build`
- Publish directory : `dist/`

---

## 10. Phases d'Implémentation

### ✅ Phase 0 — Plan (terminé)
- Plan validé : `C:\Users\nexel\.claude\plans\sprightly-discovering-rain.md`

### ⏳ Phase 1 — Fondations + Tunnel (8-10h)
1. `npm create astro@latest formateur-ia`
2. Installer packages : `astro add tailwind sitemap netlify mdx`
3. `tokens.css` depuis `BrandingV2.html`
4. `BaseLayout.astro` + `SEOHead.astro` + Header/Footer/Nav
5. Homepage (`index.astro`) — 5 sections
6. Page lead magnet + `EmailForm.astro` + `/api/subscribe.ts`
7. Page `/merci/` avec upsell

### ⏳ Phase 2 — Pages Formations (6-8h)
1. `PricingCard.astro` + `ModuleAccordion.astro`
2. 6 pages formations
3. Liens Systeme.io
4. Séquence email J0→J14 dans Systeme.io

### ⏳ Phase 3 — Blog SEO (continu)
1. `BlogLayout.astro` + collection Astro
2. Premier article : Qualiopi + IA
3. 1 article/semaine

### ⏳ Phase 4 — Diagnostic interactif
- Modèle : `DiagnosticIA/index.html`

---

## 11. Fichiers de Référence

| Fichier | Usage |
|---|---|
| `D:/ClaudeProject/Contenus/Branding/BrandingV2.html` | Design tokens officiels Nexellia |
| `D:/ClaudeProject/Projets/Blog_Lelabodelaproductivite/DiagnosticIA/index.html` | Modèle lead magnet interactif |
| `D:/ClaudeProject/Projets/Blog_Lelabodelaproductivite/DiagnosticIA/DEPLOY.md` | Procédure webhook Systeme.io + Vercel |
| `D:/ClaudeProject/Projets/Blog_Lelabodelaproductivite/GEO_Template.md` | Structure articles GEO-optimisés |

---

## 12. Règles Absolues

1. **Tout le contenu est en français** — aucune exception
2. **Ne jamais exposer `SYSTEMEIO_WEBHOOK_URL` côté client** — uniquement dans `/api/subscribe.ts` (SSR)
3. **Design tokens depuis `BrandingV2.html`** — ne pas inventer de couleurs
4. **Un article = un fichier `.md`** dans le bon dossier pilier de `src/content/blog/`
5. **`output: 'hybrid'`** dans `astro.config.mjs` — statique par défaut + SSR pour `/api/` — adapter : `@astrojs/netlify`
6. **Ne pas toucher à `www.devenir-formateur-ia.fr.url`** — référence concurrentielle uniquement
