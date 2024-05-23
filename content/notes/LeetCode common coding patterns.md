---
title: LeetCode common coding patterns
draft: true
tags:
  - leetcode
  - work_in_progress
related:
  - "[[Interviews Prep]]"
timestamp: "202403120931"
---

# LeetCode 5 common coding patterns

## Outline
1. [[#1. Sliding Window|Sliding Window]]
2. [[#2. Two Pointers|Two Pointers]]
3. [[#3. Binary Search|Binary Search]]
4. [[#4. Depth First Search|Depth First Search]]
5. [[#5. Dynamic Programming|Dynamic Programming]]

## 1. Sliding Window

## 2. Two Pointers

## 3. Binary Search

## 4. Depth First Search

## 5. Dynamic Programming

---

# Other coding patterns
## BFS (Breadth First Search)
```python
from collections import deque

# Function to perform Breadth First Search on a graph
# represented using adjacency list
def bfs(adjList, startNode, visited):
    # Create a queue for BFS
    q = deque()

    # Mark the current node as visited and enqueue it
    visited[startNode] = True
    q.append(startNode)

    # Iterate over the queue
    while q:
        # Dequeue a vertex from queue and print it
        currentNode = q.popleft()
        print(currentNode, end=" ")

        # Get all adjacent vertices of the dequeued vertex
        # If an adjacent has not been visited, then mark it visited and enqueue it
        for neighbor in adjList[currentNode]:
            if not visited[neighbor]:
                visited[neighbor] = True
                q.append(neighbor)
```

--- 
# References
- [YouTube - Top 5 MOST Asked Coding Patterns for Interviews (in 2024) - Algorithm Implementation Examples](https://www.youtube.com/watch?v=-lcAuPXsQ-8)