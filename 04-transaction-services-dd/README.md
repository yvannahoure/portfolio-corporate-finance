# Projet 4 - Transaction Services / Due Diligence Financière

## Project overview

Exercice de due diligence financière (Transaction Services), construit sur **Fnac Darty (Euronext Paris : FNAC)**, qui reconstitue la démarche d'un analyste TS confronté à des comptes publiés : analyse de la qualité du résultat (« quality of earnings »), pont de réconciliation entre résultat opérationnel courant et résultat net publié, et identification de points de vigilance (« risk flags ») à partir des seules informations disponibles publiquement. L'exercice assume explicitement ses limites : là où l'information publique ne permet pas de reconstituer un chiffre avec certitude, le modèle le signale comme un résidu non documenté à demander en data room, plutôt que d'inventer une répartition plausible.

## Objectives

- Analyser la performance historique (FY2023-FY2025) à travers le prisme de l'EBITDA courant estimé et de sa marge, pour identifier les tendances sous-jacentes.
- Construire un pont de réconciliation explicite entre le résultat opérationnel courant (EBIT) et le résultat net publié (GAAP), en isolant les éléments non récurrents effectivement divulgués.
- Identifier et documenter les points de vigilance (« red flags ») qu'une véritable due diligence financière chercherait à éclaircir en data room.
- Montrer qu'une due diligence crédible nomme ses limites plutôt que de produire une réconciliation faussement précise.

## Methodology

1. **Quality of Earnings** : à partir du résultat opérationnel courant publié (FY2023 : 171 M EUR, FY2024 : 189 M EUR, FY2025 : 203 M EUR), estimation d'un EBITDA courant par ajout d'une dotation aux amortissements. Pour FY2023A-FY2024A, cette D&A est estimée à 3,4 % du chiffre d'affaires (hypothèse cohérente avec celle utilisée dans les projets 2 et 3 du portfolio, pour la continuité méthodologique) ; pour FY2025A, la D&A réelle publiée (464 M€) est utilisée directement, et recoupée avec l'EBITDA réel publié par l'entreprise (667 M€) comme référence externe de contrôle. Calcul de la marge d'EBITDA courant estimée sur les 3 exercices.
2. **Pont EBIT -> Résultat net (FY2025)** : à partir du résultat opérationnel courant publié (203 M EUR), déduction des éléments non récurrents effectivement divulgués par l'entreprise : 123 M EUR de dépréciation de goodwill/marque/IT (activités poursuivies), 60 M EUR de dépréciation sur Nature & Découvertes (activité cédée). L'écart résiduel entre ce total et le résultat net publié (-146 M EUR) représente 166 M EUR **non détaillés publiquement**, signalé explicitement comme tel dans le modèle, avec la mention « à demander en data room », plutôt que d'être réparti de manière inventée entre résultat financier, impôt et intérêts minoritaires.
3. **Risk Flags** : 5 points de vigilance documentés à partir des seules informations publiques (ambiguïté apparente entre un chiffre de dette financière brute et une « position de trésorerie nette » cités sans pont explicite dans le même communiqué, résolue par recoupement avec la trésorerie réelle publiée, voir Key findings ; implications des dépréciations sur la valeur résiduelle du goodwill, notamment Unieuro acquis en novembre 2024 ; marge d'EBITDA courant en hausse sur les 3 exercices, y compris lors de l'intégration d'Unieuro, à confirmer par segment ; le résidu de 166 M EUR du pont ; absence de granularité publique sur le besoin en fonds de roulement normatif).
4. **Onglet de contrôles** : vérification que le pont EBIT -> résultat net se réconcilie exactement à zéro (une identité arithmétique assurée par construction, puisque le résidu de 166 M EUR est lui-même calé pour boucler sur le résultat net publié ; ce contrôle ne vaut donc pas validation comptable indépendante, et le modèle le précise explicitement), que l'EBITDA courant estimé FY2025A se réconcilie exactement avec l'EBITDA réel publié, que le résultat opérationnel courant croît sur les 3 exercices, et que la marge d'EBITDA estimée reste dans une fourchette plausible (3 %-10 %) pour un retailer omnicanal.

## Key findings

- **Point de vigilance méthodologique corrigé** : une première estimation de la D&A FY2025A par la même règle que les 2 exercices précédents (3,4 % du CA) aurait sous-estimé l'EBITDA d'environ 17 % et fait apparaître une marge d'EBITDA en baisse (5,7 % -> 5,4 %). En retenant la D&A réelle publiée (464 M€) pour FY2025A, recoupée avec l'EBITDA réel publié (667 M€), la marge d'EBITDA courant estimée ressort en réalité en **hausse régulière sur les 3 exercices (5,6 % -> 5,7 % -> 6,5 %)**, y compris lors de l'exercice d'intégration d'Unieuro.
- Le résultat opérationnel courant croît de manière régulière sur 3 exercices (171 -> 189 -> 203 M EUR), y compris sur l'exercice de la perte nette publiée, ce qui isole la perte FY2025 comme un phénomène largement comptable (dépréciations) plutôt qu'une dégradation de l'exploitation courante.
- Le pont documente explicitement 183 M EUR de dépréciations non récurrentes divulguées, mais laisse un résidu de 166 M EUR non expliqué par les seules informations publiques, exactement le type de question qu'une véritable due diligence poserait en data room plutôt que de la deviner.
- Deux chiffres (958 M EUR et 146 M EUR) cités dans le même communiqué sans pont explicite entre les deux : un recoupement avec la trésorerie réelle publiée (1 104 M EUR) lève l'ambiguïté. 958 M EUR est la dette financière brute hors IFRS16, et 146 M EUR est le résultat de 958 - 1 104 M EUR, soit une **position de cash net**, cohérente avec la lecture retenue dans le projet 2 (modèle 3 états + DCF). Un bon rappel que la terminologie dette brute / dette nette / position de trésorerie nette doit toujours être vérifiée précisément avant toute valorisation.

## Files included

- `Financial_DD_Analysis.xlsx` - modèle complet (Cover, Quality of Earnings, EBIT to Net Income Bridge, Risk Flags, Checks)
- `data/historical_financials.csv` - données publiées utilisées dans le pont et l'analyse de marge
- `data/assumptions.csv` - hypothèse de dotation aux amortissements utilisée pour estimer l'EBITDA courant
- `screenshots/` - captures d'écran des principaux onglets
- `sources.md` - sources des données publiées

## Limitations

- L'EBITDA courant est **estimé**, non publié directement : il repose sur une hypothèse de dotation aux amortissements (3,4 % du chiffre d'affaires), faute de donnée publique à cette maille.
- Le résidu de 166 M EUR dans le pont EBIT -> résultat net est **explicitement non expliqué** par les informations publiques disponibles ; il est signalé comme tel plutôt que d'être réparti de manière inventée entre résultat financier, impôt et intérêts minoritaires : c'est une limite assumée, pas un oubli.
- L'analyse ne bénéficie pas d'un accès à la data room réelle de l'entreprise (détails de BFR normatif, détail du résultat financier, note d'impôt) : elle démontre la démarche d'une due diligence à partir de l'information publique, pas une due diligence complète.
- Exercice d'entraînement à but pédagogique sur une société cotée réelle, Fnac Darty : ne constitue ni une opinion d'audit ni une recommandation d'investissement.

## Sources

Voir `sources.md`.
