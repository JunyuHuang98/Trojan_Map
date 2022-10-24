# Trojan Map
This project is based on the final project of EE538(Computing Principles for Electrical Engineers) in spring 2022 at University of Southern California
Author: Junyu Huang

# Overview
## Functionalities
- Auto Complete location names
- Find Coordinates
- Calcualte Shortest Path with Dijkstra algorithm and Bellman-ford algorithm
- Cycle Detection in a subgraph
- Topological Sort
- Travelling salesman problem with Brute-force, earlybacktracking and 2-opt

## The Data Structure

Each point on the map is represented by the class **Node** shown below and defined in [trojanmap.h](src/lib/trojanmap.h).

```cpp
class Node {
 public:
  Node(){};
  Node(const Node &n) {
    id = n.id;
    lat = n.lat;
    lon = n.lon;
    name = n.name;
    neighbors = n.neighbors;
    attributes = n.attributes;
  };
  std::string id;    // A unique id assign to each point
  double lat;        // Latitude
  double lon;        // Longitude
  std::string name;  // Name of the location. E.g. "Bank of America".
  std::vector<std::string>
      neighbors;  // List of the ids of all neighbor points.
  std::unordered_set<std::string>
      attributes;  // List of the attributes of the location.
};
```

# File Description
- ```main.cc``` is the main function.
- ```trojanmap.h```,```trojanmap.cc``` are the source files for the graph algorithms

# Environment


# Time Complexity Analysis
## Auto Complete location names
Time complexity: 

## Find Location
This function is implemented to find the latitude and longitude of the location name we enter.
**Time complexity:** $O(n)$

## Calculate Shortest Path
### 1. Dijkstra
Here we are using "priority queue" to implement Dijkstra. We should input the source node and destination node and the output should be the shortest path and distance between these two locations.

**Time complexity:** $O((m+n)*logn)$. m represents the number of edges and n represents the number of nodes.

### 2. Bellman-Ford

**Time complexity:** $O(n*m)$, n represents the number of nodes and m represents the number of edges in the map.

## Cycle Detection

## Topological Sort

## Travelling salesman

### 1. Brute force
Solving TSP with brute-force is similar to permutation. We need to permutate all possible results. Brute-force algorithm can guarantee the accuracy of the result, but the runtime for it is horrible.
**Time complexity:**  $O(n!)$, where n represents the number of nodes in the graph.
### 2. EarlyBacktracking
Solving TSP with earlybacktracking is similar to brute-force. We can skip some cases which do not meet the requirement to speed up the process. But in worst case, the runtime for it is the same as brute-force.
**Time complexity:**  $O(n!)$, where n represents the number of nodes in the graph.
### 3. 2-opt
Solving TSP with 2-opt heuristic algorithm is much more efficient than using brute-force and earlybacktracking. But it would result in less accuracy.
**Time complexity:**  $O(n^2)$, where n represents the number of nodes in the graph.
