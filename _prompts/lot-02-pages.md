# Lot 02 — Layouts de base + composants structurels
*À lire après system-prompt.md et lot-01-init.md*

## Prérequis
- Lot 01 validé (`[x]` dans ROADMAP.md)
- Projet Astro fonctionnel avec tokens CSS en place

## Objectif
Créer l'armature du site : layouts réutilisables, SEO de base, Header/Footer.

## Fichiers à créer

### `src/layouts/BaseLayout.astro`
Props attendues : `title`, `description`, `ogImage?`, `canonical?`
Inclure : `SEOHead`, `Header`, `Footer`, slot principal.

### `src/components/seo/SEOHead.astro`
Balises : `<title>`, `<meta description>`, Open Graph (og:title, og:description, og:image, og:url), Twitter Card, `<link rel="canonical">`, `<link rel="sitemap">`.
Schema.org `WebSite` en JSON-LD sur toutes les pages.

### `src/components/layout/Header.astro`
- Logo texte "Formateur-IA" (lien vers `/`)
- Navigation : Accueil | Formations | Blog | À propos
- CTA bouton : "Obtenir le guide gratuit" → `/ressources/guide-100-prompts-formateurs/`
- Responsive : hamburger menu sur mobile

### `src/components/layout/Footer.astro`
- Liens : Mentions légales | Politique de confidentialité | Contact
- Copyright Nexellia
- Liens réseaux : LinkedIn

### `src/components/layout/Nav.astro`
Navigation mobile (drawer/menu burger).

### `src/layouts/BlogLayout.astro`
Étend BaseLayout. Ajoute : fil d'Ariane, AuthorBox, TOC sidebar, Schema.org Article.

## Composants UI de base
### `src/components/ui/Button.astro`
Props : `href`, `variant` (primary | secondary | ghost), `size` (sm | md | lg).

### `src/components/ui/Badge.astro`
Props : `label`, `color`.

## Page de test
Créer `src/pages/index.astro` minimal avec BaseLayout pour valider le rendu.

## Critères de validation
- [ ] `npm run dev` → homepage visible avec Header et Footer
- [ ] SEO Head visible dans le source HTML
- [ ] Menu hamburger fonctionnel sur mobile (tester à 375px)
- [ ] Aucune erreur TypeScript

## Une fois validé
Mettre `[x]` sur les Lots 01 et 02 dans `_docs/ROADMAP.md`.
Ajouter entrée dans `_docs/CHANGELOG.md`.
Démarrer `lot-03-homepage.md`.
