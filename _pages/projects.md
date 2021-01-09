---
permalink: /projects/
title: "Projects"
excerpt: "Projects"
author_profile: true
---
<!--
## Hyparo - A repair framework for Hyperledger fabric
One of the main features of blockchains is their immutability. Immutability of blockchains can be compared to an impregnable fortress which protects everything that goes into the chain. The fortress provides ubiquitous protection irrespective of the data that resides inside it. However, malicious intent and unwanted user errors introduce faults into the chain. Certain examples are illicit content uploaded along with transactions onto public blockchains like Bitcoin and Ethereum. The DAO attack on Ethereum-->
## Upgradable ERC223 contract - First experience with Blockchains, Solidity and Ethereum Testnet - Rinkeby
I did this project as part of the course Blockchains and Cryptocurrencies, taught by Professor Aniket Kate. I implemented an ERC223 contract in the project, which is a contract to maintain a digital currency ledger as a smart contract on Ethereum. I wrote up a smart contract in the deterministic programming language Solidity and tried to minimize the gas consumed by various operations. Considering the issues with the DAO contract on Ethereum and the millions of dollars that got stuck up in it, I wrote the contract to be upgradable in nature. I also deployed the contract on the public testnet blockchain Rinkeby. I understood the importance of efficient coding which literally translates into gas and money savings and got a flavor of smart contracts. The gas consumption values of the contract are as follows:

<ol>
<li>Contract deployment: 1,123,805</li>
<li>Registration cost per user: 94,755</li>
<li>Checking balance: 0</li>
<li>Money transfer cost per transaction: 44,359</li>
</ol>

Rinkeby transaction hash: 0xdbfe84475fac303beaa4c960fa67f2292c3cf71f47102ffb4e6007713cdec252

Rinkeby public key address: 0xd687C7c9D44e4Af03d4C3F9dD4e98aE839983363

![Testnet txns](/images/rinkeby.PNG)

## Power of Streaming - In memory data profiler using Spark Streaming
Profiling datasets for important quantities such as Mean, Variance and Quantiles is an important pre-processing step in many data pipelines. These parameters summarize the quality of data, which is used extensively by data scientists. The data profiler being used was built on Apache Spark, a data processing engine for huge workloads. The profiler used spark dataframes which imported all the given data into the cluster's memory to calculate the quantities in a distributed fashion. Profiling a dataset of size 10GB needed 10GB of memory available for the job, which implied bigger clusters for bigger datasests. However, quantities such as Mean and variance can be calculated in a streamable fashion because of which we can avoid bringing all the data into cluster's memory. Considering the huge cost of operating clusters on AWS and GCP, this was an important optimization to consider. But, calculating quantiles in a streamable fashion was a different challenge altogether. The traditional way to calculate quantiles is to sort the data and take percentiles out of it. 
![Architecture of engine](/images/streaming.png)
*picture credits - [Databricks](https://databricks.com/blog/2017/04/04/real-time-end-to-end-integration-with-apache-kafka-in-apache-sparks-structured-streaming.html)*

This operation is very expensive to perform in memory, hence we need to resort to approximation techniques. A very famous approximation technique to calculate the number of distinct elements is called Hyperloglog, which uses a very innovative approach to approximately calculate the number of distinct elements in a set. In a similar fashion, there is a beautiful algorithm to calculate quantiles approximately, published by Dr. Michael Greenwald and Dr. Sanjeev Khanna in 2001, called the [Greenwald-Khanna algorithm](https://www.researchgate.net/publication/2854033_Space-Efficient_Online_Computation_of_Quantile_Summaries). I implemented this algorithm using Spark streaming and Apache Kafka to calculate quantiles in a streamable fashion. The algorithm requires to maintain a running summary of the dataset, which can be decided on the amount of memory available and the accuracy desired. The stream version of the profiler displayed a whopping 4000% efficiency in terms of memory consumption and a 100% improvement in latency. The cluster regularly gave up and jobs crashed when we ran the previous version of the profiler, but the newer version ran in a seamless fashion and also delivered results much faster than the previous version. By way of this project, I witnessed the power of stream processing and approximation algorithms applied in practical situations.

## Bluetooth based device tracker
The motivation behind this project is property theft. I was travelling from Chennai to Hyderabad (cities in India) on a heavily crowded train. I was sleeping next to the exit door and was carrying 2 huge suitcases, one of which got stolen while I was asleep. I decided to track all my commodities with bluetooth devices attached to them, so that I receive alerts when they go out of range (Yeah, I didn't know the concept of Occam's razor back then). This technique seemed possible because bluetooth's range is 50m in densely crowded locations. I decided to code up a desktop and mobile application in Java regarding the same, which also has additional features like tracking the amount of time the device was in range. The UI looks somewhat like this at the end (I used JFrame API to build the UI). I used maven as a repository manager, so it is an additional dependency to install. 

![Bluetooth Tracker](/images/bluetooth-tracker.PNG)

The code is available in my Github, in case it seems interesting - [https://github.com/akhilsb/Bluetooth-based-device-tracking-application](https://github.com/akhilsb/Bluetooth-based-device-tracking-application).
