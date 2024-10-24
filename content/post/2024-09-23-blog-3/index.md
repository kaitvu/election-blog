---
title: "Blog 3: Polling"
author: "Kaitlyn Vu"
date: '2024-09-22'
slug: "blog-3"
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
Public opinion polling is essential to understanding democratic discourse: polls measure the will of voters and help to promote election integrity. In this blog, I use both national and state-level polling data to predict election outcomes for the 2024 presidential election.



## Historical Polling Averages (2016-2024)
First, I examine overall trends in election-year polling averages. The following visualization contains three plots: the percentage of average poll approval for both the Republican and Democratic candidates are plotted by date for 2016 (March-November), 2020 (March-November), and 2024 (March-September). 

<img src="{{< blogdown/postref >}}index_files/figure-html/historical polling averages-1.png" width="960" />

In both 2016 and 2020, the Democratic candidate began the year polling higher than the Republican candidate. While the polling gap in 2016 tightened by mid-year, President Biden consistently maintained a polling advantage over former President Trump in 2020.

So far, trends in the polling data for 2024 are fascinating: heading into the summer, Trump narrowly led Biden in a contested race with about two percentage points separating the candidates. The script has clearly flipped since Vice President Harris entered the race: average poll approval for the Democratic candidate has largely surged past that of the Republican candidate. For both parties, average poll approval appears to have overall increased over time. 

## Polling Averages for 2024
To dive deeper into 2024, I create a plot of the polling averages by date with some potential "game-changers," which are events (e.g. party conventions) that *could* have an effect on voter behavior. The following plot only includes polling data from May to mid-September, since I want to focus on the presidential contest between Harris and Trump. 

<img src="{{< blogdown/postref >}}index_files/figure-html/poll averages 2024-1.png" width="960" />

Overall, it seems like polling changed little in the aftermath of these so-called "game-changers" with two notable exceptions: average poll approval diverged after the [first presidential debate](https://www.nytimes.com/2024/06/27/us/politics/biden-debate-democrats.html) in favor of the Republican candidate, and there was a massive spike in average poll approval for the Democratic candidate after Biden [ended his re-election bid](https://apnews.com/article/biden-drops-out-2024-election-ddffde72838370032bdcff946cfc2ce6). However, it is difficult to establish a direct causal relationship between the occurrence of such events and trends in public opinion. 

## Predicting 2024 National Two-Party Vote Share with Sept. Polling Averages
To incorporate polling data in a predictive model for the 2024 election, I use an ordinary least squares (OLS) regression model to analyze the relationship between national polling data from September of an election year and national two-party popular vote share, specifically for the Democratic candidate. In the model, I weighted the September polling data by the number of weeks remaining before the election. This adjustment accounts for the idea that polls taken closer to Election Day tend to be more predictive of voter behavior. 

This is a regression table for the Democratic candidate's national popular vote share and national polling in September for the presidential elections from 1948-2020. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for National Sept. Polling (1948-2020)</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">&nbsp;</th>
<th colspan="4" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">Democratic Candidate's National Popular Vote Share</th>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">23.14</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.88</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">21.40&nbsp;&ndash;&nbsp;24.87</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.60</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.02</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.56&nbsp;&ndash;&nbsp;0.64</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">420</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.678 / 0.677</td>
</tr>

</table>

From this table, we see that national polling in September is a relatively strong predictor of the Democratic candidate's share of the two-party popular vote. The R-squared values of approximately 0.68 suggest that the model is a good fit to the data. Similar to last week, it is important to note that utilizing in-sample model fit alone can contribute to overconfidence or over-fitting. 

Then, I utilize this model to predict the national two-party vote share for Harris in 2024. I take the weighted average of the national polling data from September: values from polls conducted closer to the election (fewer weeks left) have a higher impact on the overall average than polls taken earlier in the month.

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
   <td style="text-align:right;"> 51.99 </td>
   <td style="text-align:right;"> 37.62 </td>
   <td style="text-align:right;"> 66.36 </td>
  </tr>
</tbody>
</table>

This model predicts that Harris will receive about 52% of the national two-party popular vote in November. However, the wide range between the lower and upper bounds (37.62% to 66.36%) suggests that there's a significant amount of uncertainty in this prediction, which may be due to the variance in the underlying polling data. Another caveat of this prediction is that it does not include polling data for the entire month of September: there is only polling data available up to the date of this blog's writing (September 16, 2024).

## Predicting 2024 State Two-Party Vote Share with Sept. Polling Averages
I follow a similar series of steps to put together state-level predictions for the Democratic candidate's two-party vote share. First, I create an ordinary least squares (OLS) regression model for the relationship between state polling data from September of an election year and two-party popular vote share on the state level, and weight the model by weeks left before the election. I also narrow the year range to 2000-2020 to better reflect modern voter demographics, polling methodologies, and partisan alignments. 

This is a regression table for the Democratic candidate's state-level popular vote share and state-level polling in September for the presidential elections from 2000-2020.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for State Sept. Polling (2000-2020)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.52</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.26</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.02&nbsp;&ndash;&nbsp;2.02</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.09</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.01</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.08&nbsp;&ndash;&nbsp;1.10</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">8380</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.807 / 0.807</td>
</tr>

</table>

With an R-squared value of 0.81, this table suggests that state-level September polling is a strong predictor for the Democratic candidate's two-party popular vote share for that state.

I then use this regression model to predict Harris' share of the two-party popular vote on the state-level. Again, this prediction only includes polling data up to mid-September. Furthermore, the data set from FiveThirtyEight only includes polls from 15 states for the 2024 election cycle; it is of note, though, that the [seven key battleground states](https://www.bbc.com/news/articles/c511pyn3xw3o) for this year's election are included. The following table presents the predicted two-party vote share for Harris in 15 states.

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
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.52 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 30.33 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 74.72 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> California </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 66.37 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.17 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 88.56 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.61 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 28.42 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 72.81 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.17 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 30.97 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 75.37 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.41 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 31.21 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 75.60 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.88 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 33.68 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 78.07 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.77 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 30.57 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 74.96 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.07 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 34.87 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 79.27 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.92 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 30.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 75.11 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Ohio </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 48.20 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 26.01 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 70.40 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.20 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 31.00 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 75.39 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 49.80 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 27.61 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 72.00 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.79 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 33.60 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 77.99 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.56 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 32.36 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 76.75 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

The "Winner" column notes the winner of the state based on the predicted two-party popular vote share for Harris. This model therefore predicts that Harris will win 13 of the 15 states, including all seven key battleground states. That being said, it is important to note the prediction intervals, which indicate relatively high levels of uncertainty. Furthermore, the predicted two-party popular vote share for Harris for the majority of these states is quite close to 50% (e.g. Florida at 50.61%, Arizona at 52.52%), which suggest very closely contested races. Perhaps polling closer to the election will offer more precise estimates of this year's presidential election outcomes. 

## Conclusion
As I continue to build my predictive model for the 2024 presidential election, I think that it is important to incorporate the average of the most recent polls as a predictor. In the following weeks, I hope to begin creating a predictive model that includes both economic fundamentals (explored in last week's blog) and public opinion polling.
