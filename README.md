# XAI_Explain_Any_Concept

Introduction
Les DNNs sont puissants en vision par ordinateur mais restent opaques, ce qui limite leur usage dans des domaines sensibles. Pour rendre leurs décisions plus transparentes, l’Explainable AI (XAI) s’appuie souvent sur des explications pixel par pixel, peu fidèles et difficiles à comprendre.

Le papier original exploite le Segment Anything Model (SAM) pour extraire automatiquement des concepts visuels, et combine cela avec des valeurs de Shapley pour fournir des explications fidèles, compréhensibles et efficaces via leur pipeline Explain Any Concept (EAC).

Nous reproduisons ici leurs expériences afin de valider les performances et la qualité d’interprétation de cette méthode sur des jeux de données standards.



Résultats expérimentaux
Évaluation Quantitative : Insertion & Deletion
Méthode	Insertion ↑ (moy.)	Deletion ↓ (moy.)	Insertion (σ)	Deletion (σ)
Notre EAC	81.31	20.88	25.46	15.80
EAC (papier)	83.40	23.80	0.023	0.005

Conclusion : Performances globalement similaires, mais notre version présente une variabilité plus élevée (écarts-types), probablement due à un échantillon réduit (4 images) comparé aux 100 images du papier.

👁Évaluation Humaine : Compréhensibilité
Protocole : 6 participants (étudiants en IA) ont comparé les explications générées par notre EAC avec celles des baselines (extraits du papier).

Résultat :

Sur les 4 images testées, EAC a systématiquement été préféré.

Les autres méthodes n’ont pas montré d’avantage significatif.

Interprétation : Indication encourageante que EAC produit des explications plus compréhensibles pour les humains.

Étude d’ablation : Schéma PIE
Comparaison de notre implémentation PIE vs. version originale et calcul direct des valeurs de Shapley.

Méthode	Temps / image
Notre PIE	~10 minutes
PIE (papier)	~4 minutes
Shapley (direct)	>24 heures

Conclusion :

Notre implémentation est moins optimisée que celle du papier (possiblement à cause de hardware ou pipeline),

Mais reste largement plus scalable que le calcul exact.
