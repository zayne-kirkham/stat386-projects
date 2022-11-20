---
layout: post
title:  "The Wars To End All Wars: an EDA Into the World Wars"
date:  2022-10-18
author: Zayne Kirkham
description: An exploration into the casualties of the wars that shook the entire world. 
image: /assets/images/WW_post/pexels-asim-alnamat-404995.jpg
---

# Intro
World War One and World War Two have shaped the world more than any other military conflict throughout time. Millions were killed. Millions were left without a home. Millions starved or froze as they fled their homes and their countries. Despite this, technology and innovation advanced at an unprecedented rate. Technologies used to kill came to be used to save lives, grow food, and revolutionize entire economies. 

# Cleaning The Data
In a prior [post](https://zayne-kirkham.github.io/stat386-projects/2022/10/18/Scraping-Data-From-Wikipedia.html), we explored scraping data about the casualties of these wars from Wikipedia. This data was easy to obtain, but extraordinarily messy. Footnotes, missing values, and inconsistent categorization plagued the data. This data needed to be cleaned in order to be useful for exploration and analysis. While you can find the full cleaning code [here](https://github.com/zayne-kirkham/World-War-Casualties/blob/main/Cleaning%20for%20EDA.ipynb), below is an example of some of the cleaning that needed to be done. 
``` {py}
# clean WW2 'Civilian deaths due to direct military action'
temp = ww2_df['Civilian deaths due to direct military action'].str.replace('(\[.{0,3}\])', "").str.replace('(\(.*\))', "")
temp[59] = '12,100'  # remove footnote artifact
temp[19] = '1,500,000to 3,000,000' # remove footnote artifact
ww2_df['Civilian deaths due to direct military action'] = temp.str.replace(',', "").str.split("to", expand=True).astype(float).mean(axis=1).round()
```
As you can see, this was not a difficult process, just time intensive. You can find the full cleaned data [here](https://github.com/zayne-kirkham/World-War-Casualties/blob/main/Cleaned_data.csv).

# Examining Each Factor
Once the data was cleaned, I could explore the data. You can find all of the created plots in [this repository](https://github.com/zayne-kirkham/World-War-Casualties) and the EDA code [here](https://github.com/zayne-kirkham/World-War-Casualties/blob/main/EDA.ipynb). I narrowed down my interest to the following factors:
 - Nation
 - Population
 - Total military deaths from all causes
 - Civilian deaths due to direct military action
 - Civilian deaths due to indirect military action
 - Total deaths
 
 ## Factor Distributions
 Each factors of interest is numeric. As such, I wanted to check the distribution of each one, both for each war and the wars together. This was accomplished usign the following code:
 ``` {python}
temp = data.columns.values.tolist()[1:-3] + [data.columns.values.tolist()[-2:]]
for i in range(len(temp)-1) :
    fig, (ax1, ax2) = plt.subplots(ncols=2, sharey=True)
    # Set Scale
    ax1.set_xscale('log')
    ax2.set_xscale("log")
    # Plot 1
    sns.histplot(x=temp[i], 
                 data = data, 
                 ax = ax1,
                 ) 
    # Plot 2
    sns.histplot(x=temp[i], 
                 data = data, 
                 hue = "War", 
                 multiple = "dodge", 
                 ax = ax2,
                 )

    fig.suptitle(f"{temp[i]}")
    ax1.set_title(f"Distribution")
    ax2.set_title(f"Distribution by war")
```

Overall, after the log scale was applied, each distribution was suprisingly normal. The major exception was the amount of indirect civilian casualties. 
![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/dist_indir_civ.png)
Upon inspecting the distribution on the right, however, we can see that each war's distribution is distinct. World War One was a notable lower outlier while World War Two is strongly left skewed. As World War one progressed, more and more troops were poured into the meat grinder of the French countryside. Most of the conflict was contained on the soil of Europe, with only occasional battles being fought elsewhere. As such, the general lives of civilians were not majorly shortened in many parts of the world. However, World War Two was a much more global conflict. It affected many more countries in a much deeper way than World War One ever did. 

The corresponding boxplot (below) tells a similar story. Oddly enough, this factor had the least amount of outliers. I am not entirely sure what this means. Each distribution tells a story. With the proper understanding of history and context, these stories become apparent.
![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/box_dir_civ.png)

The other distribution plots are found below:
![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/dist_dir_civ.png)

![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/dist_pop.png)

![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/dist_tot_death.png)

![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/dist_tot_mil_death.png)

As stated earlier, each distribution is suprisingly normal. While there are outliers, there are no skews that would prevent us from performing standard analysis on the data. 

Additionally, I explored the relationship between total deaths and population. This plot also requires a log scale to be readable. While mostly homogeneous, It is apparent that there is not a one to one ratio between each factor. There is a lot of noise and, examining the lower portion of the graph, there is a confounding variable leadign to the data from World War Two being much more spread out. 
![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/WW_post/tot_x_pop.png)



# Conclusion
In conclusion, This data has much it can teach us. It has a few issues, such as plenty of missing values, but each factor is suitable for analysis. The past is rich with information. How can we use it to provide a bettwer future for ourselves? This data teaches us about some of the impacts of war, especially on the lives of civilians. I invite you to explore this data for yourself. In addition, I invite you to learn about the past for yourself. Learn the past and strive to make the future better.































