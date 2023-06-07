---
title: "Dynamic Programming"
url: "dsa/dynamic-programming"
summary: "Summary for DP here" 
showReadingTime: false
showToc: true
showBreadcrumbs: true
weight : 13
---

Learning objectives:

### How to solve optimization problems? [YT](https://www.youtube.com/watch?v=5dRGRueKU3M&list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs_O&index=46)
Understand the difference b/w Greedy method and Dynamic programming.
Both are used for **optimization** problems. Optimization problems are those where you solve for minimum result or maximum result.

#### 1. Greedy Method: 
we follow a pre-defined procedure to get the optimal solution. And the procedure is optimal.
Prim's and Kruskal's algorithm for finding Minimum Spanning Tree is a Greedy Method. In this method, we don't explore all the variations, we find the most optimum solution. because when we start with a node, we look for another node that has the least edge weight with current node.
  - So here the act of choosing a node is optimal because we look for least weight, and we follow this procedure to get the final optimal solution.
  - Decision is taken only once. and every stage follows this decision.
  - Takes less space and time.
#### 2. Dynamic Programming:
we find all the possible results and then pick the optimal result.
  - Though DP can be naturally represented as recursive formula's we use iterative approach to solve DP problems. We can still use recursion, but mostly it's iterative approach.
  - DP follows ***principal of optimality***: it means that a problem can be solved by taking a sequence of decisions to get the optimal solution.
  - In DP every stage we take a decision.
  - Takes more space and time. More time because we explore all possibilities. More space because in Top-Down approach we use memoization which stores all possible variations, hence more space.

### Types of DP problems:
1. Tabulation:  **Bottom-Up** approach, iterative approach
2. Memoization: **Top-Down** approach, recursive approach

#### Problem 1: MultiStage Graph [YT](https://www.youtube.com/watch?v=9iE9Mj4m8jk&list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs_O&index=47)

Understanding the problem:
It is a Directed weighted graph. All vertices are divided into stages. First and last stage will only have 1 node, start node and target node. Nodes connect only to the next stage. 
Goal is to find the least cost path from start to target. MultiStage Graph's are used for solving resource allocation problems.

![MultiStage Graph](/images/post_images/13/1.jpeg)

