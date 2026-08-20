---
layout: post
title: "PoS Sharding"
---

I worked with Prof. Haifeng YU (https://www.comp.nus.edu.sg/~yuhf/) at NUS as a summer research intern. 

I worked on 2 problems related to distributed algorithms - PoS Sharding and Problems in duplex model with dynamic graphs. 

## Proof of Stake Sharding

This is the primary problem I worked on. 

Sharding in blockchain systems refers to divding users into different groups (with the goal of increasing effeciency). Current protocols involve either Proof of Work (how much computing power I have), or Proof of Stake (how much money I have). Sharding is straight forward in PoW since one user being in many shards (committees) does not affect the effeciency considering that the user much have good computational power to end up being in many shards. However, it breaks down in Proof of Stake - I may have big stake while not have great computatoinal power. 

Thus, there is a real need to develop algorithms which try to increase effeciency while keeping security guarantees in mind. Protocols designed have security guarantees such as "as long as malicious stake (stake held by malicious nodes) is not more than 50%, the protocol securely work". The problem is then to divide the users into shards such that this guarantee is met with high probabilitiy. Of course, we don't know the malicious nodes - which makes this problem quite hard and mathematically rich.

## Duplex Model 

In the paper : https://www.comp.nus.edu.sg/~yuhf/TRA4-16.pdf, we consider the simplex model. The same idea breaks down if we consider the duplex model. Thus we want to study how powerful the duplex model is, and if similar lowerbound results hold or not. 

## My work 

<iframe src="/assets/images/res/nus/main.pdf" style="width: 100%; height: 500px;" frameborder="0"></iframe>