# Projet 3 - Modèle LBO (Leveraged Buy-Out / Private Equity)

## Project overview

Modèle LBO (Leveraged Buy-Out) illustratif et pédagogique, construit sur **Fnac Darty (Euronext Paris : FNAC)** comme cible hypothétique de rachat par effet de levier. **Il ne s'agit pas d'une opération réelle ni annoncée** : Fnac Darty a été choisie comme cible d'entraînement parce qu'elle est une entreprise réelle, cotée, avec des fondamentaux publics, un profil pratique pour démontrer la mécanique financière complète d'une opération à effet de levier (sources & emplois, échéancier de dette, cash sweep, pont de création de valeur), y compris dans un cas particulier et pédagogiquement utile : une cible dont la trésorerie dépasse la dette brute à l'entrée.

## Objectives

- Construire la mécanique complète d'un LBO : sources & emplois de financement, structuration de la dette senior, échéancier de remboursement avec cash sweep, hypothèses de sortie.
- Calculer le rendement du sponsor (MOIC et IRR) et en décomposer les moteurs via un pont de création de valeur (croissance de l'EBITDA / variation de multiple / désendettement / frais de transaction), vérifié pour se réconcilier exactement avec l'écart de valeur des fonds propres entrée-sortie.
- Traiter correctement un cas particulier : Fnac Darty est en position de **trésorerie nette positive** à l'entrée (958 M€ de dette brute contre 1 104 M€ de trésorerie réelle), ce qui change la mécanique des sources & emplois par rapport à un LBO sur une cible endettée.
- Vérifier la cohérence interne du modèle par un onglet de contrôles (y compris l'égalité stricte entre total des sources et total des emplois).

## Methodology

1. **Prix d'entrée** : prime d'offre de 20 % appliquée au cours de marché réel (34,40 EUR), prix d'offre implicite de 41,28 EUR/action, prix d'acquisition des fonds propres (Equity Purchase Price) de 1 212,4 M€ sur 29,37 M actions réelles en circulation.
2. **Données d'exploitation** : EBITDA d'entrée (554,2 M€) dérivé de l'EBIT réel publié (203 M€) et d'une D&A estimée à 3,4 % du chiffre d'affaires (hypothèse personnelle, cohérente avec le projet 4, Transaction Services DD).
3. **Dette existante et trésorerie (réelles, FY2025, hors IFRS16)** : 958 M€ de dette financière brute et 1 104 M€ de trésorerie, soit une **position de trésorerie nette de -146 M€** (Fnac Darty est en cash net, pas en dette nette).
4. **Sources & emplois** : les emplois (refinancement de la dette brute existante + prix d'acquisition des fonds propres + frais de transaction à 2 %) totalisent 2 213,8 M€. Côté sources : une trésorerie plancher de 206,6 M€ (2 % du CA) est conservée au bilan de la newco et n'est donc pas disponible pour financer la transaction ; le solde de la trésorerie existante (897,4 M€) finance une large part du besoin, ramenant le besoin de financement externe à 1 316,4 M€. La valeur d'entreprise d'entrée (prix des fonds propres + dette nette négative) ressort à 1 066,4 M€, soit un multiple d'entrée implicite de 1,9x l'EBITDA : un multiple mécaniquement bas car la trésorerie nette positive de la cible est déjà incluse dans le prix des fonds propres payé.
5. **Dette senior et apport du sponsor** : un levier senior de 1,7x l'EBITDA d'entrée (volontairement réduit par rapport à un LBO classique sur cible endettée, car la structure part déjà d'une position de cash net) donne une dette senior de 942,2 M€ ; l'apport en fonds propres du sponsor (374,2 M€, 28,4 % du besoin de financement externe) vient en solde (plug) pour équilibrer exactement sources et emplois.
6. **Plan d'affaires sur 5 ans** : croissance de l'EBITDA (3 %/an) et du chiffre d'affaires (2 %/an), capex (2,5 % du CA), variation du BFR (4 % de la variation du CA), taux d'IS de 25 %.
7. **Échéancier de dette (cash sweep)** : cascade complète EBITDA -> D&A -> EBIT -> intérêts (sur la dette d'ouverture) -> résultat avant impôt -> impôt (MAX(EBT,0) x taux d'IS) -> capex -> variation de BFR -> FCF disponible ; le remboursement de la dette senior est plafonné au minimum entre le FCF disponible et le solde de dette restant (`MIN(MAX(FCF,0), dette_début)`). La dette senior est intégralement remboursée dès l'année 4 ; le FCF excédentaire des années suivantes s'accumule en trésorerie plutôt que de disparaître du modèle. La cascade détaille également la part d'amortissement obligatoire et la part de cash sweep optionnel, ainsi qu'un ratio de couverture des intérêts, et deux covenants hypothétiques (levier senior maximal, couverture des intérêts minimale) sont suivis en continu dans l'onglet Checks.
8. **Sortie à 5 ans** : valeur d'entreprise de sortie au même multiple qu'à l'entrée (hypothèse prudente, aucune réévaluation de marché supposée), + trésorerie plancher conservée + trésorerie excédentaire accumulée - dette senior restante (nulle à ce stade) = valeur des fonds propres à la sortie.
9. **Calcul du rendement** : MOIC = valeur des fonds propres à la sortie / apport initial ; IRR = MOIC^(1/durée) - 1.
10. **Pont de création de valeur** : décomposition du gain total en quatre contributions (croissance de l'EBITDA à multiple constant, variation de multiple, désendettement net, y compris la trésorerie plancher et la trésorerie excédentaire accumulée des deux côtés du pont, et frais de transaction détruits à la clôture), recoupée pour s'additionner exactement à l'écart (valeur des fonds propres à la sortie - apport initial).
11. **Grille de sensibilité IRR** (prime d'offre x multiple de sortie, construction analogue au guide BIWS LBO Model, page 19) : la dette senior et son calendrier de remboursement ne dépendent ni de la prime payée ni du multiple de sortie dans ce modèle, ce qui permet un calcul direct par formule pour chaque scénario ; la cellule centrale (prime 20 %, multiple de sortie égal au multiple d'entrée) sert de contrôle de cohérence avec le scénario central.
12. **Onglet de contrôles** : égalité totale des sources = totale des emplois, réconciliation du pont de création de valeur, dette jamais négative, apport en fonds propres positif, cash-flow disponible positif chaque année, respect des deux covenants hypothétiques, cohérence interne MOIC/IRR.

## Key findings

- **MOIC de 4,97x et IRR de 37,8 %** sur un horizon de détention de 5 ans, dans un scénario où le multiple de sortie est strictement égal au multiple d'entrée (aucun pari sur la revalorisation de marché).
- Le pont de création de valeur (1 487,2 M€, qui se réconcilie exactement avec l'écart valeur des fonds propres sortie - entrée) montre que l'essentiel du rendement provient du désendettement (1 360,7 M€, porté par le remboursement intégral de la dette senior dès l'année 4 puis l'accumulation de trésorerie), la croissance de l'EBITDA à multiple constant contribuant pour 169,8 M€ et les frais de transaction détruisant 43,4 M€ à la clôture : aucune expansion de multiple n'est supposée.
- Le MOIC élevé s'explique en partie par un apport en fonds propres du sponsor mécaniquement faible (28,4 % du besoin de financement externe, 16,9 % du total des emplois) : la trésorerie excédentaire de la cible finance une large part de la transaction, ce qui amplifie le multiple de rendement pour un même montant de création de valeur en euros, un point de vigilance signalé dans le modèle (onglet Returns), pas une erreur de calcul.
- La grille de sensibilité IRR (prime d'offre de 0 % à 40 %, multiple de sortie de 1,52x à 2,32x) fait ressortir un IRR allant de **22,6 % à 66,0 %** autour du scénario central (37,8 %), ce qui situe l'ampleur de la sensibilité du rendement à ces deux paramètres clés.

## Files included

- `LBO_Model.xlsx` - modèle complet (Cover avec avertissement explicite, Assumptions, Debt Schedule, Returns, Checks)
- `data/historical_financials.csv` - données de marché et comptables réelles utilisées comme point d'ancrage
- `data/assumptions.csv` - hypothèses de structuration et de plan d'affaires, toutes signalées comme des choix de l'auteur
- `screenshots/` - captures d'écran des principaux onglets
- `sources.md` - sources des données d'ancrage réelles

## Limitations

- **Ceci n'est pas une opération réelle.** Fnac Darty n'a fait l'objet d'aucune offre de rachat par effet de levier à la connaissance de l'auteur ; le choix de cette société est un choix pédagogique (entreprise réelle, cotée, données publiques disponibles), pas une thèse d'investissement.
- La prime de rachat, le niveau de levier senior, le multiple de sortie et l'ensemble des hypothèses de plan d'affaires sont des estimations personnelles sans lien avec une transaction réelle ou annoncée.
- L'EBITDA d'entrée est dérivé d'une estimation de dotation aux amortissements (non publiée à cette maille, cohérente avec le projet 4), et non d'un chiffre EBITDA publié directement par l'entreprise.
- Le MOIC élevé reflète en partie un effet mécanique (apport en fonds propres faible du fait de la trésorerie nette de la cible) plutôt qu'une création de valeur opérationnelle hors norme ; voir Key findings.
- Le modèle ne couvre pas de scénario de stress (sous-performance du plan d'affaires, hausse des taux d'intérêt) au-delà du scénario central.

## Sources

Voir `sources.md`.
