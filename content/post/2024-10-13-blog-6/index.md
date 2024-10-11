---
title: Blog 6
author: Kaitlyn Vu
date: '2024-10-09'
slug: blog-6
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
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
Turning the page on election "fundamentals," our course now turns to examining presidential campaigns and their impact on voter behavior. Campaigns capture the attention of thousands of voters across the country, helping them learn about political candidates and influence the electoral process. 

My blog this week focuses on the "air war" between campaigns: advertising has both the power to persuade and mobilize voters to the ballot box. First, I create a series of descriptive figures and tables to assess past trends in campaign ad spending on both the national and state levels. I then update my models to predict both the national two-party popular vote and the Electoral College for the upcoming 2024 election. 



## Examining Ad Spending in Past Presidential Elections

Before we get to predictions for 2024, let's take a look back at campaign ad spending in previous elections. The following visualization plots campaign ad spending by month for the presidential elections from 2000-2012. 

<img src="{{< blogdown/postref >}}index_files/figure-html/ad spending by month-1.png" width="1056" />

Unsurprisingly, campaigns increase their funding for ads closer to the election — ad expenditures increase over time for all four elections. It's important to note the scale of each individual plot here: Senator Mitt Romney's campaign surpasses 15 million in ad spending by November 2012, which is significantly higher than the maximum spending of the three previous elections (2 million in 2000, 6 million in 2004, and 3 million in 2008).

However, does increased ad spending translate into an electoral advantage for the candidate with more air time? Focusing on the 13 potential toss-up states for the 2024 election (from last week's blog), I identify the candidate with the higher state-level ad spending from the 2004, 2008, and 2012 presidential elections. The "match" column indicates whether or not that candidate with the higher state-level ad spending won the state. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;" colspan="1"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2004</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2008</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2012</div></th>
</tr>
  <tr>
   <th style="text-align:left;"> State </th>
   <th style="text-align:left;"> Spending Advantage </th>
   <th style="text-align:left;"> Match </th>
   <th style="text-align:left;"> Spending Advantage </th>
   <th style="text-align:left;"> Match </th>
   <th style="text-align:left;"> Spending Advantage </th>
   <th style="text-align:left;"> Match </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Arizona </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Florida </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Georgia </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Michigan </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Minnesota </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Nevada </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Hampshire </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Mexico </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> North Carolina </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pennsylvania </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Texas </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Virginia </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Wisconsin </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Democrat </td>
   <td style="text-align:left;background-color: rgba(168, 230, 207, 255) !important;"> Yes </td>
   <td style="text-align:left;"> Republican </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> No </td>
  </tr>
</tbody>
</table>

As we can see in this table, candidates that spent the most on ads in the 13 selected states did not always end up carrying that state. This correlation (at face value) appears to the strongest in the 2008 contest, where the candidate with the state-level spending advantage won 11 out of 13 states; That's a much better performance than the 2004 (4 out of 13) and 2012 presidential elections (5 out of 13).

Looking at 2020, this table presents at the number of campaign ad airings between April and September in each of the 13 states, arranged from the greatest to lowest total cost. The table also indicates which candidate had the air advantage (greater number of aired ads), as well as who ultimately won the state.

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> State </th>
   <th style="text-align:right;"> Biden Airings </th>
   <th style="text-align:right;"> Trump Airings </th>
   <th style="text-align:right;"> Total Cost </th>
   <th style="text-align:left;"> Air Advantage </th>
   <th style="text-align:left;"> State Winner </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Florida </td>
   <td style="text-align:right;"> 112982 </td>
   <td style="text-align:right;"> 77756 </td>
   <td style="text-align:right;"> 137821820 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pennsylvania </td>
   <td style="text-align:right;"> 89612 </td>
   <td style="text-align:right;"> 62292 </td>
   <td style="text-align:right;"> 95155100 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> North Carolina </td>
   <td style="text-align:right;"> 52045 </td>
   <td style="text-align:right;"> 57299 </td>
   <td style="text-align:right;"> 66771000 </td>
   <td style="text-align:left;"> Trump </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Wisconsin </td>
   <td style="text-align:right;"> 69132 </td>
   <td style="text-align:right;"> 51951 </td>
   <td style="text-align:right;"> 56274430 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Arizona </td>
   <td style="text-align:right;"> 48401 </td>
   <td style="text-align:right;"> 35802 </td>
   <td style="text-align:right;"> 55601590 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Michigan </td>
   <td style="text-align:right;"> 73510 </td>
   <td style="text-align:right;"> 25243 </td>
   <td style="text-align:right;"> 47117340 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Georgia </td>
   <td style="text-align:right;"> 245 </td>
   <td style="text-align:right;"> 37378 </td>
   <td style="text-align:right;"> 19280010 </td>
   <td style="text-align:left;"> Trump </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Minnesota </td>
   <td style="text-align:right;"> 16424 </td>
   <td style="text-align:right;"> 11546 </td>
   <td style="text-align:right;"> 15349730 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Nevada </td>
   <td style="text-align:right;"> 13527 </td>
   <td style="text-align:right;"> 6492 </td>
   <td style="text-align:right;"> 7709440 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Texas </td>
   <td style="text-align:right;"> 731 </td>
   <td style="text-align:right;"> 606 </td>
   <td style="text-align:right;"> 707840 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Mexico </td>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:right;"> 1024 </td>
   <td style="text-align:right;"> 200380 </td>
   <td style="text-align:left;"> Trump </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Hampshire </td>
   <td style="text-align:right;"> 167 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 190010 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Virginia </td>
   <td style="text-align:right;"> 32 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 3920 </td>
   <td style="text-align:left;"> Biden </td>
   <td style="text-align:left;"> Biden </td>
  </tr>
</tbody>
</table>

There are only 4 cases here where the candidate with the air advantage went on to lose the state: President Biden had the air advantage in both Trump-won Texas and Florida, while Trump had the air advantage in Biden-won Georgia and New Mexico. 

Notably, Florida (138 million), Pennsylvania (95 million), and North Carolina (66 million) have the highest total ad spending between April and September 2020. How has total ad spending in these 13 states changed over time? The next line plot visualizes trends in total costs of ad campaigns over 5 presidential elections (2000, 2004, 2008, 2012, 2020). We do not have access to data from 2016, so spending in that election year is omitted.

<img src="{{< blogdown/postref >}}index_files/figure-html/ad costs by state-1.png" width="1056" />

First and foremost, total ad spending in Florida has been on a strong upward trend since 2008 — candidates put the most money into Floridian ads in 2004, 2012, and 2020. It's also interesting to note the states that have increased in total ad spending from 2012 to 2020, mainly Pennsylvania, North Carolina, Wisconsin, Arizona, Minnesota, and Nevada in addition to Florida. Those states now comprise our core battleground states, which makes sense why candidates are increasingly investing in ads aired there. 

Although we do not yet have access to full campaign ad spending for the 2024 election, CNN [reports](https://www.cnn.com/2024/10/08/politics/2024-election-most-expensive/index.html) that this year’s spending to elect a president and members of Congress will hit at least 15.9 billion USD — the nation’s most expensive federal election to date. Campaign ad spending is only expected to [pick up](https://www.nytimes.com/2024/09/17/us/elections/presidential-campaign-advertising-spending.html) as we near the election: groups backing Vice President Harris have reserved 332 million USD worth of airtime for TV and radio ads, compared to about 194 million USD from Trump's supporters. The spending race in the swing states is particularly interesting to track as the Harris campaign is [set to spend](https://www.axios.com/2024/08/03/trump-harris-pennsylvania-ad-spending-president) 109.2 million USD to the Trump campaign's 101.7 million USD in Pennsylvania alone.

## National Two-Party Popular Vote Model

Next, I shift back to updating my electoral predictions for the national two-party popular vote share. Building upon my model, I add a new variable to the regression: the national two-party percentage of voters. We [know](https://link.springer.com/article/10.1007/s11109-022-09816-z) that partisan affiliation is a strong demographic predictor of turnout and voting behavior, which is why I wanted to include it in my model. This data set was kindly put together using data from Pew Research Center and Gallup by my incredible classmate, Alex Heuss! The regression table for the new national popular vote share model is below. 

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for National Model (2000-2016)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">28.61</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">6.95</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">12.18&nbsp;&ndash;&nbsp;45.04</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.004</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.68</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.24</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.12&nbsp;&ndash;&nbsp;1.25</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.024</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">RDPI growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.54</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.32</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;1.29&nbsp;&ndash;&nbsp;0.22</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.135</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.43</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.11</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.18&nbsp;&ndash;&nbsp;0.68</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.005</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">two party percent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.04</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.08</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.15&nbsp;&ndash;&nbsp;0.24</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.602</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">incumbent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.24</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.50</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;3.31&nbsp;&ndash;&nbsp;3.79</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.875</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">13</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.881 / 0.797</td>
</tr>

</table>

With an R-squared value of 0.88, this table suggests that my model is a strong predictor for the incumbent party candidate’s national two-party popular vote share. That being said, Q2 GDP quarterly growth and September national polling averages are the key predictors in this model; the Q2 RDI quarterly growth, national two-party percentage, and incumbent status coefficients are not statistically significant, indicating the lack of a clear effect on the incumbent party's vote share in this model. I then use this regression model to predict Harris' share of the national two-party popular vote. 

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
   <td style="text-align:right;"> 53.29 </td>
   <td style="text-align:right;"> 46.86 </td>
   <td style="text-align:right;"> 59.72 </td>
  </tr>
</tbody>
</table>

Here, Harris is predicted to win the national two-party popular vote by 53.3%. This is consistent with the results from my previous blogs, which all have Harris winning approximately 53% of the popular vote. Notably, however, this week's prediction intervals are slightly larger than those of the last two weeks' predictions. Going forward, I may simplify my national model by focusing solely on Q2 GDP quarterly growth and September polling averages, which may help to reduce over-fitting or noise.

## State Two-Party Popular Vote Model & Electoral College Prediction

I now make my Electoral College prediction for this week. To do so, I adapt the model I've used to predict the Democratic candidate's state two-party vote share in previous weeks: I add October state-level polling averages as another coefficient in my mostly poll-based state model. This is a regression table for the Democratic candidate's state-level popular vote share and state-level polling averages in both September and October (weighted by weeks left before the election) for the presidential elections from 2000-2020.

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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.27</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.10</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;2.43&nbsp;&ndash;&nbsp;1.90</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.810</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.35</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.15</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.64&nbsp;&ndash;&nbsp;-0.06</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.018</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">oct poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.46</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.14</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.18&nbsp;&ndash;&nbsp;1.73</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">291</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.882 / 0.881</td>
</tr>

</table>

Once again, the relatively high R-squared values of 0.88 suggest that state-level September and October polling are strong predictors for the Democratic candidate’s two-party popular vote share for that state. More specifically, the model shows that October polling is a strong and significant predictor of the Democrat's state-level popular vote share, while September polling has a smaller, negative effect. The prediction for 2024 follows.

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
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.51 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.59 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.43 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.47 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 43.56 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 57.38 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.85 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.93 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 58.77 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.93 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 46.01 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.84 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.87 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 47.94 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.79 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.93 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 46.01 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.84 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 56.26 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 49.33 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.18 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Mexico </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.27 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.35 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 62.19 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.25 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.34 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.17 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 52.86 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.95 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.78 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 48.76 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 41.85 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 55.68 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 55.01 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 48.09 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.94 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.31 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 46.39 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.23 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

Again focusing on the 13 "competitive" races, the model predicts that Harris will win 12 out of the 13 states, while Trump only wins Texas. This is the same finding as the first run of the state model from last week's blog, although the prediction intervals are slightly smaller with overall lower predictions (e.g. last week's model predicted Harris to win Georgia at 53.20% vs 51.85% this week). This week's inclusion of October polling averages may suggest focusing more on late-stage polling when making predictions. Again, I've only included October polling data up to the writing of this blog (October 10, 2024). 

I also visualize my state-level predictions in a potential Electoral College map. Incorporating back in the other states (excluded as they are confident calls for either Harris or Trump), I get the following map!

<img src="{{< blogdown/postref >}}index_files/figure-html/week 6 prediction map-1.png" width="672" />

More concisely, here are the tallied Electoral College votes for both candidates using this week's state model. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> Candidate </th>
   <th style="text-align:right;"> Electoral College Votes </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Donald Trump </td>
   <td style="text-align:right;"> 189 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Kamala Harris </td>
   <td style="text-align:right;"> 349 </td>
  </tr>
</tbody>
</table>

## Conclusion

Once more, Harris is predicted to win both the national two-party popular vote and the Electoral College (by a margin of 349-189). I remain unconvinced that Harris will win Florida, but the rest of the state predictions seem quite plausible to me — especially given the close nature of all the swing state races. Perhaps I'll turn to simplifying my models in the handful of blogs that remain. Additionally, I really enjoyed diving deeper into past campaign ad spending and the "air war" this week. 
