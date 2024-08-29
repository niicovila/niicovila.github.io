---
layout: page
title: Communities and Crime Analytics with Big Data
description: Analyzing the factors contributing to violent crime rates across communities in the United States
img: assets/img/bd_project.png
importance: 7
category: Data Science
---

This comprehensive report analyzes the factors contributing to violent crime rates across communities in the United States. The analysis is based on a dataset provided by the UCI Machine Learning Repository called the Communities and Crime Data Set.
The key factors driving violent crime rates were initially explored through data visualization techniques. These revealed two main axes of variables contributing to violent crime: economic conditions
(evidenced by median income, level of poverty, and level of unemployment) and family formation (such
as whether children are born to married parents and the incidence of divorce).
Various statistical and machine-learning techniques were subsequently employed to deepen the analysis. Linear and Lasso regression techniques identified additional statistically relevant determinants of
violent crime rates, including demographic factors (specifically age), housing, and the level of immigration in given communities.
A decision tree model was developed to identify the critical variables predicting violent crime rates,
revealing the importance of family structure (PctFam2Par) and the racial composition (racePctWhite)
of a community. However, the most robust predictive performance came from a Random Forest model.
This ensemble learning technique, which constructs multiple decision trees, effectively addressed overfitting issues and demonstrated strong predictive capability.
Unsupervised learning techniques were also used, with Principal Component Analysis (PCA) and
K-Means clustering employed to identify the most influential variables and categorize communities
based on these factors. The PCA showed the distinction between structured and unstructured families as highly important to the incidence of violent crime, with the level of immigration also being
significant. The K-Means clustering technique effectively grouped communities into clusters based on
similarities in their characteristics.
The report concludes that a complex combination of economic conditions, family-level factors, demographics, and immigration levels drive violent crime rates. It challenges simple economic explanations,
proposing instead a more nuanced interpretation based on the specific circumstances of individual communities. Furthermore, it emphasizes the predictive power of the Random Forest model over linear
regression models, which showed high R-squared values but were susceptible to overfitting considering
the high dimensional nature of the dataset.
Future work could include the examination of additional community characteristics, further validation of the models on different datasets, and an exploration of other machine learning models and
techniques. The insights from this analysis could inform targeted policy interventions aimed at reducing violent crime rates in specific communities.

### Analysis write-up
<object data="/assets/pdf/BigData_crime_analysis.pdf" width="800" height="500" type='application/pdf'></object>




