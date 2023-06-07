---
title: "Heap"
url: "dsa/heap"
summary: "Intro, Insertion, Removing, Traversing, TradeOffs" 
showReadingTime: false
showToc: true
showBreadcrumbs: true
weight : 12
---

- Heap is a complete binary tree
	- If we represent a Binary Tree in the form of an array ,there should not be any blank space's.
	 - Height of heap is always be `log(n)` , where `n` is the total nodes. because nodes are inserted at next level only after completely filling the last level.
 - Max Heap: Every node must have the value >= to value of all it's descendants
 - Min Heap: Every node must have min value <= to all it's descendants.
 
Heaps main use case: to get top k items
Heap is not good for: searching

##### Insertion:

1. Insert the new_element in next free space.
2. Re-arrange elements to not break heap properties

