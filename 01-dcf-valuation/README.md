# Projet 1 - Valorisation DCF (Discounted Cash Flow)

## Project overview

Ce projet construit une valorisation DCF (Discounted Cash Flow) complète et documentée sur une entreprise cotée française, **Danone (Euronext Paris : BN)**, choisie comme étude de cas principale. Deux DCF secondaires, sur **Sonatel** (BRVM : SNTS, opérateur télécom ouest-africain) et **Tesla** (NASDAQ : TSLA, valeur de croissance américaine), complètent l'exercice pour montrer la méthode appliquée à des profils d'entreprise très différents (groupe mature de consommation, télécom émergent, valeur de croissance).

Toutes les données historiques (chiffre d'affaires, marges, dette, cours de bourse) proviennent de publications réelles et sourcées. Les hypothèses de projection (croissance future, WACC, prime de risque, croissance terminale) sont des estimations personnelles, systématiquement distinguées des données sourcées et documentées dans le modèle.

## Objectives

- Construire un DCF à deux étages (flux explicites + valeur terminale) méthodologiquement rigoureux, avec un WACC calculé par la méthode CAPM (coût des fonds propres + coût de la dette après impôt, pondéré par la structure de capital).
- Confronter la valeur implicite du DCF au cours de marché réel, et expliquer l'écart plutôt que de forcer les hypothèses pour "recoller" au marché.
- Montrer la sensibilité du résultat aux deux paramètres les plus structurants (WACC et croissance terminale) via une grille de sensibilité.
- Appliquer la même méthodologie à trois profils d'entreprise contrastés pour démontrer la portabilité de l'approche.

## Methodology

1. **Collecte des données historiques** : chiffre d'affaires, résultat opérationnel courant / EBITDA, free cash-flow, dette financière nette, cours de bourse et capitalisation, à partir des communiqués de résultats et de sources de marché (voir `sources.md`).
2. **Construction du WACC (CAPM)** : coût des fonds propres = taux sans risque + bêta x prime de risque actions ; coût de la dette après impôt = coût de la dette brut x (1 - taux d'IS) ; pondération par la structure cible E/V et D/V.
3. **Projection des flux de trésorerie disponibles (FCF)** sur un horizon explicite de 5 ans, avec hypothèses de croissance du chiffre d'affaires et de marge documentées séparément des données historiques.
4. **Valeur terminale** par la méthode de Gordon-Shapiro (croissance terminale perpétuelle), actualisée au WACC.
5. **Passage de la valeur d'entreprise à la valeur des fonds propres** (déduction de la dette nette), puis à la valeur par action (division par le nombre d'actions).
6. **Grille de sensibilité** (WACC x croissance terminale) construite par formules `SUMPRODUCT` pour éviter toute valeur en dur.
7. **Onglet de contrôles** : vérification automatique que la croissance terminale est inférieure au WACC, que les marges de FCF restent positives sur toute la période, que la valeur d'entreprise se réconcilie bien entre les différentes méthodes de calcul, et que le nombre d'actions implicite (capitalisation / cours) est cohérent.

## Key findings

**Danone (projet principal)** : valeur implicite par action de **87,41 EUR** contre un cours de marché de **59,50 EUR**, soit un écart de **+46,9 %**. Le multiple VE/EBITDA implicite du DCF (15,87x) se situe dans la fourchette des comparables cotés (Nestlé 14,1x, Unilever 12,7x), alors que le marché price Danone en dessous (11,43x implicite) : une lecture cohérente avec une sous-valorisation relative plutôt qu'une anomalie de modèle. Un recoupement par multiple de sortie (cf. guide BIWS) confirme cette lecture : la valeur terminale du DCF implique un multiple de sortie de 14,7x, proche du multiple médian des comparables (12,7x).

**Sonatel (secondaire)** : la dette nette de Sonatel n'étant pas publiée à une maille fiable, le modèle retient une lecture **indicative de la valeur d'entreprise uniquement** (6 327,8 Md FCFA), sans pont vers une valeur des fonds propres ni conclusion de potentiel de hausse ou de baisse. Le multiple VE/EBITDAaL implicite du DCF (6,9x) est supérieur au multiple implicite de marché (4,9x) et au comparable coté Maroc Telecom (4,9x) : un écart présenté comme une lecture croisée, pas comme une recommandation. Le recoupement par multiple de sortie sur l'EBITDAaL implicite de l'année 5 (5,9x) reste également proche de ce comparable régional.

**Tesla (secondaire)** : valeur implicite de **45,28 USD/action** contre un cours de marché de **379,26 USD**, soit un écart de **-88,1 %**. Ce DCF sur les seuls flux actuels ne capture pas les paris du marché sur des relais de croissance non encore dans les comptes (robotaxi/FSD, Optimus, stockage d'énergie) : l'écart est présenté comme un constat méthodologique, pas une erreur de calcul.

## Files included

- `Danone_DCF_Model.xlsx` - modèle complet (Cover, Dashboard avec graphique intégré, Assumptions, Financials, DCF, Sensitivity, Checks)
- `Sonatel_DCF_Model.xlsx` - modèle complet (Cover, Assumptions, DCF, Sensitivity, Comps, Checks)
- `Tesla_DCF_Model.xlsx` - modèle complet (Cover, Assumptions, DCF, Sensitivity, Market Gap, Checks)
- `data/historical_financials.csv` - données historiques sourcées pour les 3 entreprises
- `data/assumptions.csv` - hypothèses de projection, avec leur base/justification
- `screenshots/` - captures d'écran des principaux onglets de chaque modèle
- `sources.md` - liste complète des sources utilisées

## Limitations

- Les hypothèses de croissance au-delà de l'année de consensus, la prime de risque actions et la croissance terminale sont des estimations personnelles, non des prévisions officielles de l'entreprise ou d'un analyste.
- Le DCF Sonatel simplifie le free cash-flow en proxy du FCFF et ne déduit pas la dette nette, faute de donnée consolidée publique à cette maille ; en conséquence, seule une valeur d'entreprise indicative est retenue, sans valeur par action ni conclusion de potentiel de hausse ou de baisse.
- La dette financière nette de Danone est le point médian d'une fourchette sourcée (8 059 - 8 547 M EUR) en raison d'une légère divergence entre les sources disponibles ; cette divergence est explicitement signalée dans le modèle plutôt que lissée.
- Le bêta Danone retenu (0,56) a été préféré à un chiffre de bêta brut outlier (0,20) trouvé sur une autre source ; cet arbitrage est documenté dans le modèle.
- Ces projets sont des études de cas construites à partir de données publiques à des fins de démonstration méthodologique. Ils ne constituent pas une recommandation d'investissement.

## Sources

Voir `sources.md` pour la liste complète et horodatée des sources (communiqués de résultats, SEC EDGAR, BRVM, marketscreener.com, stockanalysis.com, etc.).
