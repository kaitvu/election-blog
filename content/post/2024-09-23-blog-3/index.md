---
title: Blog 3
author: Kaitlyn Vu
date: '2024-09-18'
slug: blog-3
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
Public opinion polling is essential to understanding democratic discourse: polls measure the will of voters and help to promote election integrity. In this blog, I use both national and state-level polling data to predict presidential election outcomes for this November.



## Historical Polling Averages (2016-2024)
First, I examine overall trends in election-year polling averages. The following visualization contains three plots: the percentage of average poll approval for both the Republican and Democratic candidates are plotted by date for 2016 (March-November), 2020 (March-November), and 2024 (March-September). 

<img src="{{< blogdown/postref >}}index_files/figure-html/historical polling averages-1.png" width="960" />

In both 2016 and 2020, the Democratic candidate began the year polling higher than the Republican candidate. While the polling gap in 2016 tightened by mid-year, President Biden consistently maintained a polling advantage over former President Trump in 2020.

So far, trends in the polling data for 2024 are fascinating: heading into the summer, Trump narrowly led Biden in a very contested race. The script has clearly flipped since Vice President Harris entered the race — Democrats have surged back in the polls.

## Polling Averages for 2024
To dive deeper into 2024, I create a plot of the polling averages by date with some potential "game-changers," which are events (e.g. party conventions) that *could* have an effect on voter behavior. The following plot only includes polling data from May to mid-September, since I want to focus on the presidential contest between Harris and Trump. 

<img src="{{< blogdown/postref >}}index_files/figure-html/poll averages 2024-1.png" width="672" />

Overall, it seems like polling changed little in the aftermath of these so-called "game-changers" with two notable exceptions: average poll approval diverged after the [first presidential debate](https://www.nytimes.com/2024/06/27/us/politics/biden-debate-democrats.html) in favor of the Republican candidate, and there was a massive spike in average poll approval for the Democratic candidate after Biden [ended his re-election campaign](https://apnews.com/article/biden-drops-out-2024-election-ddffde72838370032bdcff946cfc2ce6). However, it is difficult to establish a direct causal relationship between such events and trends in public opinion. 

## Predicting 2024 National Two-Party Vote Share with Sept. Polling Averages
To incorporate polling data in a predictive model, I use an ordinary least squares (OLS) regression model to analyze the relationship between national polling data from September of an election year and national two-party popular vote share, specifically for the Democratic candidate. This is a regression table for the Democratic candidate's national popular vote share and national polling in September for the presidential elections from 1948-2020.

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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">23.39</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.88</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">21.66&nbsp;&ndash;&nbsp;25.12</td>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.676 / 0.675</td>
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
   <td style="text-align:right;"> 46.66 </td>
   <td style="text-align:right;"> 57.33 </td>
  </tr>
</tbody>
</table>

This model predicts that Harris will receive about 52% of the national two-party popular vote in November. However, a caveat of this prediction is that it does not include polling data for the entire month of September: there is only polling data available up to the date of this blog's writing.

## Predicting 2024 State Two-Party Vote Share with Sept. Polling Averages
I follow a similar series of steps to put together state-level predictions for the Democratic candidate's two-party vote share. First, I create an ordinary least squares (OLS) regression model for the relationship between state polling data from September of an election year and two-party popular vote share on the state level. I sourced state-level two-party popular vote data from the [Federal Election Commission](https://www.fec.gov/resources/cms-content/documents/federalelections2020.pdf) (see Appendix A). This is a regression table for the Democratic candidate's state-level popular vote share and state-level polling in September for the presidential elections from 1972-2020.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for State Sept. Polling (1972-2020)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;2.41</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.37</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;3.12&nbsp;&ndash;&nbsp;-1.69</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.01</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.09&nbsp;&ndash;&nbsp;1.12</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">2816</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.865 / 0.865</td>
</tr>

</table>

As evident by the high R-squared value, this table suggests that state-level September polling is a strong predictor for the Democrat candidate's two-party popular vote share for that state.

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
   <td style="text-align:left;"> Arizona </td>
   <td style="text-align:right;"> 49.24 </td>
   <td style="text-align:right;"> 41.87 </td>
   <td style="text-align:right;"> 56.60 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> California </td>
   <td style="text-align:right;"> 63.25 </td>
   <td style="text-align:right;"> 55.88 </td>
   <td style="text-align:right;"> 70.62 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Florida </td>
   <td style="text-align:right;"> 47.30 </td>
   <td style="text-align:right;"> 39.94 </td>
   <td style="text-align:right;"> 54.67 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Georgia </td>
   <td style="text-align:right;"> 49.89 </td>
   <td style="text-align:right;"> 42.53 </td>
   <td style="text-align:right;"> 57.26 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Michigan </td>
   <td style="text-align:right;"> 50.13 </td>
   <td style="text-align:right;"> 42.76 </td>
   <td style="text-align:right;"> 57.50 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Minnesota </td>
   <td style="text-align:right;"> 52.63 </td>
   <td style="text-align:right;"> 45.27 </td>
   <td style="text-align:right;"> 60.00 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Nevada </td>
   <td style="text-align:right;"> 49.48 </td>
   <td style="text-align:right;"> 42.12 </td>
   <td style="text-align:right;"> 56.85 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Hampshire </td>
   <td style="text-align:right;"> 53.84 </td>
   <td style="text-align:right;"> 46.47 </td>
   <td style="text-align:right;"> 61.21 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;"> North Carolina </td>
   <td style="text-align:right;"> 49.64 </td>
   <td style="text-align:right;"> 42.27 </td>
   <td style="text-align:right;"> 57.00 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Ohio </td>
   <td style="text-align:right;"> 44.86 </td>
   <td style="text-align:right;"> 37.50 </td>
   <td style="text-align:right;"> 52.23 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pennsylvania </td>
   <td style="text-align:right;"> 49.92 </td>
   <td style="text-align:right;"> 42.55 </td>
   <td style="text-align:right;"> 57.29 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Texas </td>
   <td style="text-align:right;"> 46.48 </td>
   <td style="text-align:right;"> 39.12 </td>
   <td style="text-align:right;"> 53.85 </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Virginia </td>
   <td style="text-align:right;"> 52.55 </td>
   <td style="text-align:right;"> 45.18 </td>
   <td style="text-align:right;"> 59.91 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Wisconsin </td>
   <td style="text-align:right;"> 51.30 </td>
   <td style="text-align:right;"> 43.93 </td>
   <td style="text-align:right;"> 58.66 </td>
   <td style="text-align:left;"> Harris </td>
  </tr>
</tbody>
</table>

The "Winner" column notes the winner of the state based on the predicted two-party popular vote share for Harris. This model therefore predicts that Harris will win 6 of the 15 included states, including the battleground states of Michigan, Minnesota, and Wisconsin. On the other hand, Trump is predicted to win the battleground states of Arizona, Georgia, Nevada, North Carolina, and Pennsylvania. It is important to note that the predicted two-party popular vote share for Harris for the majority of these states is quite close to 50% (e.g. Pennsylvania is 49.92), which suggests a very closely contested race. Perhaps polling closer to the election will offer more precise estimates of this year's presidential election outcomes. 

## Conclusion
As I continue to build my predictive model for the 2024 presidential election, I think that it is important to incorporate the average of the most recent polls as a predictor. In the following weeks, I hope to begin utilizing ensembling to create a predictive model that includes both economic fundamentals (explored in last week's blog) and public opinion polling.
