# 228 Reading: **WEEK 15** - Monday

## **WEIGHTED GRAPHS & DIJKSTRA'S SHORTEST PATH:**

***
### **Weighted Graphs:**
* weighted graph - a graph in which each edge has an associated 'weight' (payload).
    * weight (cost) - a numerical value between vertices.
        * Ex) flight costs between airports, connection speed between computers, or travel time between cities.
    * weighted graphs can be directed graphs or undirected graphs.
* path length - the sum of the edge weights in a path.
* cycle length - the sum of the edge weights in a cycle.
    * negative edge weight cycle - a cycle with a negative cycle length. 
        * in a negative edge weight cycle, a shortest path does not exist because each loop around the negative edge weight cycle further decreases the cycle length, so a minimum cycle length does not exist.
            * must be negative upon it's first cycle.
***
### **Dijkstra's Shortest Path:**
* Dikstra's shortest path algorithm - an algorithm created by Edsger Dijkstra which determines the shortest path from a beginning vertex to each remaining vertex in the graph. 
    * the algorithm determines the vertex's distance and predecessor pointer.
        * distance - the shortest path distance from the beginning path distance.
        * predecessor pointer - points to the previous vertex along the shortest path from the beginning vertex.
    * implementation:
![](https://i.gyazo.com/6c549880944c4449904150cd32a1418f.png)
* upon completion of Dijkstra's Shortest Path, the shortest path from the beginning vertex can be found using the vertices' predecessor pointers.
    * if the vertex's predecessor pointer is not 0, the shortest path is traversed in reverse by following the predecessor pointers until the start vertex is reached.
        * if the destination vertex's predecessor pointer is null, then a path from the beginning vertex to the destination vertex does not exist. 
![](https://i.gyazo.com/0f3dfbc80b6276c535906632cb0aa91e.png)
* runtime efficiency:
![](https://i.gyazo.com/6c01448cf5ac26376ebde260efb95d05.png)
* NOTE:
    * Dijkstra's Shortest Path algorithm can be used for unweighted edges (which actually use a uniform edge weight of 1), and weighted graphs with non-negative edge weights. 
        * HOWEVER, for a directed graph with negative edge weights, Dijkstra's algorithm may not find the shortest path for some vertices, so avoid using the algorithm for graphs that contain an edge with a negative weight. 
***