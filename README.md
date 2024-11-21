# N-Puzzle Path Search

The objective of this Computational Intelligence lab was to implement and compare different path search algorithms to solve the N-Puzzle problem. Specifically, we were required to:
1. Implement different Path Search Algorithms.
2. Use the algorithms to solve a (8-puzzle) configuration.
3. Measure and compare the performance of each algorithm based on solution quality, total cost, and efficiency.


## Problem Setup

### Puzzle Configuration
- **Puzzle Dimension**: 3x3 (8-puzzle)
- **Initial State**:
```
2 3 4
6 0 1
7 5 8
```
- **Goal State**: Standard ordered configuration (1-8, with 0 as empty space)
```
1 2 3
4 5 6
7 8 0
```

## Algorithm Performance Comparison

### Performance Metrics
- **Solution Quality**: Number of moves in the solution path
- **Total Cost**: Number of states evaluated during search
- **Efficiency**: Ratio of solution quality to total cost (lower is better)

### Results Summary

| Algorithm | Solution Quality | Total Cost | Efficiency | 
|-----------|-----------------|------------|------------|
| A* Search | 16 moves | 92 states | 0.1739 |
| DFS | 58 moves | 24,141 states | 0.0024 |
| BFS | 16 moves | 12,670 states | 0.0013 |

