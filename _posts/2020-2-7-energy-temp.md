---
layout: post
title: Visualizing the relationship between energy demand and air temperature
subtitle: Analysis in Python
---
**The Data:** The energy data, hosted on Kaggle, is from a regional transmission organization called PJM Interconnection LLC. Within PJM’s data, I selected the subset from Dayton Power and Light (DPL). The weather data is from NOAA. Here is a link to my Github page hosting the Google Colaboratory notebooks where I cleaned and visualized the data.

**Background**
I started this project with the intention of digging into the relationship between energy demand and air temperature, with the goal of better understanding how complex energy systems operate. To best explore this, I wanted energy and temperature data on the highest possible time resolution. Equally high time resolution between datasets would allow me to do less data cleaning and also provides more detail. In order to focus on a single weather station, I also wanted to look at the smallest region that I could find. This led me to the hourly energy data in megawatts (MW) from DPL, which serves 525,000 customers across 6,000 square miles. To approximate the weather of this entire region I used hourly data gathered at Dayton International Airport.

**Mean Hourly Demand vs Mean Hourly Temperature**
To start off, it is helpful to take a look at how both daily energy demand and daily air temperature vary during an average day in each season:
