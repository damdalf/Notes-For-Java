# 228 Reading: **WEEK 14** - Wednesday

## **GRAPH IMPLEMENTATIONS AND BREADTH-FIRST SEARCHES:**

***
### **ADJACENCY LISTS:**
* adjacency list - a representation of a graph in which each vertex has a list of adjacent vertices, with each list item representing an edge between nodes.
* the biggest advantage of an adjacency list graph representation is a size of O(V + E), becuase each vertex appears once, and each edge appears twice. 
    * V refers to the number of vertices.
    * E refers to the number of edges.
* however, a disadvantage of an adjacency list representation of a graph is that determining whether two vertices are adjacent takes O(V), because one vertex's adjacency list must be traversed looking for the other vertex, and the adjacency list could contains V items.
* adjacency list representations of graphs are best used for sparse graphs.
    * sparse graph - a sparse graph is a graph in which it has fewer edges than the maximum amount of edges that are possible, which is most graphs.
        * computer networks, flights between cities, and social media networks.

![](https://i.gyazo.com/a2f8b4f1cacdf41bd110f7f8dc706566.png)
***

### **ADJACENCY MATRICES:**
* adjacency matrix - a representation of a graph in which each vertex is assigned to a matrix row and column, and a matrix element is 1 if the corresponding two vertices have an edge, and 0 if an edge does not exist between the two vertices.
    * the common implementation of an adjacency matrix is one which uses a two-dimensional array whose elements are accessible in O(1).
    * the ends of the matrices or arrays are assembled reading the vertices from left to right.
* the biggest advantage of using an adjacency matrix implementation of a graph is that you are able to determine if two edges are adjacent in O(1).
    * all that needs to be checked is if the element in question is a 1 or a 0.
* however, the biggest disadvantage to using an adjacency matrix implmentation of a graph is a size of O(V^2), since a graph of 1000 elements would require a 1000 x 1000 array.
* thus, adjacency matrix implmentations of graphs are best used when a graph is far from being a sparse graph, meaning that the number of edges in the graph is somewhere close to the number of maximum possible edges in the graph.
    * additionally, an adjancency matrix only represents edges among vertices, so if each vertex contains data then another list of vertices is required to store the data of the vertices.
* to find the total number of edges in an adjacency matrix, start from [0][0] and count to [0][n]. From there, continue to increment the column by one each time. 
    * Ex) to add the number of connections present in the second row of the matrix, you would start at [1][1] count to [1][n].
    * this is because after the first row, each succeeding column represents an already counted edge. Progress diagonally from where you began your previous count when moving to a different row in the adjacency matrix.

![](https://i.gyazo.com/14fd2312e885cf2b1f98d473dc07371c.png)
***

### **BREADTH-FIRST SEARCH (BFS):**
* BFS - is a graph traversal algorithm that visits a starting vertex and then all vertices of a distance of 1, then of a distance of 2, and so on... without revisting a  vertex.
    * recall that the distance between two vertices is the number of edges in the shortest path between the two vertices. 
        * note that the visiting order of vertices of the same distance from the starting vertex does not matter.
            * which implies that the traversal of a graph is not unique.
        * THE STARTING INDEX IS VISITED, lol. Thank you, ZyBooks.
    * BFS's are commonly used when reccomending particular items to a customer based off of their purchasing habits, or reccomending a friend to a user on FaceBook, or even reccomending a connection between two users on LinkedIn.
        * the only time a distance of 0 is possible is when you are visiting the starting vertex, or beginning your search.
        * current connections have a distance of 1.
            * connections with a lower distance, but a distance greater than 1, are reccomended before other possible connections.
    * intermediary distance - this is distance - 1.
    * *Example:* a peer-to-peer network.
        * peer-to-peer network - computers are cinnected via a network and may seek and download file copies (such as songs or movies) via intermediary computers or routers (like TOR and The Pirate Bay).
* a common implementation of a BSF is using two queues: a frontierQueue, and a discoveredQueue.
    * the starting vertex is enqueued into both queues, and while the frontierQueue is not empty, the algorithm dequeues a vertex from the frontierQueue, visits the dequeued vertex, and then enqueues the vertex's adjacent vertices (if not already enqueued) to both queues, and repeats. If vertices are already in the discoveredQueue, then they are not added to the discoveredQueue when encountered again through a different connection.
        * vertices with possible connections (through intermediary vertices) are enqueued into the discoveredQueue.
        * the frontierQueue merely holds the current vertices to be visited.
        * the algorithm terminates once the frontierQueue is empty, meaning that no more possible connections exist to the starting vertex.
            * discovered - when a BSF algorithm first encounters a vertex.
            * frontier - the frontier consists of the vertices that have been discovered but not yet visited.
    > Wouldn't this make searches slow?
    > Also, how can you calculate how many valid BFS are possible when starting at a particular vertex? Is there a shortcut or formula?

![](https://i.gyazo.com/585f5feec3152319332cc77ad2bb47a3.png)
***