---
title: Day 7 - Designing a histogram with pen and paper
date: 2022-02-12T17:04:42.489Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Today I learned how to design a histogram based on given percentages. Creating a histogram new in R or Python is one line away, but knowing how to design and create one is different. 

Some notes:

If we have revenues from:

0 - 1000$ dollars - 5%

1000$ - 2000$ - 5%

2000$  - 3000$ - 10%

3000$-5000$ - 20%

5000-10000$ - 60%

Given this input, if we were to create a histogram based on a density scale, we would create 5 blocks.

First we create a horizontal line with intervals with values from 0 to 10, and small intervals at each point, 0, 1, 2, 3, 4...9, 10. 

So. 

The vertical scale would be up to 60%, small intervals of 10, 20, 30, 40, 50, 60.

1st block: from 5% we draw a block from 0 to 1. 

2nd block: from 5% we draw a block from 1 to 2.

3rd block: from 10% we draw a block from 2 to 3.

4th block: we convert the 20% by 2, and we get 10%. Remember that the density is divided from 3000$ to 5000$ dollars. We create the block from 10%, from point 3 to point 5.

5th block: we convert the 60% by 5, and we get 12%. We draw a block from 12%, from point 5 to 10.