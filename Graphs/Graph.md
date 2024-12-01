
## Adjacency matrix representation
![[Pasted image 20241201162422.png]]
## Adjacency list representation

![[Pasted image 20241201162553.png]]

- Edge lookup(checking if an edge exists between vertex A and vertex B) is extremely fast in adjacency matrix representation but we have to reserve space for every possible link between all vertices(V x V), so it requires more space.
- An adjacency list is efficient in terms of storage because we only need to store the values for the edges. For a graph with millions of vertices, this can mean a lot of saved space.

> The total number of spanning trees with `n` vertices that can be created from a complete graph is equal to $$n^(n-2)$$

![[Pasted image 20241201162948.png]]

## Spanning Tree Applications

- Computer Network Routing Protocol
- Cluster Analysis
- Civil Network Planning

## Minimum Spanning tree Applications

- To find paths in the map
- To design networks like telecommunication networks, water supply networks, and electrical grids.

## Strongly Connected Components

A strongly connected component is the portion of a directed graph in which there is a path from each vertex to another vertex. **It is applicable only on** [**a directed graph**](https://www.programiz.com/dsa/graph).

![[Pasted image 20241201163747.png]]