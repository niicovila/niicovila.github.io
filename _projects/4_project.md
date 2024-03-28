---
layout: page
title: Visual Analytics WebApp integrating ML and XAI for car price predictions
description: Interactive platform leveraging data analytics and machine learning to predict car prices.
img: assets/img/pr4.png
importance: 4
category: Data Science
---

[This project](https://github.com/niicovila/Visual-Analytics-Web-App-with-ML-Integration) is aimed at providing an easy and visual way to obtain  insights from the automobile industry. By leveraging advanced data analytics techniques and machine learning models, the project provides users with actionable insights into price trends, as well as a predictive ML model that helps them find a data-based price for any car features they wish.

### Data Exploration & Analytics
This feature empowers users to delve into their datasets with ease and precision. Through interactive visualizations and intuitive tools, users can gain insights into their data's patterns, trends, and anomalies. Whether exploring relationships between variables, detecting outliers, or uncovering hidden correlations, this feature enables users to extract actionable insights and drive data-driven decision-making.



### ML Salary Predictions

This feature simplifies the exploration of data by allowing users to select different features to obtain price predictions. Users can interactively choose the features they're interested in, such as mileage, year, or model, and receive instant predictions. These predictions are then conveniently displayed and stored in a table format, making it easy for users to compare and analyze the impact of different features on the predicted prices.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/PredModel.mov" title="Web-App Visualization" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Web-App Visualization of Model Predictions feature
</div>

### Explainable AI
This feature helps users understand how our predictive model works by using SHAP (SHapley Additive exPlanations) values. These values show the contribution of each feature to a prediction. By visualizing SHAP values, users can easily see which factors influence the model's decisions the most. This makes it simpler to trust and interpret the model's predictions, leading to more informed decision-making.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/Explainability.mov" title="Web-App Visualization" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Web-App Visualization of XAI feature
</div>
