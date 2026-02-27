# ✈️ Flight Connection Optimizer

## Overview

Flight Connection Optimizer is a Java-based airline network analysis system powered by SQL Server and a graphical user interface.

The project models a real-world flight network as a weighted directed graph and applies advanced graph algorithms to compute optimal routes, analyze connectivity, and evaluate structural network properties.

This system simulates the core logic behind airline booking engines.

---

## System Architecture

The application follows a layered architecture:

Presentation Layer  
→ Java UI (JavaFX / Swing)  

Business Logic Layer  
→ Graph construction  
→ Dijkstra (Cheapest & Fastest)  
→ BFS (K connections)  
→ Articulation Points detection  
→ MST (Bonus)  

Data Layer  
→ SQL Server  
→ JDBC  
→ Relational schema with referential integrity  

---

## Database Schema (SQL Server)

### Airports
- AirportCode (PK)
- AirportName
- City
- Country

### Routes
- RouteID (PK)
- SourceAirport (FK)
- DestinationAirport (FK)
- Cost (DECIMAL)
- Duration (INT)

Constraints:
- Minimum 30 airports
- Minimum 80 routes
- Foreign key enforcement
- Directed routes

---

## Graph Model

- Directed weighted graph
- Adjacency list representation
- Two independent edge weights:
  - Cost
  - Duration

The graph is dynamically built from the database at runtime.

---

## Core Features

### 1. Cheapest Route
Dijkstra’s algorithm using cost as edge weight.

Time Complexity:
O((V + E) log V)

---

### 2. Fastest Route
Dijkstra’s algorithm using duration as edge weight.

Time Complexity:
O((V + E) log V)

---

### 3. Reachability Within K Connections
Breadth-First Search (BFS) with depth limitation.

Time Complexity:
O(V + E)

---

### 4. Critical Airports Detection
Articulation point detection using DFS-based approach.

Identifies airports whose removal disconnects part of the network.

Time Complexity:
O(V + E)

---

### 5. Robust Edge Case Handling
- Non-existent airport
- No route between airports
- Source equals destination
- Disconnected components
- Empty dataset

---

## Bonus Features

### Minimum Spanning Tree
Prim’s or Kruskal’s algorithm (network structural analysis).

Time Complexity:
O(E log V)

---

### Travel Budget Mode
Modified Dijkstra to compute all reachable destinations within a specified cost constraint.

---

## Technology Stack

- Java 17+
- JavaFX / Swing
- SQL Server
- JDBC
- PriorityQueue (Min-Heap)
- DFS / BFS
- Graph Theory Algorithms

---

## Complexity Summary

| Operation | Complexity |
|-----------|------------|
| Graph Construction | O(V + E) |
| Dijkstra | O((V + E) log V) |
| BFS | O(V + E) |
| Articulation Points | O(V + E) |
| MST | O(E log V) |

---

## Project Goals

- Apply graph theory to a real-world scenario
- Integrate database systems with algorithmic computation
- Design a layered software architecture
- Handle real-world edge cases
- Analyze algorithmic complexity

---

## Authors

Artyom Mkrtchyan and Mane Mazmandyan
Faculty of Computer Science  
2026
