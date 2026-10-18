Projet 3 — Workforce Analytics & Attrition

Construire un outil d'analyse RH à partir de plusieurs sources hétérogènes, puis utiliser Python/R 
pour approfondir certaines analyses que Power BI ne fait pas aussi bien.

Page 1 — Workforce Overview

La page « direction ».

KPI
Total Employees
Attrition Rate
Average Age
Average Monthly Income
Average Tenure
Visuels

Effectifs par département

→ bar chart

Effectifs par Job Level

→ column chart

Attrition Rate par département

→ bar chart

Attrition Rate par Job Role

→ bar chart

Employee population

→ éventuellement une pyramide âge / sexe.

Slicers
Department
Job Role
Gender
Business Travel
Job Level

L'idée est que cette page réponde immédiatement :

« Quelle est la structure actuelle de cette workforce et où se situe le problème d'attrition ? »

3. Page 2 — Compensation & Career

Là, on exploite beaucoup mieux les variables RH.

KPI
Average Monthly Income
Median Monthly Income
Average Years at Company
Average Years in Current Role
Visuels

Salary by Job Role

→ box plot si on passe par Python/R.

C'est justement un endroit où je préfère éviter un simple bar chart.

Un box plot montre :

médiane
quartiles
dispersion
valeurs extrêmes

Donc beaucoup plus pertinent pour les salaires.

Salary vs Tenure

Scatter plot :

X = Years at Company
Y = Monthly Income
Size = Job Level
Color = Attrition

Ça permettrait de voir immédiatement des profils atypiques.

Career progression

Bar chart :

Average Years Since Last Promotion

par :

Job Role
Job Level
Department

Puis éventuellement :

Years in Current Role vs Years Since Last Promotion

4. Page 3 — Attrition Analysis

C'est probablement la page principale du projet.

KPI
Employees
Employees with Attrition
Attrition Rate
Average Income of Leavers
Average Tenure of Leavers
Attrition par département
Department
    ↓
Attrition Rate
Attrition par ancienneté

On crée des groupes :

< 2 years
2–5 years
5–10 years
10–15 years
15+ years

Puis :

Attrition Rate by Tenure

Attrition vs Overtime

Un visuel très intéressant :

OverTime
    │
    ├── Yes
    └── No

        ↓

Attrition Rate
Attrition vs Work-Life Balance

Et là on peut croiser :

Work-Life Balance
        ×
Job Satisfaction
        ↓
Attrition Rate

Une heatmap serait excellente.

5. Page 4 — Employee Experience & Attrition Drivers

C'est ici que je voudrais vraiment utiliser Python/R + Power BI.

On dispose de plusieurs variables subjectives :

Job Satisfaction
Environment Satisfaction
Work-Life Balance
Job Involvement
Relationship Satisfaction
Performance Rating

On peut construire un Employee Experience Score.

Par exemple, avec prudence :

Employee Experience Score
=
Job Satisfaction
+ Environment Satisfaction
+ Work-Life Balance
+ Job Involvement
+ Relationship Satisfaction

Normalisé sur 100.

⚠️ Mais je ne voudrais pas présenter ça comme une mesure officielle de « bien-être ». Ce serait clairement un indicateur composite créé pour l'analyse.

6. Et Python/R apporte quelque chose de vraiment intéressant

Je te propose 3 analyses complémentaires, mais on ne les fera que si les résultats sont réellement pertinents.

A. Analyse statistique

Par exemple :

Chi-square

pour tester l'association entre :

Overtime ↔ Attrition
Department ↔ Attrition
Job Satisfaction ↔ Attrition
Work-Life Balance ↔ Attrition

Puis on pourrait avoir dans Power BI quelque chose comme :

Variable	Attrition association	p-value
Overtime	...	...
Job Satisfaction	...	...
Work-Life Balance	...	...

Ça serait beaucoup plus sérieux qu'un simple :

« Les salariés en overtime partent davantage ».

B. Logistic regression

Là, on peut faire quelque chose de très portfolio-friendly.

Python :

Attrition ~
Age
+ MonthlyIncome
+ JobLevel
+ OverTime
+ JobSatisfaction
+ WorkLifeBalance
+ YearsAtCompany
+ YearsSinceLastPromotion
...

On obtient :

coefficients
odds ratios
intervalles de confiance
significativité

Et on pourrait produire un visuel Power BI :

Factors associated with attrition
                Lower attrition       Higher attrition
                       ←───────────────→

Overtime
YearsSincePromotion
JobSatisfaction
MonthlyIncome
YearsAtCompany
...

Très important : on parlerait d'association, pas de causalité.

7. C. Segmentation des employés

C'est probablement l'analyse Python que je trouve la plus intéressante.

On peut faire un clustering :

Variables
Age
Income
Tenure
JobLevel
JobSatisfaction
WorkLifeBalance
JobInvolvement
Performance

Puis par exemple :

Cluster 1 — Experienced / Stable
Cluster 2 — Early Career
Cluster 3 — High Responsibility
Cluster 4 — Low Satisfaction

Et on ramène le cluster dans Power BI.

Là, le projet devient vraiment intéressant

Power BI :

Who are our employees and where is attrition concentrated?

Python :

Can we identify employee profiles with different characteristics?

Power BI :

How do these profiles differ in attrition, compensation and satisfaction?

Ça donne une vraie boucle analytique.

8. Page 5 — Employee Profile

On conserve le drill-through.

Quand on sélectionne un employé :

Profile
Age
Gender
Department
Job Role
Job Level
Business Travel
Career
Total Working Years
Years at Company
Years in Current Role
Years Since Last Promotion
Years With Current Manager
Compensation
Monthly Income
Percent Salary Hike
Experience
Job Satisfaction
Environment Satisfaction
Work-Life Balance
Job Involvement
Performance Rating

Et surtout :

Attrition

9. Le rôle exact de Python/R

Je veux éviter qu'on tombe dans le piège :

Power BI + Python + R + ML + statistiques + 50 graphiques

Ça ferait artificiel.

Je ferais plutôt :

Power BI = produit principal
Data preparation
        ↓
Data model
        ↓
DAX
        ↓
Interactive dashboard
Python = analyse complémentaire
EDA
│
├── statistical tests
├── logistic regression
└── clustering

Puis les résultats utiles reviennent dans Power BI.

10. Et je garderais une analyse visuelle Python

Il y a un autre intérêt : ton portfolio montre déjà Python/R, donc on peut produire 1 ou 2 figures scientifiques propres.

Par exemple :

Distribution du revenu par Job Level

avec :

violin plot
box plot
points individuels éventuellement

Ou :

Odds ratios de la régression logistique

C'est une figure très professionnelle et beaucoup plus intéressante qu'un énième camembert Power BI.

On pourrait la mettre dans le README ou dans une page « Statistical Analysis », plutôt que forcément l'intégrer au .pbix.

11. Ce que ça apporte à ton portfolio

Tes trois projets commenceraient à avoir une vraie logique :

Projet	Domaine	Ce qu'il démontre
01 Business Performance	Business	BI classique + DAX + Time Intelligence
02 Global Liver Cancer Atlas	Health Data	Multi-source + géospatial + épidémiologie
03 Workforce Analytics	HR / Analytics	Modélisation multi-fichiers + statistiques + segmentation

Et surtout :

Projet 1
→ Can I build a BI dashboard?

Projet 2
→ Can I apply Power BI to complex scientific data?

Projet 3
→ Can I combine BI with statistical/data-science analysis to answer a business question?

C'est beaucoup plus cohérent pour ton profil de Data Scientist / Data Analyst.

Une précaution importante

Le dataset est synthétique, pas un véritable historique RH IBM. La source elle-même le décrit comme un dataset fictif créé à des fins éducatives.

Donc dans le README, on écrira clairement :

Synthetic dataset originally created by IBM for educational purposes.

Et on évitera toute formulation du type « analysis of IBM employees ».

Donc je valide cette direction

Projet 3 = Workforce Analytics & Attrition

avec :

Power BI

5 pages
modèle relationnel
Power Query
DAX
drill-through
segmentation
KPI
dashboard décisionnel

Python/R

EDA
tests statistiques
régression logistique
éventuellement clustering
1–2 visualisations analytiques réutilisables

Et on ne commence pas encore à construire le PBIX.

La prochaine étape logique est de récupérer les 3 fichiers exacts du dataset et les inspecter ensemble
 (colonnes, types, clés, doublons, correspondances EmployeeID, valeurs manquantes), puis je te donne l'architecture exacte du modèle 
 avant que tu touches à Power BI.