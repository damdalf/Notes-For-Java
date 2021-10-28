# 228 Reading: **WEEK 10** - Friday

## **Binary Trees:**
***
### **DEFINITIONS:**

* binary tree - *a type of list in which each node has up to two children, known as a left child and a right child.*.
    * leaf - *a node with no children*.
    * internal node - *a node with at least one child, which includes the root node*.
    * parent - *a node with a child is said to be that node's parent*.
    * ancestor - *This includes the node's parent, the parent node's parent, and so forth, all the way up to the tree's root*.
    * root - *the one tree node without a parent... ie. THE ancestor / top node*.
* Terminology
    * edge - *the link fromm a node to a child*.
    * depth - *the number of edges on the path from the root to the node*.
    * level - *all nodes with the same depth form a level*.
    * height - *the largest depth of any node*.
* Special types of binary trees
    * full - *a binary tree is full if every node contains 0 or 2 children*.
    * complete - *a binary tree is complete if all levels, except possibly the last level, contain all possible nodes and and all nodes in the last level are as far left as possible*.
    * perfect - *a binary tree is perfect if all internal nodes have two children and all leaf nodes are at the same level*.
    ![](https://zytools.zybooks.com/zyAuthor/DataStructures/54/IMAGES/embedded_image_1pseudo_47f8fc17-cd79-46bb-35ac-4dd4e94fc720_BGFBkBEIuZ0Sop5yq38l.png)
***
### **CODE AND CONCEPTS:**
>Here is what a binary tree looks like:
![](https://i.gyazo.com/e805fb94cf93d91f210f23ca3820005a.png)

***
## **Tree Applications:**
* File systems
    * All files are leaf nodes, only empty directories will be leaf nodes.
    * A directory containing 1 or more files or directories is an internal node.
    * Unlike a binary treem a file system tree must support a variable number of children per directory node.

* Binary space partitioning (BSP) - technique of repeatedly separating a region of space into 2 parts and cataloging objects contained within the regions.
    * BSP tree - a binary tree used to store information for binary space partitioning. Each node in a BSP tree contains information about a region of space and which objects are contained in the region.
