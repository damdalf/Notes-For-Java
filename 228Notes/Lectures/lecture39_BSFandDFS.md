# 228 Notes: **WEEK 15** - Monday

## **BREADTH-FIRST SEARCH & DEPTH-FIRST SEARCH:**
* **the final is not cumulative, everything since second exam. maybe some quirky Big O questions. tuesday night review session. also something about a questionaire worth 1% of the grade.**
***
## **Breadth-First Search:**
* BFS - shortest path to each node from node s for source (starts at distance of 0, for the source node, then distance of 1, then distance of 2, and so forth...)
    * can tell us if two nodes are connected
    * not recursive
    * only finds one connected component
    * level-order traversal for trees upgraded for arbitrary graphs with three book-keeping arrays
        * colorArray(v) - contains the states of the nodes
            * white - untouched
            * grey - processing
            * black - finished
        * OR, you could create a container class for the Nodes that contains color and distance.
        * distanceArray(v) - contains how many edges were in the path to v (for any v)
        * predecessorArray(v) - contains the predecessor of v along the shortest path. Constructed by getting a predecessor of a predecessor of a predecessor and so forth...
        * also need a queue since it is level-order traversal.
* BFS applications:
    * 
* Inuition for BFS - never follows a further edge before processing all the near edges (the queue ensures this), and that for any white node discovered we have found a shortest path.
***
## **Depth-First Search:**
* DFS - covers the whole graph, and not just a single connected component. Visualize you are working night-shift and must walk the corridors of your building to turn off the lights, starting at the end of the corridor to ensure you are always in the light until you are done.
    * recursive
    * no attached processing data structure like a queue
    * we drop the distance array, because distances discovered with DFS are not guarranteed to be the smallest / shortest, and thus are not as interesting.
        * however, we still use colorArray and predecessorArray (or create the contained class for Nodes to include this data).
* DFS applications: (all applications require modifications to the basic  code for DFS)
    * find all connected components
        * need a component(v) array which will be a third book-keeping array; we need a variable label for each component, eg. component_num = -1.
            * component_num would be incremented everytime we enter the outermost loop. Then, during that iteration component(v) = component_num for every white node that we process.
                * as soon as the component has been traveled, we increment component_num, and if there are any outstanding white nodes, they will constitute a separate component, e.g. component_num 1, 2, 3.
                    * the resulting sequence of predecessors in a DFS search make a DFS tree OR a DFS forest if we have multiple components. Those trees do not contain the shortest paths.
    * reachability of node v from s (source node)
        * modify the code to have only 1 iteration of the outermost loop. After we finished the recursive DFS, we check if v is black. If it is not, then v is not reachable.

    > BFS can answer the same exact question without any modifications: we run BFS starting at s, and after it finishes we check dist(v)... If it is inifinity, v is not reachable. 

    * cycle detention
        * as soon as I find an edge to a grey node, I have found a cycle. We can amend the BFS code like so:
            if color(v) == white
                ...process v
            else if color(v) == gray
                cycle = true
    * topological sort (next lecture)

* for directed graphs, we CAN have edges to black nodes, which are called forward edges. And we can have cross edges (from unrealted node to a black unrelated node, e.g. two siblings or completely unrealted nodes).

    > the relationships depend on the order of search / discovery.
    * tree edges - are those in the DFS forest
    * back edges - those that go from a vertex to one of its ancestors
    * forward edges - go from a vertex to one of its descendants
    * cross edges - all other edges (edge that connects two nodes where neither node is each other's descendant or ancestor)
        * these edges are identified when a connection is found between two nodes that are already black (processed).
* undirected graphs, we only have edges to a white or a grey node. We never have edges to a black node. Because that black node would have already turned OUR node black from the other direction of the edge, before turing itself black.

* Inuition for DFS - it greedily follows a sequence of edges until it exhausts it (like a dog getting lost in the forest). It will never branch out before finishing its current path. When it branches out, it will be in the furthest location from the source for that particular path.
***
"You're going to throw me a harder one after two hours? I can do something else in my free time, like smoke weed. Kidding, I don't smoke weed. Allegedly I don't smoke weed." - Georgi Batinov