# Difference in Air Quality in Days and Nights in an Italian City

## Introduction
Air pollution is one of the leading causes of health problems. Measuring air quality in urban areas is important for regulating outdoor activities and preserving a healthy lifestyle. Air quality is measured through sensors that detect pollutants/particles in the air. Based on this detection, air quality is placed on an index that ranges from 0 ("good") to 500 ("hazardous") (Lemeš, 2018). On a daily basis, the air quality varies with surges in activities that induce more air pollution, such as intense traffic during rush hour (Trozzi et al., 1999). 

This begs us to ask the question: **How do the summarized sensor responses used to determine air quality index differ between day and night in an Italian city from 2004 to 2005?**

For our research, we use the dataset <a href="https://archive.ics.uci.edu/dataset/360/air+quality">Air Quality</a> from the UCI machine learning repository, which we have stored in a separate GitHub repository. It contains responses to gas and particle sensors placed in a highly polluted area of an Italian city. This data was collected from 2004-2005 and depicts 9348 observations of hourly averaged concentrations of different chemical air pollutants. For the purpose of our research, we are taking readings from one month and removing cases with missing data. Our variables of interest are the ```date```, ```time```, and hourly averaged sensor response columns of ``` PT08.S1``` (carbon monoxide), ```PT08.S2``` (non-metallic hydrocarbons), ``` PT08.S3``` (NO<sub>x</sub>), ```PT08.S4``` (NO<sub>2</sub>), and ```PT08.S5``` (O<sub>3</sub>). Using sensor response variables, we will create an AQI estimator that is analogous to the true AQI but isn't bound by the range of 0 to 500. We will find the differences in the means and medians of the AQI estimators for an enhanced understanding of variability in air quality.


## Methods and Results
Our preliminary report can be considered trustworthy as it is pre-processed from a reputable dataset from the UCI machine learning repository, with any missing entries removed to ensure reliable results presented as plots and estimates. However, this may not be sufficient for stakeholders who require more evidence. So, we aim to complement the plots with hypothesis testing and confidence intervals to make inferences about the population parameters with a certain level of confidence.

**Proposed Plan:**

We will conduct **two hypothesis tests** to compare the average and median AQI estimator values between day and night. For the means, the null hypothesis (H<sub>0</sub>) would be that there is no significant difference in the mean AQI estimator values during day and night, while the alternative hypothesis (H<sub>A</sub>) would be that a significant difference exists. A similar hypothesis test will be performed to assess a difference in medians, with the null hypothesis (H<sub>0</sub>) being that there is no significant difference in the median AQI estimator values during day and night, and the alternative hypothesis (H<sub>A</sub>) being that a significant difference exists. To conduct our hypothesis tests we will be using the explanatory variable of the time of day (day vs night) in order to observe our response variable (air quality). This is to ensure consistency and corroborate our findings regarding air quality in the Italian city, and eliminate vagueness in our results.

We chose the explanatory variable because there may be underlying environmental causes for differences in air quality during time of day. Moreover, the air quality may differ in the day or night due to properties in the air, causing it to hold more/less chemicals, resulting in higher/lower air quality.

We chose a **5% significance level** since this is a common value used in other studies on air quality and is widely applicable in our present research (Jelili, M. O. et al., (2020); Zhao, X. et al., (2018)). Furthermore, this will give a more accurate result as opposed to a larger/smaller significance level that would increase chances of making a Type I or Type II error.

We also construct **confidence intervals** (using a confidence level of 95%) for the summarized sensor response during day and night separately, to obtain a range of plausible values for the population mean and median, providing a measure of uncertainty around our estimates.

**Expected Results:**

Although our preliminary research showed otherwise, we expect to find that air quality is worse in the day. Based on previous research, the highest concentrations of different chemical pollutants occur in the day, likely due to traffic density, road dust, or temperature inversions (Chen et al., 2015).


### Results:

After we did the paired t-tests for day and night AQI Estimator values, the p-value was 5.04652923636584e-10. This was reinforced by our p-values from the bootstrap distribution of null model statistics for the difference in both means and medians, both being less than 0.001. This gives us a strong incentive to reject the null hypothesis (no significant difference in the mean or median AQI estimator values) at a significance level of 5%, in favour of the alternative hypothesis (significant differences in both the mean and the median AQI estimator values). We observed that the summarized AQI estimator values were higher in the night than the day, implying that air quality was worse at night in this Italian city. The mean AQI estimator value was 81.04807 units higher in the night than day, while the median AQI estimator was 109.6 units higher in the night than day.

**Bootstrapping vs. Asymptotics:**

Both bootstrapping and asymptotic methods gave us similar results for our p-value, being extremely close to 0. We find using the asymptotics method to yield more specific results, as the resulting p-value of 5.04652923636584e-10 is extremely precise. As mentioned earlier, the p-value of 0 obtained through bootstrapping enforces the assumption that there is no room for *not* rejecting our null hypothesis, which is ill-practice. Also, larger sample sizes inherently lead to more precise estimates of population parameters, and the asymptotic approach capitalizes on this. In our case, the relatively substantial dataset we employed further bolstered the precision of the p-value obtained through asymptotics. Asymptotics are a good fit for our p-value, while bootstrapping tends to underfit the true p-value (Ramses et al., 2020).

**Effect Size Consideration:**

In addition to evaluating statistical significance, it's crucial to consider the effect size of the observed differences in AQI estimator values. While our analysis indicates a statistically significant difference, quantifying the magnitude of this difference provides a deeper understanding of its practical implications. A larger effect size signifies a more substantial and potentially more meaningful difference in air quality between the two time periods. This consideration aids stakeholders in assessing the practical significance of our findings and their real-world impact on urban planning and public health policies.


## Discussion

We expected to find that air quality would be worse during the day, based on research indicating different urban activities affect pollutants in the air. After conducting our hypothesis tests, we found that our results contradicted this, but was in line with our preliminary findings of air quality being worse at night.

**Implications and Further Research:**

The finding of this research could have implications for urban planning and public health policies. City and environmental agencies can use this information to implement interventions during specific times to improve air quality and protect health.

This could lead to further research on the long term health effects of exposure to poor air quality in cities. Additionally, one could explore the relationship between air quality and specific sources of pollution, like vehicular emissions or industrial activities. In conclusion, this comprehensive report aimed to shed light on the difference in air quality in an Italian city during days and nights. By incorporating hypothesis testing and confidence intervals, we can provide more robust evidence to stakeholders, facilitating informed decision-making and potential policy changes for healthier urban environments. The research findings could lead to further investigations and have a positive impact on public health and environmental management, particularly in curbing sources of air pollution in the night.

There are several potential reasons for the difference observed in the air qualities between night and day:
- The different conditions of atmospheric diffusion. There are different conditions of things like solar illumination, wind speed, and moderation in the day and night, which affect the AQI.
- Variations in traffic and industrial activities also contribute to the differences in AQI between day and night.

Though we measured a month's worth of data in our research, we can generalize this finding to the rest of the data and consider it a representative sample. Based on the tests we conducted on the difference in means and the difference in medians, overall we found that the air quality was worse in the **night** than in the day. Though both tests measured similar variables, we found this to be conducive to our research, as measuring the difference in medians after the difference in means provided further evidence in support of our initial result.


## References

Chen, W., Tang, H., & Zhao, H. (2015). Diurnal, weekly and monthly spatial variations of air pollutants and air  quality of Beijing. Atmospheric Environment, 119, 21-34. https://doi.org/10.1016/j.atmosenv.2015.08.040

Jelili, M. O., Gbadegesin, A. S., & Alabi, A. T. (2020). Comparative Analysis of Indoor and Outdoor Particulate Matter Concentrations and Air Quality in Ogbomoso, Nigeria. Journal of health & pollution, 10(28), 201205. https://doi.org/10.5696/2156-9614-10.28.201205

Lemeš, S. (2018). Air Quality Index (AQI) - Comparative Study and Assessment of an Appropriate Model for B&H. 12th Scientific/Research Symposium with International Participation. 

Ramses, A.N., Stapenhurst, C., & Yalonetzky, G. (2020). Asymptotic Versus Bootstrap Inference for Inequality Indices of the Cumulative Distribution Function. Econometrics, 8(1). https://doi.org/10.3390/econometrics8010008

Trozzi, C.,  Vaccaro, R., & Crocetti, S. (1999). Air quality index and its use in Italy’s management plans. Science of the Total Environment. 235(1-3),387-389. https://doi.org/10.1016/S0048-9697(99)00242-9

Zhao, X., Gao, Q., Sun, M., Xue, Y., Ma, R., Xiao, X., & Ai, B. (2018). Statistical Analysis of Spatiotemporal Heterogeneity of the Distribution of Air Quality and Dominant Air Pollutants and the Effect Factors in Qingdao Urban Zones. Atmosphere, 9(4), 135. MDPI AG. http://dx.doi.org/10.3390/atmos9040135
