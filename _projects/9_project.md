---
layout: page
title: Time-series analysis for weather data
description: 
img: assets/img/ts_arima.png
importance: 9
category: Data Science
---

# Executive summary
In this project, I analyzed the Central England Temperature (CET) dataset, which records mean monthly temperatures from 1659 to the present. My main goal was to examine trends in temperature over time using various statistical methods, with a focus on identifying and forecasting long-term temperature trends.

### Key Points:
1. **Dataset**: The CET dataset is one of the longest temperature records in existence, with over 360 years of data. However, the dataset was missing values for November and December 2022, so I substituted these with the mean temperatures from the same months in 2021.

2. **Long-Term Trends**: My analysis indicated a clear upward trend in temperatures, particularly in the past 50 years. I used smoothing techniques to highlight these trends, showing that the rate of temperature increase has accelerated, especially since the 1990s.

3. **ARIMA Models**: I employed ARIMA models to analyze annual and seasonal temperature data. After testing several models, I selected ARIMA(0,1,1) for the annual data due to its balance between accuracy and simplicity. This model predicts a continued increase in temperatures for the coming years, though I acknowledge some limitations in short-term forecasting accuracy.

4. **Seasonal Analysis**: I also examined temperature data by season (Winter, Spring, Summer, Fall) using ARIMA models. The analysis revealed that all seasons exhibit a warming trend, although the rate of increase slowed during the 2000s in Central England.

5. **Spectral Analysis**: A spectral analysis of the monthly data confirmed the presence of strong seasonal cycles, with dominant frequencies corresponding to 12-month and 6-month periods. This indicates that temperature patterns are highly influenced by seasonal changes.

6. **Conclusions**: I concluded that there is an ongoing trend of rising temperatures in Central England, with predictions indicating that this trend will continue in the near future. However, I also note that the models used are relatively simple and may not fully capture the complexities of climate change.

Overall, this project provides a detailed statistical analysis of historical temperature data in Central England, highlighting the ongoing impact of global warming in this region.

### Full Project write-up
<object data="/assets/pdf/time_series_climate.pdf" width="600" height="800" type='application/pdf'></object>


