---
title: "Heap"
url: "dsa/graphs"
summary: "Intro, Insertion, Removing, Traversing, TradeOffs" 
showReadingTime: false
showToc: true
showBreadcrumbs: true
weight : 11
---

- Heap is a complete binary tree
	- If we represent a Binary Tree in the form of an array ,there should not be any blank space's.
	 - Height of tree is always `log(n)` , where `n` is the total nodes
 - Max Heap: Every node must have the value >= to value of all it's descendants
 - Min Heap: Every node must have min value <= to all it's descendants.
 
Heaps main use case: to get top k items
Heap is not good for: searching

##### Adding items to heap:
1. Insert in next possible level.
2. Re-arrange elements to not break heap properties