Download link :https://programming.engineering/product/homework-8-graph-algorithms/


# Homework-8-Graph-Algorithms
Homework 8: Graph Algorithms
For this assignment, you will code 4 different graph algorithms. This homework has many files included, so be sure to read ALL of the documentation given before asking questions.

Graph Data Structure

You are provided a Graph class. The important methods to note from this class are:

getVertices returns a Set of Vertex objects (another class provided to you) associated with a graph.

getEdges returns a Set of Edge objects (another class provided to you) associated with a graph.

getAdjList returns a Map that maps Vertex objects to Lists of VertexDistance objects. This Map is especially important for traversing the graph, as it will efficiently provide you the edges associated with any vertex. For example, consider an adjacency list where vertex A is associated with a list that includes a VertexDistance object with vertex B and distance 2 and another VertexDistance object with vertex C and distance 3. This implies that in this graph, there is an edge from vertex A to vertex B of weight 2 and another edge from vertex A to vertex C of weight 3.

Vertex Distance Data Structure

In the Graph class and Dijkstra’s algorithm, you will be using the VertexDistance class implementation that we have provided. In the Graph class, this data structure is used by the adjacency list to represent which vertices a vertex is connected to. In Dijkstra’s algorithm, you should use this data structure along with a PriorityQueue. When utilizing VertexDistance in this algorithm, the vertex attribute should represent the destination vertex and the distance attribute should represent the minimum cumulative path cost from the source vertex to the destination vertex.

Disjoint-Set Data Structure

In Kruskal’s algorithm, you will be using the DisjointSet class implementation that we have provided. You should use this data structure to determine whether vertices are already connected by a path (which means adding an edge between them would create a cycle) and to merge sets of edges together. These methods are find(…) and union(…) respectively.

Homework 8: Graph Algorithms

Due: See Canvas

Disjoint Set Example

Consider the graph below:

Original Graph

ds.union(vertexA, vertexB)

ds.union(vertexA, vertexC)

A

B

A

A



B B



C C C

Assume a DisjointSet object called ds is initialized with the vertices from above. Calling ds.union(vertexA, vertexB) joins vertex A and vertex B. Since vertex A and vertex B are in the same component, ds.find(vertexA).equals(ds.find(vertexB)) returns true. However, calling ds.find(vertexA).equals (ds.find(vertexC)) returns false since vertex A and vertex C are not in the same component. Calling ds.union(vertexA, vertexC) joins vertex C with both vertex A and vertex B. Therefore, ds.find(vertexA)

.equals(ds.find(vertexC)) returns true and ds.find(vertexB).equals(ds.find(vertexC)) returns true.

Search Algorithms (BFS, DFS)

Breadth-First Search is a search algorithm that visits vertices in order of “level”, visiting all vertices one edge away from start, then two edges away from start, etc. Similar to levelorder traversal in BSTs, it depends on a Queue data structure to work.

Depth-First Search is a search algorithm that visits vertices in a depth based order. Similar to pre/post/in-order traversal in BSTs, it depends on a Stack data structure to work. In your implementation, the Stack will be the recursive stack. It searches along one path of vertices from the start vertex and backtracks once it hits a dead end or a visited vertex until it finds another path to continue along. Your imple-mentation of DFS must be recursive to receive credit.

Single-Source Shortest Path (Dijkstra’s Algorithm)

The next algorithm is Dijkstra’s Algorithm. This algorithm finds the shortest path from one vertex to all of the other vertices in the graph. This algorithm only works for non-negative edge weights, so you may assume all edge weights for this algorithm will be non-negative. In order to keep track of the cumulative distance from the source vertex to the vertices you visit in this algorithm, you will need to use the VertexDistance data structure we are providing you. At any stage throughout the algorithm, the PriorityQueue of VertexDistance objects will tell you which vertex currently has the minimum cumulative distance from the source vertex.

There are two commonly implemented terminating condition variants for Dijkstra’s Algorithm. The first variant is where you depend purely on the PriorityQueue to determine when to terminate. You only terminate once the PriorityQueue is empty. The other variant, the classic variant, is the version where you maintain both a PriorityQueue and a visited set. To terminate, still check if the PriorityQueue is empty, but you must terminate early once all the vertices are in the visited set. You should implement the classic variant for this assignment. The classic variant, while using more memory, is usually more time efficient since there is an extra condition that could allow it to terminate early.

Homework 8: Graph Algorithms Due: See Canvas

Minimum Spanning Trees (Kruskal’s Algorithm)

A tree is a graph that is acyclic and connected. A spanning tree is a subgraph that contains all the vertices of the original graph and is a tree. An MST has two main qualities: being minimum and a spanning tree. Being minimum dictates that the spanning tree’s sum of edge weights must be minimized.

By the properties of a spanning tree, any valid MST must have |V | − 1 edges in it. However, since all undirected edges are specified as two directional edges, a valid MST for your implementation will have 2(|V | − 1) edges in it.

Kruskal’s algorithm builds the MST using a Disjoint-Set data structure. This is a greedy algorithm, and at each step, the algorithm adds the cheapest edge in the entire graph that does not cause a cycle. Cycle detection is done with a Disjoint-Set. If an edge connects vertices that are in the same set, then the algorithm continues to the next candidate edge. Unlike the previous algorithm, Dijkstras, Kruskal’s algorithm does not require the use of the VertexDistance data structure since it does not begin at a source vertex. Instead, it greedily selects edges with the lowest path costs until an MST is formed for each connected component.

Self-Loops and Parallel Edges

In this framework, self-loops and parallel edges work as you would expect. If you recall, self-loops are edges from a vertex to itself. Parallel edges are multiple edges with the same orientation between two vertices. In other words, parallel edges are edges that are incident on precisely the same vertices. These cases are valid test cases, and you should expect them to be tested. However, most implementations of these algorithms handle these cases automatically, so you shouldn’t have to worry too much about them when implementing the algorithms.

Visualizations of Graphs

The directed graph used in the student tests is:



1  4  6

2 3  5  7

The undirected graph used in the student tests is:



7

A B

5

8

3

C

F

2

D

E

6

1

Homework 8: Graph Algorithms Due: See Canvas

Grading

Here is the grading breakdown for the assignment. There are various deductions not listed that are incurred when breaking the rules listed in this PDF and in other various circumstances.

Methods:

BFS

15pts

DFS

15pts

Dijkstra’s

25pts

Kruskal’s

20pts

Other:

Checkstyle

10pts

Efficiency

15pts

Total:

100pts

Provided

The following file(s) have been provided to you. There are several, but we’ve noted the ones to edit.

GraphAlgorithms.java

This is the class in which you will implement the different graph algorithms. Feel free to add private static helper methods but do not add any new public methods, new classes, in-stance variables, or static variables.

Graph.java

This class represents a graph. Do not modify this file.

Vertex.java

This class represents a vertex in the graph. Do not modify this file.

Edge.java

This class represents an edge in the graph. It contains the vertices connected to this edge and its weight. Do not modify this file.

VertexDistance.java

This class holds a vertex and a distance together as a pair. It is meant to be used with Dijk-stra’s algorithm. Do not modify this file.

DisjointSet.java

This class represents a Disjoint-Set. It has the operations union and find. It is meant to be used with Kruskal’s algorithm. Do not modify this file.

DisjointSetNode.java

This class represents an element in a Disjoint-Set. It is meant to be used with Kruskal’s algo-rithm. Do not modify this file.

GraphAlgorithmsStudentTests.java

This is the test class that contains a set of tests covering the basic algorithms in the GraphAlgorithms

Homework 8: Graph Algorithms Due: See Canvas

class. It is not intended to be exhaustive and does not guarantee any type of grade. Write your own tests to ensure you cover all edge cases. The graphs used for these tests are shown above in the pdf.

Deliverables

You must submit all of the following file(s). Make sure all file(s) listed below are in each submission, as only the last submission will be graded. Make sure the filename(s) matches the filename(s) below, and that only the following file(s) are present. If there are multiple files, do not zip up the files before submitting; submit them all as separate files.

Once submitted, double check that it has uploaded properly on Gradescope. To do this, download your uploaded file(s) to a new folder, copy over the support file(s), recompile, and run. It is your sole responsibility to re-test your submission and discover editing oddities, upload issues, etc.

GraphAlgorithms.java
