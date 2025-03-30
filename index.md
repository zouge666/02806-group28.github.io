---
layout: default
title: Welcome to Group 28's Website - Assignment 2
---

# Welcome to Group 28's Website - Assignment 2

<div style="text-align: center;">
    Written by：
</div>
<div style="text-align: center;">
    Yunxuan Li - s232900
</div>
<div style="text-align: center;">
    Senhao Zou - s242606
</div>
<div style="text-align: center;">
    Xiaosa Liu - s242649
</div>

Welcome! On this page, we present a short data story about **TRESPASS crimes** in San Francisco.
Our visualizations aim to reveal spatial, temporal, and interactive patterns based on real crime data.

---

San Francisco, the cultural, commercial, and financial center of Northern California and the Bay Area, has long been known for innovation, diversity, and cultural vitality—but it’s also a city grappling with complex issues of urban safety and inequality. **Trespass crimes** is one of the lesser-known crimes that quietly affects city life: the act of entering someone else’s property without permission.
This short data story explores how trespassing in San Francisco has changed over time and space using publicly available police data from 2003 to 2025. Our goal is to go beyond the raw numbers to understand: How has this urban crime evolved? Which parts of the city are most affected? What might these patterns reveal about larger societal trends?
Using three visualizations—a time series, a geographic heat map, and an interactive borough-level map—we tell a visual story spanning two decades, zooming out from citywide to individual neighborhoods.

## Figure 1: TRESPASS Crimes by Year

This time series chart shows how the number of trespass incidents has changed over time from 2003 to 2025.

![TRESPASS Chart](trespass_by_year.png)

### 📈 When and Why Did Trespass Incidents Spike?

When analyzing San Francisco crime data, we observed a significant spike in trespassing incidents in **2018**, when the number of cases rose rapidly. This was followed by a gradual decline beginning in 2019, creating a distinct **"up-then-down" trend** over time.

According to [news reports](https://hoodline.com/2018/11/calls-to-sfpd-down-from-last-year-trespassing-and-noise-complaints-tick-up/), multiple types of crime surged in 2018, including trespassing, theft, and public disturbances. Several factors may have contributed to this rise:

---

#### 1. A Rise in Other Crime Types

As other forms of crime increased—such as vehicle break-ins—criminals may have felt emboldened to commit additional offenses, including trespassing.

Research shows that **2017 and 2018 were peak years for the "smash-and-grab" epidemic**, with **over 85 car break-ins per day**. Out of more than **30,000 reported incidents**, only **550 suspects were arrested**, amounting to a **clearance rate below 2%**. The near-absence of consequences may have encouraged more opportunistic crimes like trespassing.
🔗 [KQED: Car Break-Ins Are Up in San Francisco – What's Being Done](https://www.kqed.org/news/11643054/car-breaks-ins-are-up-in-san-francisco-whats-being-done)

---

#### 2. Legal Shifts – Proposition 47

The passage of **California’s Proposition 47 in 2014** reclassified certain non-violent felonies as misdemeanors, reducing penalties for offenses such as theft and drug possession. Critics argue that this policy **gave criminals more confidence** to commit low-level crimes with less fear of legal consequences.
🔗 [LA Times: What Is California Proposition 47?](https://www.latimes.com/california/story/2024-08-12/what-is-california-proposition-47-how-proposition-36-could-change-crime-sentencing-drugs-theft)

---

#### 3. Housing Insecurity and Rising Homelessness

Economic pressure has intensified in recent years, with **housing affordability reaching a breaking point**. According to [Invisible People's 2024 housing report](https://invisiblepeople.tv/californias-housing-crisis-86-cant-comfortably-afford-san-francisco), a staggering **86% of residents can no longer comfortably afford to live in San Francisco**.

Skyrocketing rents and a shortage of affordable units have pushed thousands into **precarity or homelessness**, leading some to enter private or abandoned spaces in search of shelter—actions that can be classified as trespassing under the law.


---

## Figure 2: Heatmap Animation of TRESPASS

This animated heatmap illustrates the **geographic distribution of trespass crimes**, year by year.
Each frame shows hot zones where incidents were most frequent.

<iframe src="trespass_heatmap_by_year.html"
        style="width: 100%; max-width: 960px; height: 520px; margin: auto; display: block; border: none;"></iframe>

Based on the heat map we can find:
It is clear that the MISSION district and its northeastern part have a significantly higher frequency of criminal activities, showing a more concentrated area of high crime heat. This suggests that these areas may have become major activity zones for criminals, especially some vagrants and criminal street gangs. It is therefore reasonable to speculate that those vagrants engaging in vehicle crimes in the urban areas may gradually shift their targets to the nearby affluent districts in search of greater benefits and opportunities to commit crimes.

---

## Figure 3: Interactive Bokeh Explorer

Use the dropdown and slider to explore **where and when** trespass crimes occurred across different police districts.

<iframe src="bokeh_trespass_interactive.html"
        style="width: 100%; max-width: 960px; height: 620px; margin: auto; display: block; border: none;"></iframe>

As we analyze the situation by district, the answers emerge (please select Mission District).
The severe homeless problem has brought not only random urination and defecation to the streets of San Francisco, but also a large number of property crimes, with car smashes and supermarket robberies being the most direct results.The Mission District is a busy commercial area in downtown San Francisco, but it is also one of the areas where property crimes are most prevalent. [Link4](https://sfchamber.com/public-safety-homelessness-affordability-biggest-issues-2018-sf-chamber-poll/)

---

### Summary

As a result of the widening gap between the rich and the poor, rents have skyrocketed, and San Francisco's homeless population has also increased dramatically in recent years, with the number of homeless people in San Francisco increasing by 17 percent from 2017 to 2020. The city has more than 8,000 homeless people sleeping on the streets year-round, with tents staked out on either side of the sidewalk. This confirms our suspicion that there is a strong correlation between crime “spikes” and homelessness in the context of the Prop 47 referendum.
Together, these visualizations help us uncover how TRESPASS crimes evolved across time and space in San Francisco.
The interactive explorer empowers viewers to dive deeper into their districts of interest.

---
