# Projet 6 - Business Plan & Pitch Deck (construction d'un plan d'affaires fintech)

## Project overview

Construction complète d'un plan d'affaires sur 5 ans et d'un pitch deck de levée de fonds seed pour **KobaPay**, une startup fictive de paiement mobile et d'épargne de groupe digitalisée dans l'UEMOA. **KobaPay n'est pas une entreprise réelle** : elle a été inventée pour cet exercice afin de démontrer, de bout en bout, la construction d'un modèle financier de startup (hypothèses -> compte de résultat -> trésorerie -> cap table) et sa traduction en un support de présentation destiné à des investisseurs. Le contexte de marché (taux d'inclusion financière, taille du marché du mobile money) est en revanche réel et sourcé - voir `sources.md`.

## Objectives

- Construire un modèle financier de startup sur 5 ans (2027F-2031F) entièrement piloté par des hypothèses modifiables : acquisition d'utilisateurs, trois moteurs de revenu activés progressivement (transactionnel, épargne de groupe, micro-crédit), structure de coûts, trésorerie et financement.
- Modéliser une levée de fonds seed réaliste : montant levé, valorisation pre/post-money, table de capitalisation, pool ESOP, et un tableau d'utilisation des fonds qui se réconcilie avec le montant levé.
- Vérifier la cohérence interne du modèle par un onglet de contrôles dédié (tie-outs entre onglets, sommes de pourcentages, trésorerie jamais négative).
- Traduire le modèle financier et le contexte de marché en un pitch deck structuré (problème, solution, marché, modèle économique, trajectoire financière, positionnement concurrentiel, feuille de route, équipe, demande de financement), construit sur un thème graphique cohérent et des graphiques natifs.

## Methodology

1. **Acquisition d'utilisateurs** : 25 000 utilisateurs actifs en année 1 (2027F), puis une croissance qui décélère progressivement (260 % / 145 % / 70 % / 45 % sur les années 2 à 5) à mesure que la base mûrit - hypothèses de l'auteur, propres à KobaPay.
2. **Trois moteurs de revenu, activés progressivement** : revenu transactionnel (commission de 1,3 % sur le volume de paiements, dès l'année 1), épargne de groupe digitalisée (frais de gestion de 1,5 % sur l'encours géré, dès l'année 1), micro-crédit (marge nette d'intérêt de 9 %, activé seulement à partir de l'année 3 - une fois qu'un historique d'épargne est disponible pour limiter le risque de crédit à l'amorçage).
3. **Structure de coûts** : coût d'acquisition client dégressif (2 500 FCFA par nouvel utilisateur en année 1, -8 %/an), coûts techniques et d'hébergement (12 % du chiffre d'affaires), masse salariale, frais généraux et coûts de conformité renseignés année par année, amortissement des investissements sur 3 ans.
4. **Trésorerie et financement** : apport initial des fondateurs (50 000 €) en année 1, levée de fonds seed (550 000 €) également en année 1, variation du besoin en fonds de roulement (3 % de la variation du chiffre d'affaires), rémunération de la trésorerie excédentaire (3 %).
5. **Levée de fonds et cap table** : valorisation pre-money de 2 450 000 €, valorisation post-money de 3 000 000 €, pool ESOP de 10 % créé à la levée, répartition du capital entre fondateurs / investisseurs seed / pool ESOP totalisant 100 %.
6. **Utilisation des fonds** : répartition de la levée entre produit et technologie (35 %), acquisition et marketing (30 %), recrutement de l'équipe clé (25 %) et conformité réglementaire / licence d'Établissement de Monnaie Électronique (10 %), avec un contrôle de somme à 100 %.
7. **Onglet de contrôles** : réconciliation du chiffre d'affaires entre les onglets Revenue Build et P&L, somme de la table de capitalisation, somme du tableau d'utilisation des fonds (table et montants), réconciliation du résultat net entre P&L et Cash Flow, et un contrôle que la trésorerie de clôture ne devient jamais négative sur l'horizon du plan.
8. **Pitch deck** : construit à partir des mêmes chiffres (modèle financier) et des données de marché réelles et sourcées (taux d'inclusion financière UEMOA, taille du marché mobile money ouest-africain), structuré selon une trame standard de levée de fonds seed (problème, solution, marché, modèle économique, trajectoire financière, positionnement, feuille de route, équipe, demande de financement).

## Key findings

- Le chiffre d'affaires passe de 156 M FCFA en 2027F à 4 829 M FCFA en 2031F, soit une multiplication par environ 31 sur l'horizon du plan.
- La marge d'EBITDA devient positive dès 2028F (28,1 %) et atteint 65,9 % en 2031F, portée par la dégressivité du coût d'acquisition client et par l'activation progressive du micro-crédit (marge nette de 9 %) à partir de l'année 3.
- La trésorerie de clôture ne devient jamais négative sur l'horizon du plan : l'apport des fondateurs et la levée seed, combinés à la génération de cash à partir de 2028F, couvrent le besoin de financement sans recours à un financement additionnel dans le scénario central.
- Le marché adressable est réel et conséquent : 498 Md$ de valeur de transactions mobile money en Afrique de l'Ouest en 2025, sur un taux d'inclusion financière UEMOA qui progresse (47 % en 2016, 72,3 % en 2023) mais reste en deçà de la cible régionale de 90 % d'ici 2030 - l'épargne de groupe structurée demeure un usage largement sous-adressé par les acteurs mobile money existants.

## Files included

- `Business_Plan_Model.xlsx` - modèle complet (Cover, Assumptions, Revenue Build, P&L, Cash Flow, Funding & Cap Table, Dashboard, Checks)
- `Pitch_Deck.pptx` - pitch deck de levée de fonds seed (10 diapositives, thème graphique dédié, graphiques natifs)
- `data/assumptions.csv` - hypothèses propres à KobaPay, toutes signalées comme des choix de l'auteur
- `data/market_data.csv` - données de marché réelles utilisées comme contexte (taux d'inclusion financière UEMOA, marché mobile money ouest-africain)
- `screenshots/` - captures d'écran des principaux onglets du modèle
- `sources.md` - sources des données de marché réelles et avertissement sur le caractère fictif de KobaPay

## Limitations

- **KobaPay est une entreprise entièrement fictive.** Aucune personne réelle n'est associée au projet ; les profils de l'équipe fondatrice présentés dans le pitch deck sont illustratifs.
- Toutes les hypothèses de croissance, de prix, de coûts et de financement sont des choix personnels de l'auteur, calibrés pour raconter une trajectoire plausible de startup fintech - elles ne reposent pas sur un business plan ou des données opérationnelles réelles.
- Le modèle ne couvre qu'un scénario central : il ne modélise pas de scénario dégradé (acquisition plus coûteuse, croissance plus lente, taux de change défavorable) ni de tour de financement ultérieur au-delà du seed.
- Le taux d'IS utilisé (25 %) est une hypothèse générique pour la zone UEMOA, non spécifique à un pays d'immatriculation précis de la société.

## Sources

Voir `sources.md`.
