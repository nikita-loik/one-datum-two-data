---
title: "Route Inspection"
date: 2019-09-08T00:00:00-00:00
categories:
  - blog
toc: true
toc_label: "Table of Contents"
toc_icon: "th-list"
tags:
  - chinese-postman problem
  - CPP
  - travelling-salesman problem
  - TSP
  - route inspection
  - NetworkX
---

## 0. Very Brief Introduction

In route inspection, I will try to address two classical invert problems — [Chinese-Postman Problem (CPP)][cpp] and [Travelling-Salesman Problem (TSP)][tsp]. In CPP the task is to create a route along all the roads in some area, such that it covers each road exactly once. In TSP one has to create a route to get to all the cities within some area, in such way that travelling is minimum. Both problems are considered [NP-hard problems][np-hardness]. In reality, people are satisfied with some suboptimal solutions — travel along all the roads (possibly more than once), but try to minimise the extra travelling. Those solutions cost money. To the best of my knowledge, one such solution offers a custom-made app at approximately €50 000 per year; another offers a route generation for as little as €400 per route.

In here I will use a simulation to show how these two problems can be solved (it is just a solution, not a panacea, though). Unlike simulated data, the algorithms themselves are pretty real though and are in constant use.

I will also try to introduce some graph theory concepts essential for understanding. Not too much, though, because I don't know too much about them. Finally, I will try to design some simple test cases, cases which are easy to visualise and understand.

## 1. Get Random City and Random District

First, I will model a random city — some area, where you can get from any node to any node. Then, I will select a random district in the city. Importantly, it may be impossible to get to any node within the district without crossing its boarders.

To make it more realistic, I included both one-way and two-way streets, as well as exclude some segments completely.

### 1.A. Visualise City

### 1.B. Get City Statistics

## 2. Graph Introduction

Graph is a set of dots (nodes), some of which are connected by segments (edges).

### 2.A. Directed Graph Vs Undirected Graph

In undirected graph an edge between two nodes (a and b) indicates that each node can be reached from another node, i.e. edges (a, b) and (b, a) are equal. In directed graph any edge between two nodes has a direction, with a source node known as tail and target node known as head. In directed graph edges (a, b) and (b, a) have opposite directions and are not equal.

### 2.B. Strongly Connected Graph

### 2.C. Graph Representation in NetworkX

Essentially, a graph is comprised of two collections — collection of nodes (each node has a unique name, and some node attributes) and collection of edges (each edge is uniquely defined by the nodes it connects, and some edge attributes). Node attributes can be anything including node coordinates. Importantly, two nodes with identical coordinates but different names, are different nodes.

### 2.D. Links

## 2. Get City and District Graphs

### 2.A. Visualise

[cpp]: https://en.wikipedia.org/wiki/Route_inspection_problem
[tsp]: https://en.wikipedia.org/wiki/Travelling_salesman_problem
[np-hardness]: https://en.wikipedia.org/wiki/NP-hardness