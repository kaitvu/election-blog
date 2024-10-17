---
title: "Blog 7: The Ground Game"
author: "Kaitlyn Vu"
date: '2024-10-17'
slug: blog-7
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
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

## Introduction
From canvassing to phone banks, the second main aspect of presidential campaigns is the "ground game." The on-the-ground efforts of political organizing require a completely different set of infrastructure than the "air war" discussed in last week's blog: campaigns must work to identify and selectively target individual voters, while coordinating thousands of volunteers and field offices across the country. Former President Barack Obama's 2008 campaign against the late Senator John McCain is [widely considered](https://www.hks.harvard.edu/publications/groundbreakers-how-obamas-22-million-volunteers-transformed-campaigning-america) to have revolutionized the modern conceptualization of the ground game — we know that this side of the campaigning effects voting behavior to a certain extent. 

In this penultimate blog update, I first examine historical trends in "ground game" mobilization — specifically campaign events and field offices — across the 2012-2024 presidential elections. I pay particular attention to the states and geographical regions targeted by these campaigning efforts. Then, I transition to updating my models to predict the national two-party popular vote and the Electoral College for the quickly-approaching 2024 election. 



## Campaign Events 

Arguably, the "ground game" of campaigns is most visibility manifested in campaign events, including rallies, speeches, and town halls. To start, I examine the number of campaign events over time for the 2016, 2020, and 2024 (so far) presidential elections — the visualization is below.

<img src="{{< blogdown/postref >}}index_files/figure-html/campaign events over time-1.png" width="960" />

As expected, the number of campaign events for both parties increases over time. While 2016 and 2020 exhibit a sharp increase in campaign events approaching Election Day, the 2024 trend remains relatively flat with fewer events overall, particularly for the Republican candidate. 

I also map the location of these campaign events for each of the 3 election cycles. Each circle represents a campaign event, colored blue if hosted by the Democratic candidate and red for the Republican candidate.

<img src="{{< blogdown/postref >}}index_files/figure-html/campaign events maps-1.png" width="960" />

Looking at these maps, there seems to be a lot of geographic overlap in the locations that campaigns choose to host their events. Many campaign events take place in the Great Lakes region (near the "blue wall" states of Michigan and Wisconsin) as well as the Mid-Atlantic and southern states along the East Coast. The density of dots appears to be the highest and most geographically spread in 2016, which indicates a larger number of campaign events held over a greater number of states. In comparison, campaign events in 2024 seem to have concentrated in a handful of states so far, including Wisconsin, Michigan, Pennsylvania, Georgia, and Pennsylvania. 

The following table presents the number of campaign events in our 13 states of interest for 2024 over the past 3 presidential elections. The final row of the table displays the total number of events across all these states for each campaign. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;" colspan="1"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2016</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2020</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2024</div></th>
</tr>
  <tr>
   <th style="text-align:left;"> State </th>
   <th style="text-align:left;"> Clinton </th>
   <th style="text-align:left;"> Trump </th>
   <th style="text-align:left;"> Biden </th>
   <th style="text-align:left;"> Trump </th>
   <th style="text-align:left;"> Harris </th>
   <th style="text-align:left;"> Trump </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Arizona </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> 5 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Florida </td>
   <td style="text-align:left;"> 44 </td>
   <td style="text-align:left;"> 40 </td>
   <td style="text-align:left;"> 14 </td>
   <td style="text-align:left;"> 17 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Georgia </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 9 </td>
   <td style="text-align:left;"> 6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Michigan </td>
   <td style="text-align:left;"> 9 </td>
   <td style="text-align:left;"> 16 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 13 </td>
   <td style="text-align:left;"> 10 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Minnesota </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 2 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Nevada </td>
   <td style="text-align:left;"> 9 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Hampshire </td>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> 15 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Mexico </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 3 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> North Carolina </td>
   <td style="text-align:left;"> 24 </td>
   <td style="text-align:left;"> 32 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 14 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 10 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pennsylvania </td>
   <td style="text-align:left;"> 25 </td>
   <td style="text-align:left;"> 32 </td>
   <td style="text-align:left;"> 23 </td>
   <td style="text-align:left;"> 20 </td>
   <td style="text-align:left;"> 14 </td>
   <td style="text-align:left;"> 11 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Texas </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> 1 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Virginia </td>
   <td style="text-align:left;"> 8 </td>
   <td style="text-align:left;"> 22 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 1 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Wisconsin </td>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 12 </td>
   <td style="text-align:left;"> 10 </td>
   <td style="text-align:left;"> 8 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> TOTAL EVENTS </td>
   <td style="text-align:left;font-style: italic;"> 141 </td>
   <td style="text-align:left;font-style: italic;"> 196 </td>
   <td style="text-align:left;font-style: italic;"> 75 </td>
   <td style="text-align:left;font-style: italic;"> 103 </td>
   <td style="text-align:left;font-style: italic;"> 73 </td>
   <td style="text-align:left;font-style: italic;"> 57 </td>
  </tr>
</tbody>
</table>

By simply looking at the total events row, we see that the 2016 presidential election had the highest number of campaign events in these states. Former President Trump beat both Secretary Clinton and President Biden in terms of the volume of campaign events in these states for 2016 and 2020, although Vice President Harris holds a slight advantage in 2024 thus far. On the individual state level, it's interesting to note that neither candidate has hosted a campaign event in Florida for the 2024 electoral cycle, despite the high number of events in previous elections. Also, at this point in the cycle, the number of campaign events in Georgia has more than doubled from the 2020 election for both parties. Once again, the battleground states of Michigan, North Carolina, and Pennsylvania have attracted significant campaign attention across all 3 elections. 

I decided to take a closer look at [Pennsylvania](https://www.nbcnews.com/politics/2024-election/trump-harris-pennsylvania-battleground-visits-map-rcna175691), which is one of the most important battleground states in the 2024 contest. This is a county-level map of Pennsylvania, where the fill color of each county indicates the margin by which the Democratic or Republican candidate won that county in 2020 — a more intense blue or red symbolizes a wider margin of victory for the appropriate party. Over this map, I've also plotted the location of 2024 campaign events by party so far. Some of these circles are overlapped on top of each other — meaning that the candidates hosted events in the same city  — and that is represented by a darker blue/purple colored circle. 

<img src="{{< blogdown/postref >}}index_files/figure-html/pa map-1.png" width="672" />

So far, both 2024 candidates have hosted events in Philadelphia and Erie. I think it's important to examine campaign activity in the lighter colored counties, which indicates a narrower win margin in 2020. For example, the Harris campaign has hosted events in York county and Luzerne county (both won by Trump in 2020) and in Lehigh county and Northampton county (narrowly won by Biden in 2020). The Trump campaign has likewise hosted an event in the counties surrounding Philadelphia, which went for Biden in 2020. To some extent, this map is evidence that campaigns pay attention to previous election results to inform future campaign investments.

## Field Offices
Next, I survey past trends in the location and number of campaign field offices. We only have data on field offices for 2012 and 2016, so the geographical spread of field offices for those two election cycles is mapped below.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-1-1.png" width="960" />

The field offices follow a similar pattern as the campaign events, concentrating along the West/East coasts and the Great Lakes region. At face value, the density of offices seem quite similar across both elections, perhaps with less offices across both parties in 2016 relative to 2012. Notably, we see a clear growth of Republican field offices in Arizona from 2012 to 2016. 

The next table displays the number of field offices in the 13 states for the 2012 and 2016 presidential elections. Again, the final row of the table provides the total number of field offices across all these states for each campaign.   

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;" colspan="1"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2012</div></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">2016</div></th>
</tr>
  <tr>
   <th style="text-align:left;"> State </th>
   <th style="text-align:left;"> Obama </th>
   <th style="text-align:left;"> Romney </th>
   <th style="text-align:left;"> Clinton </th>
   <th style="text-align:left;"> Trump </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Arizona </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 18 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Florida </td>
   <td style="text-align:left;"> 104 </td>
   <td style="text-align:left;"> 48 </td>
   <td style="text-align:left;"> 69 </td>
   <td style="text-align:left;"> 23 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Georgia </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> 1 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Michigan </td>
   <td style="text-align:left;"> 28 </td>
   <td style="text-align:left;"> 24 </td>
   <td style="text-align:left;"> 27 </td>
   <td style="text-align:left;"> 22 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Minnesota </td>
   <td style="text-align:left;"> 12 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 13 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Nevada </td>
   <td style="text-align:left;"> 26 </td>
   <td style="text-align:left;"> 12 </td>
   <td style="text-align:left;"> 16 </td>
   <td style="text-align:left;"> 3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Hampshire </td>
   <td style="text-align:left;"> 22 </td>
   <td style="text-align:left;"> 9 </td>
   <td style="text-align:left;"> 26 </td>
   <td style="text-align:left;"> 6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> New Mexico </td>
   <td style="text-align:left;"> 13 </td>
   <td style="text-align:left;"> 8 </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> North Carolina </td>
   <td style="text-align:left;"> 54 </td>
   <td style="text-align:left;"> 24 </td>
   <td style="text-align:left;"> 35 </td>
   <td style="text-align:left;"> 8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pennsylvania </td>
   <td style="text-align:left;"> 54 </td>
   <td style="text-align:left;"> 25 </td>
   <td style="text-align:left;"> 57 </td>
   <td style="text-align:left;"> 12 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Texas </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Virginia </td>
   <td style="text-align:left;"> 61 </td>
   <td style="text-align:left;"> 29 </td>
   <td style="text-align:left;"> 33 </td>
   <td style="text-align:left;"> 6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Wisconsin </td>
   <td style="text-align:left;"> 69 </td>
   <td style="text-align:left;"> 24 </td>
   <td style="text-align:left;"> 40 </td>
   <td style="text-align:left;"> 13 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> TOTAL OFFICES </td>
   <td style="text-align:left;font-style: italic;"> 453 </td>
   <td style="text-align:left;font-style: italic;"> 203 </td>
   <td style="text-align:left;font-style: italic;"> 326 </td>
   <td style="text-align:left;font-style: italic;"> 112 </td>
  </tr>
</tbody>
</table>

Overall, the total number of field offices in these states seems to have dropped from 2012 to 2016. Exceptions include the increase in Republican field offices in Arizona (+18) and Georgia (+1), as well as the increase in Democratic field offices in Minnesota (+1), New Hampshire (+4), Pennsylvania (+3), and Texas (+2) — not significantly large increases.

## National Two-Party Popular Vote Model
I now transition to updating my national two-party popular vote prediction. For this week's national model, I exclude Q2 RDI quarterly growth and the national two-party percentage of voters included in Blog 6. Instead, I add the national October polling averages (weighted by weeks left before the election) as another coefficient. The regression table for this week's national popular vote share model is below. 

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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">30.87</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">3.75</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">22.22&nbsp;&ndash;&nbsp;39.52</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">GDP growth quarterly</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.45</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.17</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.07&nbsp;&ndash;&nbsp;0.83</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.025</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.21</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.28</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.87&nbsp;&ndash;&nbsp;0.45</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.484</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">oct poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.61</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.26</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.01&nbsp;&ndash;&nbsp;1.22</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>0.048</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">incumbent</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.00</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.27</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;1.94&nbsp;&ndash;&nbsp;3.93</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.456</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">13</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.891 / 0.836</td>
</tr>

</table>

The model has an R-squared value of 0.89 and R-squared adjusted value of 0.84, which suggests that it is a strong predictor for the incumbent party candidate’s national two-party popular vote share. Of note here is that Q2 GDP growth and October national polling averages are statistically significant predictors of the incumbent party candidate's vote share, while September polling averages and incumbent status are not statistically significant. Again, we only have data on polling averages up to the date of this blog's writing (October 17, 2024). I use this model to predict Harris' share of the national two-party popular vote. 

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
   <td style="text-align:right;"> 51.88 </td>
   <td style="text-align:right;"> 46.6 </td>
   <td style="text-align:right;"> 57.16 </td>
  </tr>
</tbody>
</table>

In a slight decrease from previous weeks, this model predicts that Harris will win the national two-party popular vote by approximately 51.9%. Perhaps this national model comes closer to conveying the tightly contested nature of this year's presidential election — for context, Biden defeated Trump 51.3% to 46.9% in 2020. The prediction intervals are also smaller here than the previous two weeks, which is a good sign. 

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> Candidate </th>
   <th style="text-align:right;"> Two-Party Popular Vote Share (%) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Kamala Harris </td>
   <td style="text-align:right;"> 51.88 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Donald Trump </td>
   <td style="text-align:right;"> 48.12 </td>
  </tr>
</tbody>
</table>


## State Two-Party Popular Vote Model & Electoral College Prediction
Next up is updating the state model. This week, I add campaign events data — the total number of events in a given state — to the state model from Blog 6. Since we only have campaign events data from 2016 on, this state-level model is limited to 2016-2020, which is important to keep in mind. The regression table for the Democratic candidate's state-level popular vote share follows.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">Regression Table for State Model (2016-2020)</caption>
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
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">2.28</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">2.46</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;2.60&nbsp;&ndash;&nbsp;7.16</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.356</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">sept poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.49</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.36</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;1.20&nbsp;&ndash;&nbsp;0.22</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.172</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">oct poll</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">1.52</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.34</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.85&nbsp;&ndash;&nbsp;2.20</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  "><strong>&lt;0.001</strong></td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">campaign events</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.01</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.07</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">&#45;0.13&nbsp;&ndash;&nbsp;0.15</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">0.940</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">Observations</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="4">96</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">R<sup>2</sup> / R<sup>2</sup> adjusted</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="4">0.820 / 0.814</td>
</tr>

</table>

In this model, only October state-level polling averages are a statistically significant predictor of the Democrat's state-level popular vote share. The R-squared value of 0.82 and adjusted R-squared value of 0.81 indicate that the model has a relatively good fit. Here is this model's 2024 prediction for our 13 states of interest:

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
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.37 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 41.18 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 59.56 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Florida </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 49.15 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 39.98 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 58.32 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Georgia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 50.80 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 41.58 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.02 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Michigan </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.61 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 42.32 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.89 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Minnesota </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.56 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.37 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 62.76 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Nevada </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 42.55 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.90 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Hampshire </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 54.75 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 45.53 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.97 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> New Mexico </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.79 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.57 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.00 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> North Carolina </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.05 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 41.83 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 60.28 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Pennsylvania </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.79 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 42.49 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.08 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Texas </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 47.74 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 38.56 </td>
   <td style="text-align:right;background-color: rgba(255, 209, 209, 255) !important;"> 56.91 </td>
   <td style="text-align:left;background-color: rgba(255, 209, 209, 255) !important;"> Trump </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Virginia </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 53.92 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 44.72 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 63.12 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
  <tr>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Wisconsin </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 51.76 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 42.51 </td>
   <td style="text-align:right;background-color: rgba(211, 229, 255, 255) !important;"> 61.02 </td>
   <td style="text-align:left;background-color: rgba(211, 229, 255, 255) !important;"> Harris </td>
  </tr>
</tbody>
</table>

This week's state model predicts that Harris will win 11 out of 13 states, while Trump wins Florida and Texas. Harris' margins of victory are smaller here (e.g. Michigan at 51.61% this week vs 52.93% in Blog 6), and the prediction intervals are slightly larger relative to last week. Personally, I feel a little more at ease that this model predicted Trump to win Florida — given the [current state](https://www.nytimes.com/interactive/2024/us/elections/polls-president-florida.html) of the polls, I doubt that Harris will be able to flip the state as last week's state model predicted. 

Adding back in the other states, we get the following Electoral College map for this week's model.

<img src="{{< blogdown/postref >}}index_files/figure-html/week 7 prediction map-1.png" width="960" />

Here is the predicted tally for the Electoral College votes!

<table class="table" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> Candidate </th>
   <th style="text-align:right;"> Electoral College Votes </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Kamala Harris </td>
   <td style="text-align:right;"> 319 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Donald Trump </td>
   <td style="text-align:right;"> 219 </td>
  </tr>
</tbody>
</table>

## Conclusion
Another week, another predicted presidential victory for Harris. A few thoughts moving into next week: I think that removing Q2 RDI growth in the national model was a good decision (in terms of its statistical insignificance and for the sake of reducing over-fitting), so that coefficient may not return for my final national model. For the state model, incorporating data on campaign events decreased the number of observations and only allowed me to train the model on 2 presidential elections. It could be argued here that narrowing down the state model to Trump-era races is productive, given that today's political environment is a very different world from that of the early 2000s. However, I'm not sure if I'll continue to incorporate campaign-related data into my models moving forward — they generally appear to be weaker predictors of vote share and tend to vary greatly from candidate to candidate. Onward!
