# Projet 2 - Modèle intégré 3 états + DCF (Fnac Darty)

## Project overview

Modèle financier intégré construit comme exercice d'entraînement sur **Fnac Darty (Euronext Paris : FNAC)**, couvrant la chaîne complète : 3 exercices réels de compte de résultat (FY2023A-FY2025A), des schedules dédiées (fonds de roulement, immobilisations/amortissements, dette avec remboursement programmé et sweep de trésorerie excédentaire), les 3 états financiers connectés par formules (bilan, compte de résultat, tableau de flux), un DCF alimenté directement par les projections du modèle (WACC par CAPM, FCFF, valeur d'entreprise), une grille de sensibilité WACC x croissance terminale, et un dashboard de graphiques de synthèse. 12 onglets au total. L'objectif de cette version est d'aller au-delà d'un modèle 3 états isolé : montrer la chaîne historique réel -> modèle -> valorisation, comme le ferait un modèle de formation professionnel (type CFI), mais construit de façon originale plutôt que reproduit d'un template existant.

## Objectives

- Ancrer le modèle sur des données réelles (chiffre d'affaires, EBIT, résultat net sur 3 exercices ; trésorerie, dette financière brute, EBITDA, cours de bourse, bêta, coupon obligataire en FY2025A) plutôt que sur un cas 100 % fictif.
- Construire des schedules dédiées (fonds de roulement, immobilisations, dette) séparées des 3 états, à l'image des modèles professionnels, plutôt que de tout calculer en ligne dans le bilan.
- Concevoir un échéancier de dette et un calcul d'intérêts non circulaires (sweep basé sur la trésorerie de clôture de l'exercice précédent, intérêts sur la dette d'ouverture) sans recourir au calcul itératif d'Excel.
- Alimenter un DCF directement depuis les projections du modèle (pas un DCF isolé), avec un WACC calculé par CAPM à partir de données de marché réelles.
- Construire une grille de sensibilité par formules vivantes (SUMPRODUCT), robuste à l'export/au recalcul, plutôt qu'une Data Table Excel native.
- Garantir l'équilibre comptable du bilan à chaque période et documenter honnêtement les écarts de valorisation plutôt que de les dissimuler.

## Methodology

1. **Compte de résultat (3 exercices réels + 5 ans de projection)** : chiffre d'affaires, EBIT et résultat net FY2023A-FY2025A sont des chiffres publiés par Fnac Darty. Point de vigilance documenté explicitement : Fnac Darty a acquis Unieuro (Italie) en novembre 2024, donc la hausse FY2024A -> FY2025A (8 253 -> 10 330 M€) reflète en grande partie un changement de périmètre, pas une croissance organique comparable.
2. **Bilan d'ouverture FY2025A** : seuls le total actif (8 543 M€), le total capitaux propres (1 576 M€), la trésorerie (1 104 M€) et la dette financière brute (958 M€) sont des ancres réelles publiées. Les 4 autres postes d'actif et les 3 autres postes de passif sont une reconstruction personnelle, répartie proportionnellement à une structure de bilan retail plausible, calée pour respecter exactement les totaux réels.
3. **Working Capital Schedule** : créances, stocks et dettes fournisseurs projetés par des délais en jours de chiffre d'affaires, dérivés du bilan d'ouverture reconstitué.
4. **PP&E Schedule** : rollforward des immobilisations (valeur d'ouverture + capex - D&A), avec un point de vigilance documenté : le D&A (4,49 % du CA, cohérent avec le réel FY2025A qui inclut l'amortissement des droits d'usage IFRS16) dépasse le capex (2,5 % du CA) sur l'horizon explicite - un écart court terme légitime, mais neutralisé dans la valeur terminale du DCF (voir point 6) pour ne pas le prolonger indéfiniment.
5. **Debt Schedule** : amortissement programmé (100 M€/an) + mécanisme de sweep de trésorerie excédentaire (50 % de l'excédent au-delà d'un seuil de 400 M€), non circulaire par construction : le sweep se base sur la trésorerie de clôture de l'exercice **précédent**, et les intérêts se calculent sur la dette d'**ouverture** de période.
6. **DCF** : FCFF non levier (EBIT après impôt + D&A - capex +/- variation de BFR), actualisé au WACC (CAPM : bêta réel 1,07, taux sans risque réel 4,91 % - OAT France 10 ans, prime de risque 5,0 %). La valeur terminale (Gordon-Shapiro, croissance terminale 1,5 %) utilise un **FCFF terminal normalisé** (capex = D&A en régime stationnaire) plutôt que le FCFF brut de la 5e année : reconduire indéfiniment l'écart D&A/capex lié à l'IFRS16 dans une rente perpétuelle n'est pas une hypothèse de régime stationnaire défendable, alors que les 5 années explicites, elles, conservent l'écart réel. Pont vers la valeur des capitaux propres via la dette nette **y compris les dettes locatives IFRS16** (convention retenue car l'EBITDA réel inclut déjà le D&A des droits d'usage - voir note méthodologique dans Assumptions). Les délais de BFR (Working Capital Schedule) sont des formules vivantes ancrées sur le bilan d'ouverture reconstitué, plutôt que des hypothèses saisies en dur, pour éviter un à-coup artificiel de BFR en première année de projection.
7. **Sensitivity** : grille WACC x croissance terminale (5x5), chaque cellule recalculant indépendamment la valeur d'entreprise par SUMPRODUCT (même logique de FCFF terminal normalisé que le DCF) - vérifiée pour retomber exactement sur la valeur centrale du DCF.
8. **Dashboard** : 3 graphiques (chiffre d'affaires + marges en axe secondaire, flux de trésorerie par nature, valeur par action DCF vs cours de marché réel).
9. **Checks** : 12 contrôles de cohérence (équilibre du bilan sur toutes les périodes, positivité de la trésorerie/dette/capitaux propres/immobilisations, cohérence sweep/dette, validité du Gordon-Shapiro, cohérence grille de sensibilité/DCF, cohérence BFR bilan/schedule).

## Key findings

- Le modèle atteint un **équilibre bilanciel exact (écart nul)** sur le bilan d'ouverture et les 5 années de projection, et les 12 contrôles de l'onglet Checks passent tous "OK".
- Le DCF ressort à une **valeur par action implicite de 24,21 €**, contre un cours de marché réel de 34,40 € (12/10/2026) - un écart de **-29,6 %**. Le multiple VE/EBITDA implicite du DCF (5,55x) est proche du multiple réel y compris IFRS16 (6,00x) - une lecture cohérente entre DCF et marché, permise par la normalisation du FCFF terminal décrite en Methodology (point 6).
- Fnac Darty est en position de **cash net** hors IFRS16 à fin FY2025A (958 M€ de dette financière brute - 1 104 M€ de trésorerie = -146 M€), cohérent avec la lecture retenue dans le projet 4 (Transaction Services DD).
- Les délais de BFR (Working Capital Schedule) sont des formules vivantes ancrées sur le bilan d'ouverture reconstitué (=solde / CA x 365), ce qui évite tout à-coup artificiel de BFR en première année de projection.

## Files included

- `Three_Statement_Model.xlsx` - modèle complet (12 onglets : Cover, Assumptions, Working Capital Schedule, PP&E Schedule, Debt Schedule, Income Statement, Balance Sheet, Cash Flow, DCF, Sensitivity, Dashboard, Checks)
- `data/historical_financials.csv` - chiffres réels publiés (compte de résultat 3 ans, bilan FY2025A, données de marché) et détail de la reconstruction personnelle du bilan d'ouverture
- `data/assumptions.csv` - hypothèses de projection, de dette et de valorisation (WACC, croissance terminale)
- `screenshots/` - captures d'écran des 12 onglets (14 images, certains onglets s'étalant sur 2 pages)
- `sources.md` - sources des données réelles

## Limitations

- La répartition détaillée du bilan d'ouverture (créances, stocks, immobilisations, goodwill, dettes fournisseurs, dettes locatives, autres passifs) **n'est pas une donnée publique à ce niveau de détail** : c'est une reconstruction personnelle calée sur les totaux réels et sur les deux ancres réelles (trésorerie, dette financière brute). Seuls le total actif, le total capitaux propres, la trésorerie et la dette financière brute sont des chiffres réels à ce niveau de granularité.
- La dette réelle de Fnac Darty est une obligation senior unique de 300 M€ remboursable in fine en avril 2032 (coupon fixe 4,75 %) ; le modèle simplifie volontairement en un amortissement linéaire hypothétique + un mécanisme de sweep, pour illustrer la mécanique d'un échéancier de dette plutôt que pour prévoir le remboursement réel de cette obligation.
- Les hypothèses de projection 2026-2030 (croissance, marges, délais de BFR, capex, seuil de trésorerie, taux de sweep, prime de risque, croissance terminale) sont des estimations personnelles, non des prévisions officielles de l'entreprise.
- L'écart résiduel (-29,6 %) entre la valeur par action implicite du DCF et le cours de marché réel est documenté plutôt que corrigé artificiellement pour se rapprocher du marché ; il reste à l'intérieur d'un ordre de grandeur raisonnable une fois la valeur terminale normalisée (voir Key findings).
- Exercice d'entraînement à but pédagogique - ne constitue ni une prévision officielle ni une recommandation d'investissement sur Fnac Darty.

## Sources

Voir `sources.md`.
