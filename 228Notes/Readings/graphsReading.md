# 228 Reading: **WEEK 14** - Monday

## **GRAPHS:**
* graph - a graph is a non-linear data structure for representing connections among items, and consists of vertices (nodes) connected by edges.
    * vertex - represents an item in a graph.
    * edge - represents a connection between to vertices in a graph.
    * adjacent vertices - in an undirected graph, two vertices are adjacent if they are connected by an edge.
    * path - a path is a sequence of edges leading from a source vertex to a destination vertex. 
    * path length - the number of edges that are traversed in a given path.
    * distance - the number of edges in the shortest path between two vertices.
    * simple path - a path with no repeated nodes.
    * simple cycle - a cycle with no repeated nodes or edges, other than the source and terminating nodes. 
    * denisty - the ratio of the number of edges (or average number of edges per node) to the maximum number of possible edges.
        * undirected maximum density - V^(2) / 2
        * directed maximum density - V^(2)
* there are two main types of graphs
    * undirected graphs
        * connections or relationships between items are mutual.
    * directed graphs
        * these are one-way connections in which there is a starting (source) vertex and a terminating (destination) vertex.
        * directed graphs are also known as digraphs.

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fadrianmejia.com%2Fimages%2Fdirected-vs-undirected-graph.jpg&f=1&nofb=1)

* graphs are used for many different kinds of data structures:
    * social media networks
    * world wide web
    * navigation appliacations
***
### **UNDIRECTED GRAPHS:**
* adjacent vertices - in an undirected graph, two vertices are adjacent if they are connected by an edge.
* path - a path is a sequence of edges leading from a source vertex to a destination vertex. 
* path length - the number of edges in the path.
* distance - the number of edges in the shortest path between two vertices.
* degree - the number of the neighbors of a specific node.
* connected - an undirected graph is 'connected' if there is a path from every node to every other node in the graph.
    * think of a web, or one 'whole' structure.
* if the undirected graph is not connected, then it contains 'connected components'. 
***
### **DIRECTED GRAPHS:**
* directed edge - a directed edge is a one-way connection between a source vertex and a destination vertex.
* adjacent vertices - in a digraph, a vertex is adjacent to another vertex if the other vertex points to the original vertex.
    * A->B
        * Vertex B is adjacent to vertex A, but vertex A is not adjacent to vertex B.
* path - in a digraph, the path is a sequence of edges leading from a starting vertex to a terminating vertex.
* cycle - in a digraph, a cycle is a path that starts and ends at the same vertex.
    * cyclic digraph - if the graph contains a cycle, then it is a cyclic digraph.
    * acyclic digraph - if the graph does not contain a cycle, then it is an acyclic digraph. 
* out-degree - the number of the neighbors connected to a specific node.
    * 'directed outward'.
* in-degree - the number of neighbors that have the specific node as a neighbor.
    * 'directed inwards'.
* a digraph is 'strongly connected' if for every pair of nodes both nodes are neighbors of each other. 
    * meaning that the two nodes both share a connection with each other - not a single one-way connection.
![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fadrianmejia.com%2Fimages%2Fcyclic-vs-acyclic-directed-graph.jpg&f=1&nofb=1)
***
### **WEIGHTED VS. UNWEIGHTED GRAPHS**
* weighted graph - a graph in which there is some form of 'weight', or preference / quality, given to the connections (edges) between vertices.
    * a graph for a navigation application may provide greater weight to certain edges that offer a quicker travel-time for the user.
* unweighted graph - a graph in which all edges are 'weighted' equally.
***
### **IMPLEMENTING A GRAPH:** 
* there are three main ways to implement a graph in programming:
    1) adjacency matrices
    2) adjacency lists
    3) HashMaps / HashSets
* adjacency matrix - An adjacency matrix is a V-by-V array of boolean values. Each row and column represents a vertex of the graph. Set the value at row i, column j to true if (i, j) is an edge of the graph.
    * this implementation is a good choice if the graph consists of few nodes, or if the graph is dense and large. 
* adjacency list - An adjacency list representation consists of an array with one entry per node. The entry for node v references the set of all neighbors of v (recall that u is a neighbor of v if (v,u) is an edge in the graph).  
    * this implementation is a good choice if the graph is large, but not very dense. 
    * to handle the references to the node's neighbors, you can use any of the following:
        1) arrays
        2) linked-lists
        3) BST's
* HashMaps and HashSets offers a time complexity of O(1) for the following operations:
    * accessing nodes.
    * checking if nodes are adjacent.
    * adding and deleting a node.
    * adding and deleting an edge.
* here are the time complexities for adjacency matrices and lists:

![](https://i.gyazo.com/19bfdd456490d34d8d997d1a2eb02e02.png)
***
### **TRAVERSING A GRAPH:**
* there are two main ways to traverse a graph:
    1) depth-first search (DFS).
    2) breadth-first search (BFS).

***