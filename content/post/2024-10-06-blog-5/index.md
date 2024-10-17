---
title: "Blog 5: Demographics"
author: "Kaitlyn Vu"
date: '2024-10-06'
slug: "blog-5"
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
Defined as group level characteristics that can be attached to individuals, campaigns often look to demographics to inform predictions of election outcomes — including the likelihood of candidate support and turnout — and determine which populations to target with their limited resources. As such, demographic conformity is almost an expected norm: individuals are expected to vote in line with their perceived group interests. 

However, are demographics truly predictive of vote choice? A 2024 paper by Seo-young Silvia Kim and Jan Zilinsky [found](https://link.springer.com/article/10.1007/s11109-022-09816-z) that the accuracy for vote choice predictions is generally low (< 65%) when using just demographics. In this blog, I aim to apply demographics to my state-level popular vote model from Blog 3 to assess its predictive effects. I also use recent polling data to update last week's combined model for the incumbent party candidate's national popular vote share. 



## Examining Demographics for 2024 Voter File Samples
One of the ways in which campaigns measure individual-level demographics is through state voter files. Before applying demographics to my predictive models, I wanted to take a closer look at the 2024 voter file data that [Statara](https://statara.com/) graciously provided to our class. Thank you to our excellent TF Matthew Dardet, who initially cleaned these voter files and took a 1% sample from each state's 2024 voter file. I work with those 1% samples here.

In particular, I examine demographic data from 13 states: these states have all been designated as either "Lean/Likely Democrat," "Lean/Likely Republican," or "Toss Up" in the 2024 state-level predictions from Cook Political Report and Sabato's Crystal Ball, which were the expert models examined last week. I exclude NE-02 and ME-02 as data on the congressional district level was difficult to obtain. Assuming that states designated as "Safe/Solid Democrat" or "Safe/Solid Republican" by these expert models are confident calls for their respective parties, we should look at these 13 states to try to predict where their electoral votes will end up. 

The descriptive table of demographics — specifically registered party, gender, and race — from those 13 state voter file samples is below.

<div style="border: 1px solid #ddd; padding: 0px; overflow-y: scroll; height:auto; overflow-x: scroll; width:100%; "><table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;position: sticky; top:0; background-color: #FFFFFF;" colspan="1"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; position: sticky; top:0; background-color: #FFFFFF;" colspan="5"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">REGISTERED PARTY</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; position: sticky; top:0; background-color: #FFFFFF;" colspan="3"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">GENDER</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; position: sticky; top:0; background-color: #FFFFFF;" colspan="6"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">RACE</div></th>
</tr>
  <tr>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> State </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Democrat </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Republican </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Unaffiliated/ Independent </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Unregistered </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Other Party </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Male </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Female </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Other Gender </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> African-American </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Asian </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Non-Hispanic White </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Hispanic </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Native American </th>
   <th style="text-align:left;position: sticky; top:0; background-color: #FFFFFF;"> Other Race </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Arizona </td>
   <td style="text-align:left;"> 21.13 </td>
   <td style="text-align:left;"> 24.68 </td>
   <td style="text-align:left;"> 27.78 </td>
   <td style="text-align:left;"> 25.80 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.61 </td>
   <td style="text-align:left;"> 47.60 </td>
   <td style="text-align:left;"> 48.90 </td>
   <td style="text-align:left;border-right:1px solid;"> 3.49 </td>
   <td style="text-align:left;"> 2.18 </td>
   <td style="text-align:left;"> 2.40 </td>
   <td style="text-align:left;"> 70.29 </td>
   <td style="text-align:left;"> 21.06 </td>
   <td style="text-align:left;"> 1.15 </td>
   <td style="text-align:left;"> 2.92 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Florida </td>
   <td style="text-align:left;"> 23.55 </td>
   <td style="text-align:left;"> 26.79 </td>
   <td style="text-align:left;"> 23.31 </td>
   <td style="text-align:left;"> 26.09 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.26 </td>
   <td style="text-align:left;"> 48.00 </td>
   <td style="text-align:left;"> 50.97 </td>
   <td style="text-align:left;border-right:1px solid;"> 1.03 </td>
   <td style="text-align:left;"> 12.58 </td>
   <td style="text-align:left;"> 2.22 </td>
   <td style="text-align:left;"> 61.84 </td>
   <td style="text-align:left;"> 18.93 </td>
   <td style="text-align:left;"> 0.24 </td>
   <td style="text-align:left;"> 4.18 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Georgia </td>
   <td style="text-align:left;"> 0.83 </td>
   <td style="text-align:left;"> 0.51 </td>
   <td style="text-align:left;"> 75.81 </td>
   <td style="text-align:left;"> 22.83 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.02 </td>
   <td style="text-align:left;"> 47.42 </td>
   <td style="text-align:left;"> 51.79 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.79 </td>
   <td style="text-align:left;"> 29.16 </td>
   <td style="text-align:left;"> 3.16 </td>
   <td style="text-align:left;"> 52.18 </td>
   <td style="text-align:left;"> 5.09 </td>
   <td style="text-align:left;"> 0.62 </td>
   <td style="text-align:left;"> 9.79 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Michigan </td>
   <td style="text-align:left;"> 0.29 </td>
   <td style="text-align:left;"> 0.20 </td>
   <td style="text-align:left;"> 79.25 </td>
   <td style="text-align:left;"> 20.25 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.00 </td>
   <td style="text-align:left;"> 49.22 </td>
   <td style="text-align:left;"> 50.12 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.66 </td>
   <td style="text-align:left;"> 11.87 </td>
   <td style="text-align:left;"> 2.32 </td>
   <td style="text-align:left;"> 80.76 </td>
   <td style="text-align:left;"> 2.63 </td>
   <td style="text-align:left;"> 0.12 </td>
   <td style="text-align:left;"> 2.30 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Minnesota </td>
   <td style="text-align:left;"> 0.47 </td>
   <td style="text-align:left;"> 0.29 </td>
   <td style="text-align:left;"> 71.54 </td>
   <td style="text-align:left;"> 27.69 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.01 </td>
   <td style="text-align:left;"> 48.76 </td>
   <td style="text-align:left;"> 48.34 </td>
   <td style="text-align:left;border-right:1px solid;"> 2.91 </td>
   <td style="text-align:left;"> 3.36 </td>
   <td style="text-align:left;"> 3.71 </td>
   <td style="text-align:left;"> 88.05 </td>
   <td style="text-align:left;"> 2.13 </td>
   <td style="text-align:left;"> 0.28 </td>
   <td style="text-align:left;"> 2.47 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Nevada </td>
   <td style="text-align:left;"> 22.61 </td>
   <td style="text-align:left;"> 21.04 </td>
   <td style="text-align:left;"> 31.68 </td>
   <td style="text-align:left;"> 23.97 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.70 </td>
   <td style="text-align:left;"> 48.27 </td>
   <td style="text-align:left;"> 46.68 </td>
   <td style="text-align:left;border-right:1px solid;"> 5.05 </td>
   <td style="text-align:left;"> 7.22 </td>
   <td style="text-align:left;"> 5.77 </td>
   <td style="text-align:left;"> 62.73 </td>
   <td style="text-align:left;"> 20.39 </td>
   <td style="text-align:left;"> 0.18 </td>
   <td style="text-align:left;"> 3.71 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> New Hampshire </td>
   <td style="text-align:left;"> 21.53 </td>
   <td style="text-align:left;"> 20.75 </td>
   <td style="text-align:left;"> 27.95 </td>
   <td style="text-align:left;"> 29.72 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.04 </td>
   <td style="text-align:left;"> 47.94 </td>
   <td style="text-align:left;"> 49.81 </td>
   <td style="text-align:left;border-right:1px solid;"> 2.25 </td>
   <td style="text-align:left;"> 0.27 </td>
   <td style="text-align:left;"> 1.38 </td>
   <td style="text-align:left;"> 94.30 </td>
   <td style="text-align:left;"> 1.71 </td>
   <td style="text-align:left;"> 0.03 </td>
   <td style="text-align:left;"> 2.31 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> New Mexico </td>
   <td style="text-align:left;"> 30.46 </td>
   <td style="text-align:left;"> 22.62 </td>
   <td style="text-align:left;"> 18.69 </td>
   <td style="text-align:left;"> 27.04 </td>
   <td style="text-align:left;border-right:1px solid;"> 1.19 </td>
   <td style="text-align:left;"> 47.70 </td>
   <td style="text-align:left;"> 51.47 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.84 </td>
   <td style="text-align:left;"> 0.68 </td>
   <td style="text-align:left;"> 1.19 </td>
   <td style="text-align:left;"> 52.02 </td>
   <td style="text-align:left;"> 38.52 </td>
   <td style="text-align:left;"> 3.80 </td>
   <td style="text-align:left;"> 3.79 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> North Carolina </td>
   <td style="text-align:left;"> 22.96 </td>
   <td style="text-align:left;"> 21.89 </td>
   <td style="text-align:left;"> 28.92 </td>
   <td style="text-align:left;"> 25.77 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.46 </td>
   <td style="text-align:left;"> 47.17 </td>
   <td style="text-align:left;"> 51.66 </td>
   <td style="text-align:left;border-right:1px solid;"> 1.17 </td>
   <td style="text-align:left;"> 18.71 </td>
   <td style="text-align:left;"> 1.96 </td>
   <td style="text-align:left;"> 64.55 </td>
   <td style="text-align:left;"> 4.88 </td>
   <td style="text-align:left;"> 0.65 </td>
   <td style="text-align:left;"> 9.26 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Pennsylvania </td>
   <td style="text-align:left;"> 32.31 </td>
   <td style="text-align:left;"> 29.29 </td>
   <td style="text-align:left;"> 11.60 </td>
   <td style="text-align:left;"> 26.36 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.44 </td>
   <td style="text-align:left;"> 47.68 </td>
   <td style="text-align:left;"> 51.00 </td>
   <td style="text-align:left;border-right:1px solid;"> 1.32 </td>
   <td style="text-align:left;"> 8.46 </td>
   <td style="text-align:left;"> 2.68 </td>
   <td style="text-align:left;"> 82.19 </td>
   <td style="text-align:left;"> 4.30 </td>
   <td style="text-align:left;"> 0.04 </td>
   <td style="text-align:left;"> 2.33 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Texas </td>
   <td style="text-align:left;"> 0.43 </td>
   <td style="text-align:left;"> 0.51 </td>
   <td style="text-align:left;"> 71.01 </td>
   <td style="text-align:left;"> 28.04 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.02 </td>
   <td style="text-align:left;"> 47.37 </td>
   <td style="text-align:left;"> 49.45 </td>
   <td style="text-align:left;border-right:1px solid;"> 3.18 </td>
   <td style="text-align:left;"> 10.16 </td>
   <td style="text-align:left;"> 4.33 </td>
   <td style="text-align:left;"> 52.37 </td>
   <td style="text-align:left;"> 29.87 </td>
   <td style="text-align:left;"> 0.07 </td>
   <td style="text-align:left;"> 3.20 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Virginia </td>
   <td style="text-align:left;"> 0.94 </td>
   <td style="text-align:left;"> 0.59 </td>
   <td style="text-align:left;"> 75.50 </td>
   <td style="text-align:left;"> 22.94 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.03 </td>
   <td style="text-align:left;"> 47.51 </td>
   <td style="text-align:left;"> 51.56 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.93 </td>
   <td style="text-align:left;"> 15.47 </td>
   <td style="text-align:left;"> 5.48 </td>
   <td style="text-align:left;"> 71.07 </td>
   <td style="text-align:left;"> 5.16 </td>
   <td style="text-align:left;"> 0.04 </td>
   <td style="text-align:left;"> 2.78 </td>
  </tr>
  <tr>
   <td style="text-align:left;border-right:1px solid;"> Wisconsin </td>
   <td style="text-align:left;"> 0.19 </td>
   <td style="text-align:left;"> 0.17 </td>
   <td style="text-align:left;"> 87.08 </td>
   <td style="text-align:left;"> 12.55 </td>
   <td style="text-align:left;border-right:1px solid;"> 0.01 </td>
   <td style="text-align:left;"> 46.70 </td>
   <td style="text-align:left;"> 50.55 </td>
   <td style="text-align:left;border-right:1px solid;"> 2.75 </td>
   <td style="text-align:left;"> 4.99 </td>
   <td style="text-align:left;"> 1.61 </td>
   <td style="text-align:left;"> 88.44 </td>
   <td style="text-align:left;"> 3.24 </td>
   <td style="text-align:left;"> 0.24 </td>
   <td style="text-align:left;"> 1.48 </td>
  </tr>
</tbody>
</table></div>

Notably, I find the information on registered party especially interesting. In most of these voter file samples, the majority of individuals are registered as either "Unaffiliated/Independent" or did not register a party. It is important to note, however, voters in some states register [without reference to party](https://centerforpolitics.org/crystalball/registering-by-party-where-the-democrats-and-republicans-are-ahead/). These voter file samples are also fairly balanced between genders. As expected, non-Hispanic White voters comprise the largest percentage of the voter file samples compared to other racial categories.

## Revisiting Blog 3's State Sept. Polling Averages Model
To predict state-level outcomes and ultimately the Electoral College, I start by updating my state-level popular vote share model from Blog 3 with new polling data; I now have polling data for the entire month of September. 

This is a regression table for the Democratic candidate's state-level popular vote share and state-level polling averages in September (weighted by weeks left before the election) for the presidential elections from 2000-2020.

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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.15</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.28</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;2.68&nbsp;&ndash;&nbsp;2.37</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.904</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.13</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.03</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.07&nbsp;&ndash;&nbsp;1.19</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">291</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.839 / 0.838</td>
</tr>

</table>

With an R-squared value of 0.84, this table suggests that state-level September polling is a strong predictor for the Democratic candidate’s two-party popular vote share for that state. Like Blog 3, I then use this regression model to predict Vice President Harris' share of the two-party popular vote at the state-level. 

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
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.69 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.63 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.75 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.92 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 42.86 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.98 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.20 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.14 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.26 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.90 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.84 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.96 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.09 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.02 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 64.16 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.10 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.04 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.16 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.48 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 49.41 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 65.55 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Mexico </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.49 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.42 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 64.56 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.15 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.09 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.22 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.67 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.61 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.74 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 49.84 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 41.78 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 57.90 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.14 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.07 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 64.20 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 46.66 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 62.79 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

This model predicts that Harris will win 12 out of the 13 states — including all 7 key battleground states — while Trump only wins Texas under this model. Of note: the numbers here are quite similar to those predicted a few weeks ago in Blog 3, although with smaller prediction intervals. This indicates that there is less uncertainty, which makes sense given that we are now closer to November 5, 2024. However, many of these races remain contested as the predicted two-party popular vote share for Harris is quite close to 50% (e.g. Nevada at 53.10%, Arizona at 52.69%). With this model, Harris would carry the Electoral College by a margin of **319** to former President Trump's **219**. 

## Adding Demographics to the State Sept. Polling Averages Model
I now turn to incorporating demographics data — specifically race — into my September polling averages model. To do so, I created a new ordinary least squares (OLS) regression model using past state-level September polling averages and demographics data on race from the U.S. Census for 2000-2020. The regression table is below. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for State Sept. Polling & Race (2000-2020)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;19.86</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">5.92</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;31.51&nbsp;&ndash;&nbsp;-8.21</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.09</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.03</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.03&nbsp;&ndash;&nbsp;1.15</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">non hispanic white</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.21</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.06</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.10&nbsp;&ndash;&nbsp;0.33</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">african american</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.18</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.06</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.06&nbsp;&ndash;&nbsp;0.30</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.004</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">hispanic</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.50</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.29&nbsp;&ndash;&nbsp;0.71</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">asian</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.53</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.12</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.31&nbsp;&ndash;&nbsp;0.76</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">native american</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.18</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.12</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.06&nbsp;&ndash;&nbsp;0.42</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.133</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">291</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.857 / 0.854</td>
</tr>

</table>

Similarly, the R-squared values of approximately 0.85 indicate a relatively good fit for the model. Here, September polling averages are the strongest predictor of the Democratic candidate's state-level two-party popular vote share with the race category coefficients as weaker predictors in comparison. 

I input the race data from the 2024 voter file samples to create state-level predictions of Harris' two-party popular vote share for the upcoming election.

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
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.57 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.53 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 66.61 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.57 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.65 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.49 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.28 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.58 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.98 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.25 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 46.57 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.92 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.93 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 49.23 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 64.63 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.52 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.47 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 67.58 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.56 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 49.85 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 65.27 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Mexico </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 66.63 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.78 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 75.48 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.29 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.63 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.96 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.74 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.06 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 62.43 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.65 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.20 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 67.10 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.90 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.18 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 65.61 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.41 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.11 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

This model seems to be a bit more optimistic regarding Harris' prospects: the Vice President's two-party vote share in each state is greater than the previous model. However, some of these results appear counter-intuitive at face value. For example, this model predicts that Harris will win both Texas and Florida — both of which have been won by the Republican candidate in recent elections — by 58.62% and 55.45%, respectively. Of course, we have to take into account the wide prediction intervals, but these results seem unlikely with just face validity. Perhaps, then, the demographic variables included in this model overestimate the potential gains for Harris in some of these states. With this model, Harris would carry the Electoral College by a margin of **389** to Trump's **149**. 

## Updating Last Week's National Popular Vote Share Model
Lastly, I also update the incumbent party candidate's national popular vote share model from Blog 4 with the recent September polling data. The following regression table is copied from last week's blog. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for Combined Model (1968-2016)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">31.62</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">4.03</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">22.33&nbsp;&ndash;&nbsp;40.91</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.67</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.23</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.15&nbsp;&ndash;&nbsp;1.19</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.018</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">RDPI growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.58</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.29</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;1.26&nbsp;&ndash;&nbsp;0.10</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.083</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.42</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.10</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.19&nbsp;&ndash;&nbsp;0.65</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.003</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">incumbent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.05</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.39</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;3.16&nbsp;&ndash;&nbsp;3.26</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.972</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">13</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.876 / 0.815</td>
</tr>

</table>

This model is then utilized to predict Harris' expected share of the national two-party popular vote. Similar to last week, the combined model of economic fundamentals and national September polling averages predicts that Harris will win by approximately 53.4%. The numbers here are quite similar to the ones from Blog 4, changing by a few decimal points.

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
   <td style="text-align:right;"> 53.44 </td>
   <td style="text-align:right;"> 47.49 </td>
   <td style="text-align:right;"> 59.4 </td>
  </tr>
</tbody>
</table>

## Conclusion
In line with my other blogs, the models in this week's entry anticipate that Harris will win both the national two-party popular vote as well as obtain the 270 electoral votes required to win the Electoral College. However, my attempt at incorporating demographics in my state-level predictive model produced unexpected — and seemingly unlikely — election outcomes, which is a source of growth for future work. As such, I'm eager keep developing my predictions for the national popular vote and the Electoral College and look forward to learning about campaign-focused factors in the coming weeks.
