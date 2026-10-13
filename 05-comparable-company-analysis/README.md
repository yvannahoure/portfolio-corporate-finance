# Projet 5 - Analyse de Comparables Boursiers & M&A

## Project overview

Ce projet combine deux volets. Le premier est une **analyse de comparables boursiers (trading comps)** qui consolide, sur un seul classeur, les groupes de pairs cotés mobilisés dans les DCF du portfolio (Danone, Sonatel, Tesla) et en dérive une **fourchette de valorisation** pour Danone en appliquant les multiples VE/EBITDA de ses pairs (Nestlé, Unilever, General Mills) à son propre EBITDA. Le second volet est un **mandat de screening M&A réel** : le test technique de recrutement réalisé pour Collaboration Capital (boutique de conseil M&A), qui identifie une cible d'acquisition pour Evian (groupe Danone) dans l'alimentation infantile biologique, restitué sous forme d'un support de présentation de 12 slides.

## Objectives

- Construire une analyse de comparables boursiers multi-secteurs (agroalimentaire, télécoms, valeur de croissance), en distinguant clairement les multiples calculés par l'auteur des multiples sourcés directement.
- Dériver une fourchette de valorisation par comparables pour Danone et la confronter à la valeur issue du DCF (projet 1) et au cours de marché réel.
- Restituer un vrai mandat de screening M&A (méthodologie en 5 étapes, short-list de cibles, cible retenue, rationale stratégique) sous une forme professionnelle et présentable en entretien.

## Methodology

**Volet comparables boursiers :**
1. Consolidation des multiples VE/EBITDA et P/E par secteur (agroalimentaire/staples, télécoms Afrique/Maghreb, valeur de croissance US), avec la source de chaque chiffre.
2. Calcul d'une fourchette de valorisation pour Danone : application des multiples VE/EBITDA de 3 pairs cotés (Nestlé 14,1x, Unilever 12,7x, General Mills 9,25x) à l'EBITDA propre de Danone, déduction de la dette nette, division par le nombre d'actions, pour obtenir une valeur par action implicite selon chaque comparable.
3. Ajout d'un **multiple médian des pairs cotés** (12,7x), à côté de la moyenne du groupe, car la médiane est moins sensible à une valeur isolée dans un petit échantillon (Vernimmen, chapitre 32, section 3.7) ; une note méthodologique rappelle aussi que ces multiples sont des multiples de marché (participations minoritaires) et n'intègrent pas de prime de contrôle, laquelle s'observe en moyenne autour de 25 % dans les acquisitions de sociétés cotées (Vernimmen, chapitre 32, section 3.6).
4. Synthèse de la fourchette ainsi obtenue avec la valeur issue du DCF (projet 1, scénario central) et le cours de marché actuel, pour une lecture croisée des quatre points de référence (3 comparables + médiane) face au DCF et au marché.

**Volet M&A (mandat Evian) :**
1. Définition des critères de cible (Europe, alimentation infantile bio/sans sucre ajouté, 1 à 300 M EUR de chiffre d'affaires, 0-14 ans).
2. Screening documentaire (registres officiels, presse spécialisée) pour constituer une short-list de 5 cibles.
3. Segmentation du marché (baby food bio vs conventionnel) pour affiner le choix du sous-segment.
4. Analyse de la cible retenue (Smileat) : positionnement, part de marché, rationale de synergies avec Evian/Danone (produit, distribution, image santé, innovation R&D).
5. Proposition d'un axe de croissance alternatif (nutrition fonctionnelle adultes actifs), appuyé sur des précédents réels d'acquisition par Danone (Huel, MADE Group).

## Key findings

- La fourchette de valorisation par comparables pour Danone s'étend de **45,80 EUR/action (General Mills, borne basse)** à une valeur DCF centrale de **87,41 EUR/action (borne haute)**, le cours de marché actuel (59,50 EUR) se situant dans le bas de cette fourchette, et le multiple médian des pairs cotés (67,50 EUR/action) au centre de cette même fourchette : une lecture convergente avec le DCF du projet 1, sans constituer une recommandation d'investissement.
- La lecture croisée multiple de marché / multiple de DCF diffère selon le contexte : pour Danone, le DCF se rapproche des pairs cotés alors que le marché price en dessous (lecture favorable) ; pour Tesla, l'écart est inverse et massif (le marché price une optionalité hors flux actuels) ; pour Sonatel, le comparable coté valide la lecture de marché plutôt que celle du DCF.
- Sur le mandat Evian : **Smileat** (Espagne, 21 M EUR de chiffre d'affaires 2025, +26 % de croissance, leader bio indépendant, 49 % de part de marché sur le baby food bio espagnol) est la cible prioritaire retenue, avec Yooji et Popote en options de repli. Un axe de croissance alternatif (nutrition fonctionnelle) est proposé, appuyé sur les précédents réels Huel et MADE Group.

## Files included

- `Trading_Comps.xlsx` - modèle complet (Cover, Trading Comps, Valuation Range)
- `MA_Presentation.pptx` - support de présentation du mandat Evian (12 slides)
- `MA_Presentation.pdf` - version PDF du même support
- `data/historical_financials.csv` - multiples de comparables et données des cibles M&A
- `data/assumptions.csv` - hypothèses utilisées dans le calcul de la fourchette de valorisation
- `screenshots/` - captures d'écran des principaux onglets du classeur
- `sources.md` - sources complètes

## Limitations

- Le mandat M&A sur Evian est une **recherche fictive réalisée dans le cadre d'un test technique de recrutement pour Collaboration Capital** : elle ne reflète aucune stratégie réelle d'Evian ou de Danone, et ne doit pas être lue comme une recommandation d'acquisition réelle.
- La fourchette de valorisation par comparables applique des multiples de pairs à l'EBITDA de Danone sans ajustement de taille, de croissance ou de profil de risque relatif : une simplification assumée à but pédagogique.
- La comparaison des multiples entre Danone, Sonatel et Tesla (volet "lecture transversale") met en regard des secteurs et des profils de risque très différents ; elle est présentée comme un exercice de lecture croisée, pas comme une équivalence de valorisation.

## Sources

Voir `sources.md`.
