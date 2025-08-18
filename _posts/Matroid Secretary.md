---
layout: post
title: "Matroid Secretary Problem"
---
I am currently working on this problem under [Prof. Zhiyi Huang](https://i.cs.hku.hk/~zhiyi/) from HKU.

## Online Secretary Problem

This is a classic problem in online algorithms that has been solved optimally in competitive ratio-$e$. 

Assume you are selling a product and you have a list of $n$ potential buyers. Each buyer will put in their bid at a random time and you must decide whether to sell the product or not. Additionally, the bids are private - so you only know their value when the buyer puts their bid. The goal is then to maximize your revenue by selecting the one with the highest bid. 

As is the case with most online problems, we can never solve it optimally. That is, the competitive ratio $r = \frac{OPT}{ALG}$ where $OPT$ is "Optimal in hindsight" (if the problem was offline), and $ALG$ is what our algorithm achieves. 

As mentioned before, this problem has been solved in $r = e$ and a hardness result shows that we can not do better. 

## Online Matroid Secretary Problem

There are many variants of the classic Online Secretary Problem—perhaps the most popular one is the Matroid Secretary Problem.

We are given a [Matroid](https://en.wikipedia.org/wiki/Matroid#:~:text=In%20combinatorics%2C%20a%20matroid%20%2F%CB%88,linear%20independence%20in%20vector%20spaces.) and the elements in the ground set are revealed in an online manner. We can select an element as long as the selected set of elements are independent.

The best known result so far gives $r = \log \log k$ where $k$ is the rank of the matroid. It has been conjectured that we can solve it in $r = e$ - although the problem has been open for decades.

There are some specific classes of matroids for which a better ratio has been achieved - for example, [graphical matroids](https://en.wikipedia.org/wiki/Graphic_matroid) have been solved so far in $r = 4$. 




 