# Lot 01 — Initialisation projet Astro
*À lire après system-prompt.md*

## Objectif
Créer le projet Astro avec la configuration de base, les design tokens et les dépendances approuvées.

## Commandes à exécuter
```bash
# Dans le dossier SiteFormateur/
npm create astro@latest formateur-ia -- --template minimal --typescript strict --no-install --no-git

cd formateur-ia
npm install
npx astro add tailwind sitemap vercel mdx
```

## Fichiers à créer

### `astro.config.mjs`
```js
import { defineConfig } from 'astro/config';
import tailwind from '@astrojs/tailwind';
import sitemap from '@astrojs/sitemap';
import vercel from '@astrojs/vercel/serverless';
import mdx from '@astrojs/mdx';

export default defineConfig({
  site: 'https://formateur-ia.fr',
  output: 'hybrid',
  adapter: vercel(),
  integrations: [tailwind(), sitemap(), mdx()],
});
```

### `src/styles/tokens.css`
Extraire les variables CSS depuis `D:/ClaudeProject/Contenus/Branding/BrandingV2.html`.
Les intégrer dans `:root {}`.

### `src/styles/global.css`
Import de `tokens.css` + reset minimal + classes utilitaires Nexellia.

### `src/content/config.ts`
```ts
import { defineCollection, z } from 'astro:content';

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string().max(160),
    pubDate: z.date(),
    pilier: z.enum(['prompting', 'conception', 'qualiopi', 'animation', 'vente', 'roi']),
    keywords: z.array(z.string()),
    featured: z.boolean().default(false),
    draft: z.boolean().default(false),
    leadMagnet: z.boolean().default(false),
  }),
});

export const collections = { blog };
```

## Critères de validation
- [ ] `npm run dev` démarre sans erreur
- [ ] `npm run build` produit un dossier `dist/` sans erreur
- [ ] Les tokens CSS sont correctement importés
- [ ] TypeScript ne signale aucune erreur critique

## Une fois validé
Mettre `[x]` sur le Lot 01 dans `_docs/ROADMAP.md` et ajouter une entrée dans `_docs/CHANGELOG.md`.
