---
layout: post
title:  "Descrimination in Traffic Stops"
date:  2022-12-6
author: Zayne Kirkham
description: A dive into descriminatory rates of violations in traffic stops
image: /assets/images/pexels-pixabay-532001.jpg
---

# Summary of Past Work
When a police officer pulls over a car, they can either give the offending individual a warning or a citation. The reasons they may do either are multitude. Some reasons, such as if the driver is not sober, are well founded and acceptable. Other reasons, such as the driver's race or sex, are not. The data I used in these graphics came from the police department records for Montgomery County, Maryland. The data was messy and massive, with over 1.6 million entries. As such, I trimmed the factors that I was interested in down to whether the individual's race, their sex, whether alcohol was present, the season the stop was performed in, and whether the stop was conducted during the day shift or night shift. Whether they should have or not, each of these factors contributed to the individual receiving a violation or a warning. I will be exporing how each of the factors affects citations rates. You can find the code used to create these graphics in this [repository](https://github.com/zayne-kirkham/386_Data_Story).

This data set is massive; the uncleaned and unfiltered data set had 1.6 million observations. In order to be able to show the relationship between each factor, I will be displaying them using mosaic plots. Unfortunately, as there is so much information, I have had to split the data into four sections, displayed in the plot below. A critical split is on whether there was alcohol involved in the traffic stop. As you can tell by the plot below, there are many more entries with no alcohol present than the alternative. This plot is given to show how each of the subsequent plots fit in together. Each plot could be placed inside its respective intersection to show the relationship. Unfortunately, that would be illegible. 

![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/Context%20Plot.png)

The next two images illumniate the datain which alcohol was not present. by comparing the sizes of each region, we can gain insights into the interactions between the factors. It appears that each of the three highlighted races had approximately the same rates of citations accross season, sex, and shift. However, there appears to be a bias towards stopping men more than women. Without obtaining the demographics of all drivers in the state, we cannot be sure if these rates match the population. However, as the proportions do not seem to vary between citations and warnings, I believe this is pretty accurate to the population. This is not true of the observations in which alcohol was present. 


<div align="center">
<img src="https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/no_alcohol_day.png" alt="" style="width:400px;"/> <img src="https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/no_alcohol_night.png" alt="" style="width:400px;"/> 
<div align="left">
 

 If each race and sex were treated the same, we would expect the block representing those who received a warning to be shrunk down versions of the blocks for citations. However, they are radically different. While the treatment of each sex differs, I will focus on the treatment of each race. Those who were white were radically more likely to receive a warning than other races. In fact, during some seasons, essentially only white people received warnings while those of other races received near-exclusively citations. This is especially true for Hispanic males.  
 
 
<div align="center">
<img src="https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/alcohol_day.png" alt="" style="width:400px;"/> <img src="https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/alcohol_night.png" alt="" style="width:400px;"/> 
<div align="left">
  
 
We have a responsibility to stand up to descrimination in all forms. By giving a higher rate of warnings to white citizens when compared to the other two races in the data, the police are giving preferential treatment to one race over another. This is descriminatory and oppressive to all others and must be stopped. I invite you to take a look on how you treat those different than you. If there is something in your life that is descriminatory, whether conscious or unconscious, I invite you to change and invite others to do the same. Together, we can make the world a better place. 
  
