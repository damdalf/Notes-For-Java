# 228 Reading: **WEEK 14** - Friday

## **DEPTH-FIRST SEARCH AND TOPOLOGICAL SORT:**
* to recap from the previous reading, recall that a Breadth-First Search is a graph traversal algorithm for a graph in which a starting vertex is visited, and then succeeding vertices are searched based upon their distance form the starting vertex, all while never revisiting a vertex. 
***
### **Depth-First Search (DFS):**
* DFS - a graph traversal algorithm that visits a starting vertex, then visits every vertex along each path starting from that vertex to the path's end before backtracking to the first previous vertex that is adjacent to unvisited vertices -> already visited vertices are not visited again.
    * the algorithm backtracks to the previous vertex upon reaching a terminating vertex (meaning that the vertex is not adjacent with any unvisited vertices), and then checks if there are any adjacent vertices that have not been visited yet. 
        * if there are, then one of these vertices is visited next, and the process repeats. 
* similar to BFS's, a traversal of a graph using a DFS is not unique... there are several possible DFS searches for (almost) any graph.
* normal implementation - an algorithm for depth-first search pushes the starting vertex to a stack. While the stack is not empty, the algorithm pops the vertex from the top of the stack. If the vertex has not already been visited, the algorithm visits the vertex and pushes the adjacent vertices to the stack.
    * unlike a BFS graph traversal, a DFS graph traversal does not use a frontierQueue and a discoveredQueue, but instead uses a visitedStack and adjacentStack.
    * if a vertex has already been visited it is still added to the adjacentStack, but it will not be pushed to the visitedStack again.
![](https://i.gyazo.com/766261ddb32a13f5c5afa534f2a3f640.png)

* recursive implementation - a recursive DFS can be implemented using the program stack instead of an explicit stack. The recursive DFS algorithm is first called with the starting vertex. If the vertex has not already been visited, the recursive algorithm visits the vertex and performs a recursive DFS call for each adjacent vertex.
    * if a vertex has yet to be visited, then RecursiveDFS is called for each adjacent vertex.
![](https://i.gyazo.com/22e88c7999442ad2fed71030e0f7a257.png)

***
### **Topological Sort:**
* topological sort - a type sort of a directed, acyclic graph produces a list of the graph's vertices such that for every edge from a vertex X to a vertex Y, X comes before Y in the list.
    * the graph MUST be directed and acyclic. 
    * such a graph can have more than one valid topological sort out.
    * if a vertex, or vertices, has / have no incoming edges / connections, then it / they must be the starting vertex / vertices.
    if a vertex, or vertices, has / have no outgoing edges / connections, then it / they must be the ending vertex / vertices.
        * this vertex / vertices must end the topological sort output.
    * Ex) a topological graph is commonly used for handling course prerequisites.
![](https://i.gyazo.com/71dcb68c88e188d7d2ad72e3716a4f9f.png)

* normal implementation - The topological sort algorithm uses three lists: a results list that will contain a topological sort of vertices, a no-incoming-edges list of vertices with no incoming edges, and a remaining-edges list. The result list starts as an empty list of vertices. The no-incoming-edges vertex list starts as a list of all vertices in the graph with no incoming edges. The remaining-edges list starts as a list of all edges in the graph.
    * the algorithm executes while the no-incoming-edges vertex list is not empty. For each iteration, a vertex is removed from the no-incoming-edges list and added to the result list. Next, a temporary list is built by removing all edges in the remaining-edges list that are outgoing from the removed vertex. For each edge currentE in the temporary list, the number of edges in the remaining-edges list that are incoming to currentE's terminating vertex are counted. If the incoming edge count is 0, then currentE's terminating vertex is added to the no-incoming-edges vertex list.
        * because each loop iteration can remove any vertex from the no-incoming-edges list, the algorithm's output is not guaranteed to be the graph's only possible topological sort.
            * when a vertex has no more incoming edges, it is added to the resultList.
            * when a vertex is the currentV, then outgoingEdges contains the vertex's outgoing edges and the corresponding vertices.
            * returns resultList which contains vertices.
![](https://i.gyazo.com/e048a753d7dc764603b8d1683103cd5a.png)
***