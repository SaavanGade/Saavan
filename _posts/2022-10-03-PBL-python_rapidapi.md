---
keywords: fastai
description: APIs can be found all over the internet.  A great consolidator of many APIs is <mark>RapidAPI</mark>.  In this blog we will use a site to consolidates API stats.  Learning a few lines of code and you can start extracting lots of data from the internet via APIs.  
title: Python RapidAPI
toc: true
image: /images/rapidapi.png
permalink: /techtalk/rapidapi
categories: [1.A, 5.B, 5.D]
tags: [api, rapidapi]
type: pbl
week: 7
nb_path: _notebooks/2022-10-03-PBL-python_rapidapi.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2022-10-03-PBL-python_rapidapi.ipynb
-->

<div class="container" id="notebook-container">
        
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="sd">&quot;&quot;&quot;</span>
<span class="sd">Requests is a HTTP library for the Python programming language. </span>
<span class="sd">The goal of the project is to make HTTP requests simpler and more human-friendly. </span>
<span class="sd">&quot;&quot;&quot;</span>
<span class="kn">import</span> <span class="nn">requests</span>

<span class="sd">&quot;&quot;&quot;</span>
<span class="sd">RapidAPI is the world&#39;s largest API Marketplace. </span>
<span class="sd">Developers use Rapid API to discover and connect to thousands of APIs. </span>
<span class="sd">&quot;&quot;&quot;</span>
<span class="n">url</span> <span class="o">=</span> <span class="s2">&quot;https://corona-virus-world-and-india-data.p.rapidapi.com/api&quot;</span>
<span class="n">headers</span> <span class="o">=</span> <span class="p">{</span>
    <span class="s1">&#39;x-rapidapi-key&#39;</span><span class="p">:</span> <span class="s2">&quot;dec069b877msh0d9d0827664078cp1a18fajsn2afac35ae063&quot;</span><span class="p">,</span>
    <span class="s1">&#39;x-rapidapi-host&#39;</span><span class="p">:</span> <span class="s2">&quot;corona-virus-world-and-india-data.p.rapidapi.com&quot;</span>
<span class="p">}</span>

<span class="c1"># Request Covid Data</span>
<span class="n">response</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">request</span><span class="p">(</span><span class="s2">&quot;GET&quot;</span><span class="p">,</span> <span class="n">url</span><span class="p">,</span> <span class="n">headers</span><span class="o">=</span><span class="n">headers</span><span class="p">)</span>
<span class="c1"># print(response.text)  # uncomment this line to see raw data</span>

<span class="c1"># This code looks for &quot;world data&quot;</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;World Totals&quot;</span><span class="p">)</span>
<span class="n">world</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;world_total&#39;</span><span class="p">)</span>  <span class="c1"># turn response to json() so we can extract &quot;world_total&quot;</span>
<span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">world</span><span class="o">.</span><span class="n">items</span><span class="p">():</span>  <span class="c1"># this finds key, value pairs in country</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">)</span>

<span class="nb">print</span><span class="p">()</span>

<span class="c1"># This code looks for USA in &quot;countries_stats&quot;</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Country Totals&quot;</span><span class="p">)</span>
<span class="n">countries</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;countries_stat&#39;</span><span class="p">)</span>
<span class="k">for</span> <span class="n">country</span> <span class="ow">in</span> <span class="n">countries</span><span class="p">:</span>  <span class="c1"># countries is a list</span>
    <span class="k">if</span> <span class="n">country</span><span class="p">[</span><span class="s2">&quot;country_name&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;USA&quot;</span><span class="p">:</span>  <span class="c1"># this filters for USA</span>
        <span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">country</span><span class="o">.</span><span class="n">items</span><span class="p">():</span>  <span class="c1"># this finds key, value pairs in country</span>
            <span class="nb">print</span><span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>World Totals
total_cases 509,268,964
new_cases 204,268
total_deaths 6,242,509
new_deaths 630
total_recovered 461,827,849
active_cases 41,198,606
serious_critical 42,510
total_cases_per_1m_population 65,334
deaths_per_1m_population 800.9
statistic_taken_at 2022-04-24 11:18:01

Country Totals
country_name USA
cases 82,649,779
deaths 1,018,316
region 
total_recovered 80,434,925
new_deaths 0
new_cases 0
serious_critical 1,465
active_cases 1,196,538
total_cases_per_1m_population 247,080
deaths_per_1m_population 3,044
total_tests 1,000,275,726
tests_per_1m_population 2,990,303
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># RapidAPI page https://rapidapi.com/Coinranking/api/coinranking1/</span>

<span class="c1"># Begin Rapid API Code</span>
<span class="kn">import</span> <span class="nn">requests</span>

<span class="n">url</span> <span class="o">=</span> <span class="s2">&quot;https://nba-schedule.p.rapidapi.com/schedule&quot;</span>

<span class="n">querystring</span> <span class="o">=</span> <span class="p">{</span><span class="s2">&quot;team&quot;</span><span class="p">:</span><span class="s2">&quot;GSW&quot;</span><span class="p">,</span><span class="s2">&quot;date&quot;</span><span class="p">:</span><span class="s2">&quot;31-01-2022&quot;</span><span class="p">}</span>

<span class="n">headers</span> <span class="o">=</span> <span class="p">{</span>
	<span class="s2">&quot;X-RapidAPI-Key&quot;</span><span class="p">:</span> <span class="s2">&quot;4f0f5ee0b6msh1bcb7e2bb792a18p18c6b0jsn03bc958312b3&quot;</span><span class="p">,</span>
	<span class="s2">&quot;X-RapidAPI-Host&quot;</span><span class="p">:</span> <span class="s2">&quot;nba-schedule.p.rapidapi.com&quot;</span>
<span class="p">}</span>

<span class="n">response</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">request</span><span class="p">(</span><span class="s2">&quot;GET&quot;</span><span class="p">,</span> <span class="n">url</span><span class="p">,</span> <span class="n">headers</span><span class="o">=</span><span class="n">headers</span><span class="p">,</span> <span class="n">params</span><span class="o">=</span><span class="n">querystring</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">())</span>
<span class="c1"># End Rapid API Code</span>
<span class="n">json</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span>  <span class="c1"># convert response to python json object</span>

<span class="c1"># Observe data from an API.  This is how data transports over the internet in a &quot;JSON&quot; text form</span>
<span class="c1"># - The JSON &quot;text&quot; is formed in dictionary {} and list [] divisions</span>
<span class="c1"># - To read the result, Data Scientist of  Developer converts JSON into human readable form</span>
<span class="c1"># - Review the first line, look for the keys --  &quot;status&quot; and &quot;data&quot;</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>[{&#39;gameDate&#39;: &#39;1/31/2022 12:00:00 AM&#39;, &#39;games&#39;: [{&#39;gameId&#39;: &#39;0022100764&#39;, &#39;gameCode&#39;: &#39;20220131/GSWHOU&#39;, &#39;gameStatus&#39;: 3, &#39;gameStatusText&#39;: &#39;Final&#39;, &#39;gameSequence&#39;: 7, &#39;gameDateEst&#39;: &#39;2022-01-31T00:00:00Z&#39;, &#39;gameTimeEst&#39;: &#39;1900-01-01T20:00:00Z&#39;, &#39;gameDateTimeEst&#39;: &#39;2022-01-31T20:00:00Z&#39;, &#39;gameDateUTC&#39;: &#39;2022-01-31T05:00:00Z&#39;, &#39;gameTimeUTC&#39;: &#39;1900-01-02T01:00:00Z&#39;, &#39;gameDateTimeUTC&#39;: &#39;2022-02-01T01:00:00Z&#39;, &#39;awayTeamTime&#39;: &#39;2022-01-31T17:00:00Z&#39;, &#39;homeTeamTime&#39;: &#39;2022-01-31T19:00:00Z&#39;, &#39;day&#39;: &#39;Mon&#39;, &#39;monthNum&#39;: 1, &#39;weekNumber&#39;: 16, &#39;weekName&#39;: &#39;Week 16&#39;, &#39;ifNecessary&#39;: False, &#39;seriesGameNumber&#39;: &#39;&#39;, &#39;seriesText&#39;: &#39;&#39;, &#39;arenaName&#39;: &#39;Toyota Center&#39;, &#39;arenaState&#39;: &#39;TX&#39;, &#39;arenaCity&#39;: &#39;Houston&#39;, &#39;postponedStatus&#39;: &#39;A&#39;, &#39;branchLink&#39;: &#39;https://app.link.nba.com/ZThbyrgCXib&#39;, &#39;broadcasters&#39;: {&#39;nationalTvBroadcasters&#39;: [], &#39;nationalRadioBroadcasters&#39;: [], &#39;homeTvBroadcasters&#39;: [], &#39;homeRadioBroadcasters&#39;: [], &#39;awayTvBroadcasters&#39;: [], &#39;awayRadioBroadcasters&#39;: [], &#39;intlRadioBroadcasters&#39;: [], &#39;intlTvBroadcasters&#39;: []}, &#39;homeTeam&#39;: {&#39;teamId&#39;: 1610612745, &#39;teamName&#39;: &#39;Rockets&#39;, &#39;teamCity&#39;: &#39;Houston&#39;, &#39;teamTricode&#39;: &#39;HOU&#39;, &#39;teamSlug&#39;: &#39;rockets&#39;, &#39;wins&#39;: 14, &#39;losses&#39;: 36, &#39;score&#39;: 108, &#39;seed&#39;: 0}, &#39;awayTeam&#39;: {&#39;teamId&#39;: 1610612744, &#39;teamName&#39;: &#39;Warriors&#39;, &#39;teamCity&#39;: &#39;Golden State&#39;, &#39;teamTricode&#39;: &#39;GSW&#39;, &#39;teamSlug&#39;: &#39;warriors&#39;, &#39;wins&#39;: 38, &#39;losses&#39;: 13, &#39;score&#39;: 122, &#39;seed&#39;: 0}, &#39;pointsLeaders&#39;: [{&#39;personId&#39;: 201939, &#39;firstName&#39;: &#39;Stephen&#39;, &#39;lastName&#39;: &#39;Curry&#39;, &#39;teamId&#39;: 1610612744, &#39;teamCity&#39;: &#39;Golden State&#39;, &#39;teamName&#39;: &#39;Warriors&#39;, &#39;teamTricode&#39;: &#39;GSW&#39;, &#39;points&#39;: 40}]}]}]
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

</div>
 
