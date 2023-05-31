---
title: "Graphs"
url: "dsa/graphs"
summary: "Intro, Insertion, Removing, Traversing, TradeOffs" 
showReadingTime: false
showToc: true
showBreadcrumbs: true
weight : 11
---

## Introduction 
~~an image of graph~~  
### Definition
Graph is an abstract data structure, that represents a collection of items that share a relationship.  
Connection of vertices with edges    
**G = (V,E) [where v is the set of vertices, E is the set of edges]**  

### Terminology

- **Vertex** : 

- **Edge** : 

- **Undirected Graph** (or) **Non-Directed Graph** :
A graph where the vertices have no direction    - Also known as Graph    - There is only "Degree" but there is no "In-Degree" or "Out-Degree" since there is no direction  

- **Directed Graph** : There is direction to the edges.    - Also known as Di-Graph  


- **Non-Connected Graph**:  
when there are 2 or more components(graphs), that do not have connections with each other    - If you join two components(graphs) by placing an edge between two vertices then it becomes a connected graph.    - But if you remove that connection, then entire graph is now again un-connected with two separate components(graphs).        - Such vertices whose connection removal will result in splitting the graph into sub-graphs(components) are called "Articulation Point"  

- **Simple Graph**: A directed graph is a simple graph, when below conditions satisfy  
    - If there are no self-loop vertices, and,    - If there are no parallel-edges  

- **Strong-Connected Graph**: 

- **Di-Graph** :

- **Neighbor** :

- **Adjacent** : 
1 -> 4 when two nodes are connected with an edge, they are called "Adjacent Vertices" (can be 1 <-> 4)  

- **Parallel Edges**:
4 <-> 3  these are two vertices that connect to each other. These are called "Parallel edges"  

- **Neighbors** :

- **Degree of a Node**:

    - **In-Degree**:
    2->1, 3->1, 9->1 In this graph the "In-Degree" of node 1, is 3. In-Degree is the #.of incoming edges to a vertex  

    - **Out-Degree**:
    1->21, 1->5 In this graph the "Out-Degree" of node 1 is 2. Out-Degree is the #.of outgoing edges from a vertex  

- **Self-Loop** / **cycle** :
If there is a cycle in Directed Graph it's called "Self-loop" Graph. ( 1.next = 1, here 1 connects to itself)  

~~~ad-tip
hi this is a tip
~~~
{{<note "This is the note">}}
{{</note>}}


  
## Types of Graphs:


## Representing a graph
~~~
Represent the following graph in python  

Graph:

        1 ---- 2        
        |      |        
        |      |        
        4 ---- 3        
         \    /         
          \  /           
            5  


Edges b/w nodes:

x | 1   2   3   4   5  ⬅ rows
----------------------
1 |  0   1   0   1   0  
2 |  1   0   1   0   0  
3 |  0   1   0   1   1  
4 |  1   0   1   0   1  
5 |  0   0   1   1   0  
⬆
columns  

Matrix representation:
  
matrix = [[0, 1, 0, 1, 0],
          [1, 0, 1, 0, 0],
          [0, 1, 0, 1, 1],
          [1, 0, 1, 0, 1],
          [0, 0, 1, 1, 0]]
~~~

Download file: {{<download "name" "/files/dsa/11_graphs/graph.py" >}}
Viewing file: {{<viewFile "graph.py" "/files/dsa/11_graphs/graph.py" >}} false -> new window  
Viewing file: {{<viewFile "graph.py" "/files/dsa/11_graphs/graph.py" true>}} true -> same window  


{{<details " Display a Graph">}}
Download Code: {{<download "name" "/files/dsa/11_graphs/graph.py" >}}
~~~python
import networkx as nx  
import matplotlib.pyplot as plt

def create_graph(edges: list[list[int]]) -> None:  
    # Create a graph  
    G = nx.Graph()  
  
    # Add edges to the graph  
    G.add_edges_from(edges)  
  
    plt.figure()  
    nx.draw(G, with_labels=True)  
    plt.show()
~~~
{{</details>}}

## Creating a Graph


## Traversing a Graph
### Bread First Search
### Depth First Search


## Problems
List of problems that cover Graphs

1. {{<link "Number of Islands" "https://leetcode.com/problems/number-of-islands/">}}
2. {{<link "Clone Graph" "https://leetcode.com/problems/clone-graph/">}}
3. {{<link "Max Area of Island" "https://leetcode.com/problems/max-area-of-island/">}}
4. {{<link "Pacific Atlantic Water Flow" "https://leetcode.com/problems/pacific-atlantic-water-flow/">}}
5. {{<link "Surrounded Regions" "https://leetcode.com/problems/surrounded-regions/">}}
6. {{<link "Rotting Oranges" "https://leetcode.com/problems/rotting-oranges/">}}
7. {{<link "Walls and Gates" "https://leetcode.com/problems/walls-and-gates/">}}
8. {{<link "Course Schedule" "https://leetcode.com/problems/course-schedule/">}}
9. {{<link "Course Schedule II" "https://leetcode.com/problems/course-schedule-ii/">}}
10. {{<link "Redundant Connection" "https://leetcode.com/problems/redundant-connection/">}}
11. {{<link "Number of Connected Components in an Undirected Graph" "https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/">}}
12. {{<link "Graph Valid Tree" "https://leetcode.com/problems/graph-valid-tree/">}}
13. {{<link "Word Ladder" "https://leetcode.com/problems/word-ladder/">}}






## Spanning Tree
---
Mathematically we can can represent a Graph with the notation:
`G = (V, E)`, where `V` = total vertices, `E` = total edges

For a given graph G, a spanning tress is simply a subset of the graph. So there can be multiple spanning trees for a given graph.
But the rule for of a spanning tree for a graph G with V vertices and E edges is that.
1. `V' = V` , where `V'` is the total vertices the spanning tree(sub-graph)
2. `E' = V - 1` , where `E'` is the total edges of the spanning tree.

Spanning trees can be drawn for any graph

### Minimum Spanning Tree
---
