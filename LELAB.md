# LELAB.md — La Cuisine de Gagny

Mémoire projet pour les sessions Claude Code. Mise à jour après chaque phase.

## Le client
- **La Cuisine de Gagny** — bistrot-traiteur sénégalais/malien
- 153 boulevard Chave, 13005 Marseille 5e — Tél : 06 59 05 86 19
- Chef : Gagny Sissoko (né à Kati, parcours Bamako → théâtre → Marseille)
- Cuisine bio / locale / fait-maison, **midi uniquement**, Lun-Ven 11h45-14h30
- Épicerie fine & traiteur en extension au 155 bd Chave
- Labels Ecotable + Éco-défis Or
- Facebook : https://www.facebook.com/LaCuisinedeGagny/
- Domaine cible : lacuisinedegagny.com
- Citation signature : « Ma cuisine est une cuisine de rencontres et de mélanges »

## Architecture technique
- **Single-file** `index.html` — tout embarqué en base64 (fonts, images, motifs)
- Déploiement Netlify (publish `.`, aucun build)
- Pas de CMS pour l'instant (carte hard-codée) — évolution possible vers pattern LeLab
  (sassy-cms-loader.js + netlify/functions/save-data.js) si Gagny veut éditer sa carte

## Direction artistique (VALIDÉE)
### Palette
- Crème fond : `#FAF3E8` · Crème2 : `#F0E6D6`
- Noir : `#16110D`
- Rouge : `#E61920` · Orange : `#F36A21` · Jaune : `#F5A623`
- Vert : `#5BB535` · Vert cercle motif : `#00A86B` · Rose (motif) : `#E89BA8`

### Typographies (toutes base64)
- **Cormorant Garamond Light** — tous les titres, en CAPITALES (sauf noms de plats en bas de casse)
- **Avenir Light** (Avenir.ttc index 6) — tout le texte courant
- **Avenir Medium** (index 8) — strong, labels
- **Avenir Next Condensed Bold** — logo header "LA CUISINE DE GAGNY"
- **Avenir Next Condensed UltraLight** — CTA, petits labels espacés
- DAMN : ABANDONNÉE (remplacée par Cormorant partout)

### Motif kente
- Bandes latérales gauche/droite dans le hero, PNG nettoyés (dithering supprimé, aplats nets)
- Bande gauche : cercle VERT · bande droite : cercle jaune + carré crème
- `object-fit: cover` (pas fill — sinon étirement vertical)
- Léger flottement vertical continu (img surdimensionnée 108% pour éviter les coupes)

## Structure des sections (toutes full-screen 100vh)
1. **Hero** — motif kente latéral + centre crème + titre "BIO. LOCAL. MAISON." (Cormorant caps, vert/orange/jaune) + baseline + cercle scroll tournant qui mord sur la section suivante
2. **Histoire** (fond rouge) — photo Gagny détourée collée en bas gauche ; titre "DE BAMAKO À CHAVE" décalé à 50%, texte+CTA à 62% ; CTA → article Jeune Afrique
3. **Citation** (fond crème) — "Ma cuisine est une cuisine de rencontres & de mélanges" (rencontres=orange, de mélanges=vert)
4. **Carte** (fond orange, typo crème) — 3 colonnes Mer/Terre/Végé ; mobile = carrousel ; noms de plats Cormorant bas de casse ; hover = thumbnail photo
5. **Galerie** (fond crème) — 3 photos + marquee "FAIT MAISON" rouge qui défile en auto et mord entre les sections
6. **Épicerie** (fond crème) — "ÉPICERIE FINE & TRAITEUR" (traiteur orange) + photo Gagny & Julie en cadre fin ; légende sobre
7. **Réserve** (fond rouge) — "ALORS, ON RÉSERVE ?" + CTA jaune
8. **Infos** (fond crème) — 3 colonnes Horaires/Contact/Adresse avec pictos line + Google Map (filtre charte) en dessous
9. **Footer** (fond noir) — logo Avenir Cond Bold

## Animations (2026)
- Stagger reveal (éléments montent en cascade à l'entrée de section, IntersectionObserver)
- Intro hero (bandes se déploient + mots BIO/LOCAL/MAISON en séquence)
- Curseur personnalisé (point rouge + anneau, grossit au survol) — desktop only
- Marquee "FAIT MAISON" défilement auto CSS
- Flottement kente léger
- Plat hover → thumbnail
- **PAS de scroll fluide JS** (testé, buggait — retiré, scroll natif conservé)
- **PAS de parallaxe sur éléments collés au bord** (créait des coupes — retiré)

## Backlog / idées futures
- CMS pour que Gagny édite sa carte (pattern LeLab+)
- Photos additionnelles galerie
- Version anglaise éventuelle
