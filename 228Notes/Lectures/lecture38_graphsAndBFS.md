# 228 Notes: **WEEK 14** - Friday

## **GRAPHS AND BFS:**
* multigraph - a graph that allows multiple edges between two vertices.
* pseudograph - a multigraph that allows loops (edges to itself).
* subgraph - a subset of a graph with all edges attached to nodes.
* directed graphs and undirected graphs live in separate universes... study all definitions and concepts about them separately, there are too many differences between the two.
    * undirected graph that is connected - an undirected graph is connected if any node can be reached from any other node.
        * if the graph is not connected, the maximally connected (everything that is reachable is included) subgraphs are the connected components of the graph.
            * a connected component is a subgraph that is maximally connected (all nodes and edges are reachable from each other within the particular component).
            * connected component != connected subgraph
                * connected component == maximally connected subgraph
    * directed graphs cannot be 'connected', they can either be strongly connected or weakly connected.
        * strongly connected directed graph - a graph in which every vertex is reachable via a sequence of arrows from every other vertex.
            * if any vertex exists without having any inward connections, then the graph is not strongly connected.
        * weakly connected directed graph - we strip the arrow heads from all of the edges and convert the graph into an undirected graph. If the resulting undirected graph is connected, the source directed graph is weakly connected.
* weighted graphs - graphs that have some form of data stored in their edges.
***
* graph representations in memory
    * adjacency matrices - list the nodes along the horixontal and verttical axes of a boolean matrix (2d array). Best used when the graph is small in size or dense.
        * if an edge exists between the two vertices, then there connection should be marked as True, and False otherwise.
            * storage - O(|V|^2)
            * instantaneous O(1) lookup to checker whether two nodes are neighbors.
            * finding all neighbors is O(|V|), not very fast.
                * V = total number of vertices
        * for undirected graphs, we mirror the information along the forward-down diagonal of the matrix, so that (0, 2) and (2, 0) have the same value.
        * for directed graphs, this mirroring will not happen UNLESS the directed graph is an equivalent of an unidrected graph (2 opposing directed edges for each undirected edge).
    * adjacency list - each node is a slot in an array where we store a linked-list of all of the vertex's neighbors.
        * storage - O(|E| + |V|)
        * if we want to find if two nodes are neighbors we check IN PARALLEL whether the next neighbor is one of the two targets:
            * check 1st neighbor of u and v
            * check 2nd neighbor of u and v
            * check 3rd neighbor of u and v
                * In this way, as soon as we exhaust the shorter of the two collections of neighbors, we are done checking in O(min(degree(u), degree(v))) vs. O(1) of an adjacency matrix.
        * if we want to find the number of neighbors that exist for a particular vertex, we must enumerate all elements at a particular slot, in O(degree(v)) vs. the larger O(|V|) of an adjacency matrix.
        * we can upgrade the adjacency list representation by using a hash set of nodes as the array and a hash map of neighbors as the linked-list.
            * then, we can do the following:
                * look up a vertex in O(1)
                * check if a vertex is a neighbor of a particular vertex in O(1)
                can also look up a particular edge in O(1)
                * does not help with finding all neighbors of a vertex
***
* sparse graphs - we start with isolated nodes and add a few edges here and there.
* dense graphs - we start with a fully populated graph where all possible edge connections have been made, and a remove a few edges here and there.
    * less waste is wasted in a dense graph, because most pairs (u, v) are true.
***
* Breadth-First Search (BFS) - a graph traversal algorithm is a level-order traversal where you can have multiple edges coming into a vertex. 
    * BFS answers the following question: "What are the shortest distances to any node in the graph from my designated starting node?"
***
