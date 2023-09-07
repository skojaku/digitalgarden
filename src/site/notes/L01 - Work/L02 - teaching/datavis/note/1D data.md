---
{"dg-publish":true,"permalink":"/l01-work/l02-teaching/datavis/note/1-d-data/","dgPassFrontmatter":true}
---


# 1D data
updated: 2022-09-21


The most simplest form of data is a list of values. The values can be categorical or quantitative. Let's focus on a list of numerical values. 

How can we visualize the list of numerical values? If our data is small, maybe we can show them all using a scatter plot like this:

![one dimensional scatter plot](https://people.sc.fsu.edu/~jburkardt/m_src/grid_display_test/hermite_o7.png)
This is clear and transparent because we can see the data itself. This, however, breaks if we have more data points. For instance, multiple data points may take the same or very similar values but appear as a point because they are heavily overlapping. Or, we may see a line because all data points fill in every gap between points. 
![](https://i.stack.imgur.com/3bN1w.png)
So, what else we can do? There are two approaches:
1. Make them visible somehow
2. Aggregate or summarize the data

## 1.  Make them visible somehow
A little tweak can make the data points more visible, if the number of data points is not so many. One tweak is to use the y-axis. We can randomly assign a y value to each data point to tease out the occoluded data points. 

![Jittering](http://docs.enthought.com/chaco/_images/jitter_plot.png)
Now, we can see more points. This technique is called *Jittering*. The scatterplot with jittering is called *jittered scatter plot*. But, even with jittering, there may be still some occlusions. In this case, the data become more visible if we place them carefully such that the data are not overlapping. This is where *beeswarm plot*, or *swarm plot*, comes in. 

![Swarmplot](https://i0.wp.com/www.r-statistics.com/wp-content/uploads/2011/03/fig_05.png?ssl=1)
Swarm plot is nice because it shows all data points and also the distribution of the points in an organic fashion.

Alternatively, we can make the scatter plot more visible without jittering. 
- Making the points more trasparent 
- Drawing only the edges of visual elements
- Visualize only randomly sampled data points 


## 2.  Aggregate and show the summary statistics
The aforementioned approach only works when the number of data points is not so huge. If we have millions of data points, there is no way to visualize each point in a perceiveable way. In this case, we have no choice but to show the summary statistics. 

A common visualization technique is *box plot*. 
![boxplot](https://cdn1.byjus.com/wp-content/uploads/2020/10/Box-Plot-and-Whisker-Plot-1.png)
Although we often use box plots, not many people have drawn box plot *by hand*. I had a chance to draw the box plot and found it fun. 

[Draw box plot by hand ](https://www.youtube.com/watch?v=r43lniTavB4)

*Histogram* is another common way to represent the distribution of 1 dimensional data points. Let me write up the definition of the histogram. 

*Histogram represents a frequency of data points in each segment by area. *

This sounds simple but is surprisingly tricky when thinking about the details. 

First, histgram does not have no gap in its segments, since histgram represents a distribution of a continuous variable. This is differet from bar chart that represents the frequency of categorical variables. 
![histgram vs bar chart](https://www.edrawsoft.com/howto/charts-comparison.png)

Second, the histgram represents the frequency *by area, not hight*. The area and hight are proportional if we use the equal-sized bins. However, if the width of bins takes different sizes, we have to *normalize* the frequency. 

![unequal bin sizes](https://chartio.com/assets/8eb2b2/tutorials/charts/histograms/dd697fef22fc1823d1996d7a09d902bc648a8f5f68cf9c975909288ba496d094/histogram-misuses-2.png)
(Left: histogram with equal-sized bins; Center: histogram with unequal bins but improper vertical axis units; Right: histogram with unequal bins with density heights). 

# References 
- https://chartio.com/learn/charts/histogram-complete-guide/
- https://ldld.samizdat.cc/2017/untitled-3/