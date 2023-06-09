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
- Both are used for **optimization** problems. Optimization problems are those where you solve for minimum result or maximum result.  
- **Divide and conquer algorithms break the problem down into subproblems, but these subproblems are not overlapping.**

#### 1. Greedy Method: 
we follow a pre-defined procedure to get the optimal solution. And the procedure is optimal.
Prim's and Kruskal's algorithm for finding Minimum Spanning Tree is a Greedy Method. In this method, we don't explore all the variations, we find the most optimum solution. because when we start with a node, we look for another node that has the least edge weight with current node.
  - So here the act of choosing a node is optimal because we look for least weight, and we follow this procedure to get the final optimal solution.
  - Decision is taken only once. and every stage follows this decision.
  - Takes less space and time.
#### 2. Dynamic Programming:
we find all the possible results and then pick the optimal result.
  - Though DP can be naturally represented as recursive formula's we use iterative approach to solve DP problems. We can still use recursion, but mostly it's iterative approach.
  - DP follows ***principal of optimality***: it means that a problem can be solved by taking a **sequence of decisions** to get the optimal solution.
  - In DP every stage we take a decision.
  - Takes more space and time. More time because we explore all possibilities. More space because in Top-Down approach we use memoization which stores all possible variations, hence more space.

### Types of DP problems:
1. Bottom-up (Tabulation): Iterative approach - runtime is usually faster, as iteration does not have the overhead that recursion does.
2. Top-Down (Memoization): Recursive approach - usually much easier to write. This is because with recursion, the ordering of subproblems does not matter, whereas with tabulation, we need to go through a logical ordering of solving subproblems.

### When to use DP
**The first characteristic** that is common in DP problems is that the problem will ask for the optimum value (maximum or minimum) of something, or the number of ways there are to do something. For example:

- What is the minimum cost of doing...
- What is the maximum profit from...
- How many ways are there to do...
- What is the longest possible...
- Is it possible to reach a certain point...

**The second characteristic** that is common in DP problems is that future "decisions" depend on earlier decisions. Deciding to do something at one step may affect the ability to do something in a later step. This characteristic is what makes a greedy algorithm invalid for a DP problem - we need to factor in results from previous decisions. Admittedly, this characteristic is not as well defined as the first one, and the best way to identify it is to go through some examples.

[House Robber](https://leetcode.com/problems/house-robber/) is an excellent example of a dynamic programming problem.
[Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) is another example of a classic dynamic programming problem. In this problem, we need to determine the length of the longest (first characteristic) subsequence that is strictly increasing. For example, if we had the input nums = [1, 2, 6, 3, 5]nums = [1, 2, 6, 3, 5], the answer would be 4, from the subsequence [1, 2, 3, 5][1, 2, 3, 5]. Again, the important decision comes when we arrive at the 6 - do we take it or not take it? If we decide to take it, then we get to increase our current length by 1, but it affects the future - we can no longer take the 3 or 5. Of course, with such a small example, it's easy to see why we shouldn't take it - but how are we supposed to design an algorithm that can always make the correct decision with huge inputs? Imagine if nums contained 10,00010,000 numbers instead.

### Framework for DP problems
[LeetCode - Link for this section](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4096/)  
Before looking at the 3 things that make DP framework, understand what state & state variables are.
**State**: a **state** is a set of variables that can sufficiently describe a scenario. These variables are called **state variables**, and we only care about relevant ones. tldr; all state variables together is the state.

> - In climbing stairs problem: To describe every scenario in Climbing Stairs, there is only 1 relevant state variable, the current step we are on. We can denote this with an integer ii. If i = 6i = 6, that means that we are describing the state of being on the 6th step. Every unique value of ii represents a unique **state**.
> - In robbing houses problem: the amount of money in current house is a state variable.
> - In coin change problem: the denomination is a state variable

Mind map image: imagine that the framework is the tree/graph we are drawing, and now for the nodes we have to choose the state variables of the problem. because of the tree represents all the possible solutions for the problem, and the the state variables are those that we use to traverse in the tree to calculate the value for that path.

**FRAMEWORK:**
1. **A function or data structure that will compute/contain the answer to the problem for every given state**.  
	Data Structure is straightforward, say we have a dictionary for all the fibonacci numbers {num : fib(num) }  
	 Function: instead of a Data Structure if we have a function that we can call and that returns the value for us.
2. **A recurrence relation to transition between states.**
3. **Base cases, so that our recurrence relation doesn't go on infinitely.**



### Problem 1: MultiStage Graph [YT](https://www.youtube.com/watch?v=9iE9Mj4m8jk&list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs_O&index=47)

Understanding the problem:
It is a Directed weighted graph. All vertices are divided into stages. First and last stage will only have 1 node, start node and target node. Nodes connect only to the next stage. 
Goal is to find the least cost path from start to target. MultiStage Graph's are used for solving resource allocation problems.

1. Find the minimum cost of each vertex. when we start from 1, we have to already know the minimum cost path for 2,3,4,5 and these nodes depend on min. costs of nodes at V3 and so on. So we begin from last, (Bottom-Up approach, iteratively) because the node 12 is the end and the min. cost of 12 is 0. and from here we trace back.
![MultiStage Graph](/images/post_images/13/1.jpg)
![MultiStage Graph](/images/post_images/13/2.jpg)

2. Now using forward approach.


### Problem 2: House Robber

```python
'''
					1 2 3 1 X
					- - - - -
					
					2 7 9 3 1 X
					- - - - - -
				i = 0 1 2 3 4 5
			 dp(i)= 2 7 11 11 12

	 
					i
					
					0         0
					
					1      2       7
					
					2     9  3    3  1


- if you start from beginning, the choices of next houses are to be already known.so it doesnt make sense to start from beginning.

- We start from last house(same logic for every house), when we are at the last house we have 2 options: rob this house + rob i-2th house, or just rob i-1 house.

- So for a house at index i, the max. amount stolen is max( dp(i-2)+nums[i], dp(i-1) ),

- i.e., the max amount that can be stolen until this point depends on these 2 situations, ie.,e steal(current_house)+stolen until(current_house -2) or stolen(current_house-1).

  

- so the decision of i depends on i-1, i-2. This means that the base cases for i=0,i=1 should be defined.

- cuz starting with i = n, we go back n-1,n-2,...5,4,3,2,1. and when we reach i=2, it depends on 1,0.

-when i is at 0, we only have the option to steal that house, since each house >= 0

- when i is at 1, we chose the max(nums[0], nums[1]) bcs we start with i=1 if i=0 holds less amount, but if i=0 holds more value, then dp(1) = nums[0] meaning at idx=1, max amount stolen is nums[0] ex: 99, 7, ...
'''

class Solution:

	def rob(self, nums: List[int]) -> int:

		def dp(i, memo):
			if i == 0:
				return nums[0]
			if i == 1:
				return max(nums[0], nums[1])
			if i not in memo:
				memo[i] = max(dp(i-2, memo) + nums[i], dp(i-1, memo))
			return memo[i]
	
		n = len(nums)
		memo = {}
		return dp(n - 1, memo)

```


### Multidimensional DP

one state variable to define the state -> 1-dimension DP
Two state variables to define the state -> 2-dimension DP

The following are common things to look out for in DP problems that require a state variable:
- An index along some input.  
   Example: If the input is `nums = [0, 1, 2, 3, 4, 5, 6]`, then `dp(4)` would represent the answer to the problem for the input `nums = [0, 1, 2, 3, 4]`
- A second index along some input. Sometimes, you need two index state variables, say `i`,`j`.  
  In some questions, these variables represent the answer to the original problem if you considered the input starting at index `i` and ending at index `j`. Using the same example above, `dp(1, 3)` would solve the problem for the input `nums = [1, 2, 3]`, if the original input was `[0, 1, 2, 3, 4, 5, 6]`.  
- Explicit numerical constraints given in the problem. For example, "you are only allowed to complete `k` transactions", or "you are allowed to break up to `k` obstacles", etc. 
- Variables that describe statuses in a given state.  
  Example: "True if currently holding a key, False if not", "currently holding `k` packages"
- some sort of data or a bit mask used to indicate things being 'visited' or 'used'.  
  Example: `bitmask` is a mask where the `i` bit indicates visited or not visited.
  
