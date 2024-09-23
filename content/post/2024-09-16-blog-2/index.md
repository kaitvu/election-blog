---
title: "Blog 2: The Economy"
author: "Kaitlyn Vu"
date: "2024-09-15"
slug: "blog-2"
categories: []
tags: []
---

## Introduction
"It's the economy, stupid." Coined by political strategist Jim Carville, the phrase became a hallmark of Bill Clinton's successful election bid against incumbent George H.W. Bush in 1992. Larry Bartels and Christopher Achen note in their 2016 book _Democracy for Realists_ that voters engage in "economic voting," through which economic distress — especially during an election year — harms election outcomes for the incumbent. However, to what extent do Americans truly vote based on the state of the economy? In this blog, I utilize economic factors such as GDP and RDI growth to predict presidential election outcomes and assess the utility of a predictive model based solely on the economy.  



## Historical Trends with Gross Domestic Product (GDP)
To start, I analyze the relationship between GDP growth and the incumbent party's national popular vote share from past presidential elections. I utilize GDP growth from Quarter 2 (Q2) of an election year: Q2 is the period of April through June, which provides a stable but recent snapshot of the pre-election economy.  

Notably, the plot on the left includes all the presidential elections from 1948-2020, while the plot on the right excludes 2020. The 2020 contest between President Joe Biden and former President Donald Trump is a significant outlier: unprecedented economic turmoil stemming largely from the COVID-19 pandemic [tanked](https://www.reuters.com/markets/us/us-election-uncertainty-slowdown-heady-mix-markets-mcgeever-2024-07-03/) the national economy during that election year.  

<img src="{{< blogdown/postref >}}index_files/figure-html/historical gdp-1.png" width="1152" />

This is a regression table for the incumbent party's national popular vote share and Q2 GDP growth for the presidential elections from 1948-2016. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for Q2 GDP Growth (1948-2016)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Incumbent Party's National Popular Vote Share</th>
</tr>
<tr>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">Predictors</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">p</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">(Intercept)</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">49.38</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.42</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">46.37&nbsp;&ndash;&nbsp;52.38</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.74</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.27</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.17&nbsp;&ndash;&nbsp;1.30</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.014</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">18</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.325 / 0.283</td>
</tr>

</table>

As expected, there is a positive relationship between Q2 GDP growth and the incumbent party's national popular vote in past presidential elections. This correlation strengthens when we exclude the 2020 election: the slope of the line of best fit increases from 0.27 to 0.74. However, the R-squared value of approximately 0.2 for the 1948-2016 plot suggest that this relationship isn't particularly strong. R-squared values measure how much variation in the dependent variable (incumbent party's national vote share in this case) is captured by the fitted model's predicted value — offering an ease of interpretability for in-sample fit. However, it is important to note that utilizing in-sample model fit alone can contribute to overconfidence or over-fitting. 

## Historical Trends with Real Disposable Personal Income (RDI)
Similarly, I examine the relationship between Q2 RDI growth and the incumbent party's national popular vote share. I include RDI in this blog to engage with more individualistic perceptions of voter behavior like "pocketbook voting": voters may prioritize their own economic well-being over broader national  indicators like GDP. The left plot includes presidential elections from 1948-2020, while the right plot excludes 2020.

<img src="{{< blogdown/postref >}}index_files/figure-html/historical rdi-1.png" width="1152" />

This is a regression table for the relationship between the incumbent party's national popular vote share and Q2 RDI growth for the presidential elections from 1948-2016. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for Q2 RDI Growth (1948-2016)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Incumbent Party's National Popular Vote Share</th>
</tr>
<tr>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">Predictors</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">p</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">(Intercept)</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">49.87</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.93</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">45.77&nbsp;&ndash;&nbsp;53.96</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">RDPI growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.46</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.32</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.23&nbsp;&ndash;&nbsp;1.15</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.176</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">18</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.111 / 0.056</td>
</tr>

</table>

With RDI, excluding 2020 makes quite a significant difference: the slope of the best fit line jumps from -0.03 to 0.46. Again, there appears to be a positive correlation between Q2 RDI growth and the incumbent party's national popular vote share in past presidential elections. The R-squared values here are lower than those for GDP growth, however, which suggests that the Q2 RDI growth is also not a strong predictor of the incumbent party's national popular vote share. 

## Sitting Presidents vs Same-Party Heirs
Next, I examine whether the effect of the economy is stronger for sitting presidents running for re-election compared to same-party heirs seeking the office. First, I sorted the data into elections where the incumbent was running for re-election (11 elections) and elections where a candidate of the incumbent's party was running (7 elections). The left plot is for sitting presidents, while the right plot is for same-party heirs. Once again, I exclude 2020 from the analysis.

<img src="{{< blogdown/postref >}}index_files/figure-html/comparison gdp-1.png" width="1152" />

The associated regression table is below.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Comparison Regression Table for Q2 GDP Growth (1948-2020)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Sitting Presidents</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Same-Party Heirs</th>
</tr>
<tr>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">Predictors</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">p</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col7">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col8">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col9">p</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">(Intercept)</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">50.43</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.85</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">46.25&nbsp;&ndash;&nbsp;54.61</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">48.46</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col7">1.65</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col8">44.21&nbsp;&ndash;&nbsp;52.72</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col9"><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.85</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.32</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.12&nbsp;&ndash;&nbsp;1.57</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.027</strong></td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.29</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col7">0.36</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col8">&#45;0.64&nbsp;&ndash;&nbsp;1.22</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col9">0.458</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">7</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.437 / 0.375</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.114 / -0.063</td>
</tr>

</table>

With a slope of 0.85, it seems that there is a stronger correlation between Q2 GDP growth and national popular vote share for sitting presidents running for re-election than same-party heirs (0.29). The R-squared value for the sitting presidents model is also larger (0.44 vs 0.11), which means that Q2 GDP growth is a much stronger predictor of the national popular vote share for sitting presidents than same-party heirs.

I created the same visualizations for Q2 RDI growth. 

<img src="{{< blogdown/postref >}}index_files/figure-html/comparison rdi-1.png" width="1152" />


<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Comparison Regression Table for Q2 RDI Growth (1948-2020)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Sitting Presidents</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Same-Party Heirs</th>
</tr>
<tr>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">Predictors</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">p</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">Estimates</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col7">std. Error</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col8">CI</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  col9">p</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">(Intercept)</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">50.39</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">2.36</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">45.06&nbsp;&ndash;&nbsp;55.73</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">51.49</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col7">2.17</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col8">45.92&nbsp;&ndash;&nbsp;57.06</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col9"><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">RDPI growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.69</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.37</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.15&nbsp;&ndash;&nbsp;1.54</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.095</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.46</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col7">0.41</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col8">&#45;1.51&nbsp;&ndash;&nbsp;0.59</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  col9">0.307</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">7</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.279 / 0.198</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.206 / 0.047</td>
</tr>

</table>

For RDI, sitting presidents have historically enjoyed a positive correlation between Q2 RDI growth and national popular vote share with a slope of 0.69 for the line of best fit. On the other hand, there appears to be a negative relationship between Q2 RDI growth and national popular vote share for same-party heirs with a slope of -0.46. Again, the R-squared value for the sitting presidents model is a bit greater (0.28 vs 0.21), which means that Q2 RDI growth is a stronger predictor of the national popular vote share for sitting presidents than same-party heirs. 

## Predictions for 2024
While such univariate models are imperfect, we can still use them to develop predictions for the 2024 election. The following table utilizes the regression models included in this blog to estimate the national popular vote share for the incumbent party's candidate; in this case, Vice President Kamala Harris is a same-party heir so those equations also apply. Based on the table, Harris is predicted to receive a bit over 50% of the national popular vote this November.


|Model    |   Fit| Lower CI| Upper CI|
|:--------|-----:|--------:|--------:|
|GDP      | 51.58|    41.86|    61.31|
|Heir GDP | 49.34|    40.69|    57.98|
|RDI      | 50.33|    38.90|    61.76|
|Heir RDI | 51.03|    42.04|    60.01|

## Conclusion
In very general terms, it seems that the incumbent's party enjoys an advantage when the economy is doing well. Furthermore, the effect of the economy appears to be stronger for sitting presidents running for re-election than same-party heirs. 

However, the relatively low R-squared values of all these simple models suggest that GDP and RDI growth only loosely fit national popular vote data. As such, continuing to add different variables — beyond the economy — to my model can help to increase its predictive performance. The predictive power of the economy can vary over time due to factors such as unexpected economic shocks (e.g. COVID-19), other policy concerns, and/or increasing political polarization.
