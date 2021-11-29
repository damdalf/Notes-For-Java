# 228 Reading: **WEEK 14** - Monday

## **GRAPHS:**
* graph - a graph is a non-linear data structure for representing connections among items, and consists of vertices (nodes) connected by edges.
    * vertex - represents an item in a graph.
    * edge - represents a connection between to vertices in a graph.
    * graphs are best similar to binary trees, but are far less structured
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
* path length - the number of edges in the path 
* distance - the number of edges in the shortest path between two vertices.
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

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fadrianmejia.com%2Fimages%2Fcyclic-vs-acyclic-directed-graph.jpg&f=1&nofb=1)
***
### **WEIGHTED VS. UNWEIGHTED GRAPHS**
* weighted graph - a graph in which there is some form of 'weight', or preference / quality, given to the connections (edges) between vertices.
    * a graph for a navigation application may provide greater weight to certain edges that offer a quicker travel-time for the user.
* unweighted graph - a graph in which all edges are 'weighted' equally.
***