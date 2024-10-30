---
title: "Blog 8: Shocks"
author: "Kaitlyn Vu"
date: '2024-10-27'
slug: blog-8
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
We're in the home stretch, folks! Welcome to my last blog update for the 2024 presidential election, which less than two weeks away. This week, we discussed "shocks," a broad category of external factors and events that aren't the result of campaigns or systematic fundamental forces. Such shocks can range from pandemics to natural disasters and local college football victories, all with potential implications for voter behavior — depending on who you ask. 

In this blog, I briefly discuss the role of shocks in presidential elections and continue to update my national and state-level models in preparation for my final prediction!



## Assessing Shocks
The effects of shocks on elections are perhaps best understood through the logic of retrospection, where voters look to the past to assess incumbent performance. To [Christopher Achen and Larry Bartels](https://press.princeton.edu/books/hardcover/9780691169446/democracy-for-realists?srsltid=AfmBOooJLrwf2Na-MT6i50wNH-lmkWRNnBe4VaKlWVyLFriDwas1hnk9), voters' supposed reactions to shocks paint a bleak picture for democracy: voters are swayed by irrelevant factors — such as shark attacks — and fail to accurately evaluate the current government and incumbent. [Andrew Healy and Neil Malhotra](https://www.nowpublishers.com/article/Details/QJPS-9057) likewise finds that voters punish incumbents for random events (droughs, floods, economic shocks, etc) and fail to differentiate between government-caused outcomes and uncontrollable external factors. Following this perspective, shocks and their impact on voting behavior undermine the democratic ideal of elections as accountability mechanisms.

However, there's also evidence to prove that shocks don't truly have a predictive effect on election outcomes. [Marco Mendoza and Semra Sevi](https://www.researchgate.net/publication/354002319_Did_exposure_to_COVID-19_affect_vote_choice_in_the_2020_presidential_election) find that COVID-19 exposure didn't consistently affect voting — pre-existing partisan identities had a much stronger role. 

Let's quickly revisit the polling visualization with potential "game-changers" from Blog 3. Here is the updated plot with national polling averages to the date of this blog's writing (October 24, 2024). 

<img src="{{< blogdown/postref >}}index_files/figure-html/poll averages 2024-1.png" width="1056" />

Again, it is difficult to establish a causal relationship between potential "game-changers" and trends in public opinion. That being said, polling doesn't seem to change much following these events. Perhaps it's because America has become so [politically calcified](https://www.newser.com/story/327917/a-theory-to-explain-modern-politics-calcification.html) that such "shocks" don't affect us: we'll still be voting for our party's candidate at the end of the day. It's interesting to think about what would happen if we put the craziness of the 2024 election cycle in the context of another presidential election year — would these potential "game-changers" have more of a notable effect?

To conclude this discussion on shocks, I briefly look at the potential effect of hurricanes on electoral outcomes. For this graph, I plot a regression between the number of hurricanes in a presidential election year (occurring before November) and the two-party popular vote share for the incumbent party's candidate.

<img src="{{< blogdown/postref >}}index_files/figure-html/hurricanes-1.png" width="960" />

For this regression, the slope of the line of best fit is barely greater than 0 and the R-squared value of 0.17 is low. This seems to indicate that there isn't a strong relationship between the number of hurricanes in a presidential election year and the two-party popular vote for the incumbent party's candidate. Specifically, the low R-squared value indicates that only a small portion of vote share variation is explained by the number of hurricanes, implying that other factors likely play a much larger role in influencing election outcomes.

So, do shocks matter for presidential election outcomes? The answer is obviously complicated, but these two simple analyses seem to signal that they do not. 

## National Two-Party Popular Vote Model
For this week's national model, I test a different combination of the factors that I've been using previous weeks: quarterly GDP growth for Q2 of the election year, national October polling averages (weighted by weeks left before the election), national two-party percentage of voters, and an incumbent variable (1 if the incumbent party candidate was also the incumbent president, 0 if not). The regression table is below!

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for National Model (1968-2016)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">National Popular Vote Share for Incumbent Party Candidate</th>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">21.77</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">5.19</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">9.81&nbsp;&ndash;&nbsp;33.74</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.003</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.50</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.14</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.18&nbsp;&ndash;&nbsp;0.82</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.007</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">oct poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.47</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.08</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.29&nbsp;&ndash;&nbsp;0.64</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">two party percent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.12</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.06</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.02&nbsp;&ndash;&nbsp;0.26</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.093</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">incumbent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.13</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.08</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;1.36&nbsp;&ndash;&nbsp;3.61</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.327</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">13</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.920 / 0.880</td>
</tr>

</table>

The model has an R-squared value of 0.92 and R-squared adjusted value of 0.88, which suggests that it is a strong predictor for the incumbent party candidate’s national two-party popular vote share. Here, Q2 GDP growth and October national polling averages are statistically significant predictors, while two-party percent and incumbent status aren't statistically significant. Once again, we only have polling data up to the date of this blog's writing (October 24, 2024). I now use this model to predict Vice President Harris' (the incumbent party candidate) share of the national two-party popular vote. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:right;"> Prediction </th>
   <th style="text-align:right;"> Lower Bound </th>
   <th style="text-align:right;"> Upper Bound </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 52 </td>
   <td style="text-align:right;"> 47.49 </td>
   <td style="text-align:right;"> 56.52 </td>
  </tr>
</tbody>
</table>

Similar to last week, this model predicts that Harris will win 52% of the national two-party popular vote. The prediction intervals are also smaller here than the previous two weeks! 

Next, let's assess the out-of-sample fit for this model. I performed 1,000 runs of a cross-validation, randomly selecting half of the election years in my data set to test the model each run. Here, the mean of the absolute value of the out-of-sample residuals was approximately 3.63. Considering that the national two-party vote share spans nearly 20 points, this suggests a positive indication of the model's performance. This histogram displays the distribution of out-of-sample errors for this week's national model.

<img src="{{< blogdown/postref >}}index_files/figure-html/national model out-of-sample fit-1.png" width="960" />
The errors appear slightly right-skewed, indicating the model occasionally underestimates the incumbent party's performance by a wider margin than it overestimates.

Here is a summary visualization for this week's prediction of the national two-party popular vote! The dashed black line indicates 50% of the national popular vote. 

<img src="{{< blogdown/postref >}}index_files/figure-html/national prediction viz-1.png" width="960" />

## State Two-Party Popular Vote Model & Electoral College Prediction
Moving onto my state-level model, I utilize September state polling averages, October state polling averages, and an indicator for the incumbent party (1 if an incumbent party candidate, 0 if not) as coefficients. Not bounded by the campaign events data of last week, I train the model on presidential elections from 2000 to 2020. The regression table for the Democratic candidate's state-level popular vote share is below.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for State Model (2000-2020)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Democrat's State-Level Popular Vote Share</th>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;2.33</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;4.52&nbsp;&ndash;&nbsp;-0.14</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.037</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.31</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.14</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.57&nbsp;&ndash;&nbsp;-0.04</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.024</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">oct poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.43</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.13</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.17&nbsp;&ndash;&nbsp;1.69</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">incumbent party</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">2.57</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.39</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.81&nbsp;&ndash;&nbsp;3.33</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">290</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.894 / 0.893</td>
</tr>

</table>

Higher than last week, the R-squared values of 0.89 indicate the model's strong fit. All the coefficients here are statistically significant. October polling is a strong positive predictor of the Democratic state-level popular vote share with the incumbent variable also a significant positive coefficient. On the other hand, September polling is a negative, slightly smaller coefficient, indicating that higher September polling averages slightly reduce the predicted Democratic vote share — which seems counter-intuitive. This may indicate some noise in earlier polls or possible overemphasis on early polling that might shift by Election Day.

This is the state model's prediction for our 13 states of interest. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> State </th>
   <th style="text-align:right;"> Prediction </th>
   <th style="text-align:right;"> Lower Bound </th>
   <th style="text-align:right;"> Upper Bound </th>
   <th style="text-align:left;"> Winner </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Arizona </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.26 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 43.89 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.62 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 48.89 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 42.52 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 55.26 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.35 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.09 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.56 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.19 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.93 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.75 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.38 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.13 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.59 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.22 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.96 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.08 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.70 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.45 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Mexico </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.03 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.66 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.41 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.95 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.58 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.31 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.69 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.32 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.06 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 47.41 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 41.04 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 53.78 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.11 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.74 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.48 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.83 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.46 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.21 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

Like last week, this model predicts that Harris will win 11 out of the 13 states, with Trump winning Florida and Texas again. The electoral margin continues to decrease from week to week (e.g. Pennsylvania 51.69% this week vs 51.79% in Blog 7 and 52.86% in Blog 6) with smaller prediction intervals as well. Obviously, these races are still extremely close and most of the prediction intervals include 50%. 

To visualize this, I calculate the predicted win margin for Harris in the 13 state races with their confidence intervals, sorted by greatest to smallest predicted margin. Since I'm calculating the predicted win margin for the Democratic candidate, a negative win margin favors the Republican candidate. The black dot is the predicted win margin, with the blue dot (favoring Democrats) representing the upper bound and the red dot (favoring Republicans) representing the lower bound of the win margin.

<img src="{{< blogdown/postref >}}index_files/figure-html/state win margins prediction-1.png" width="960" />

New Hampshire, Virginia, and New Mexico have the highest predicted win margins for Harris. Close states include Arizona, Georgia, and North Carolina. Pennsylvania is higher on this chart than I would've expected — it currently sits in the middle of the pack with very similar margins to the other swing states of Michigan, Nevada, Wisconsin, and Minnesota.

Incorporating in the other states, here is this week's Electoral College map!

<img src="{{< blogdown/postref >}}index_files/figure-html/week 8 prediction map-1.png" width="960" />

Similar to the state prediction, I create another visualization to summarize the Electoral College prediction for this week. The dashed black line indicates 270 electoral votes, which is the number of votes required to win the Electoral College. 

<img src="{{< blogdown/postref >}}index_files/figure-html/state model prediction viz-1.png" width="960" />

## Conclusion
Once again, I predict that Harris will win both the national two-party popular vote and the Electoral College. We're less than 14 days away from the election, so I'm excited (and a little scared) to see how our predictions will shake out. Looking forward to putting together my final election prediction next week!
