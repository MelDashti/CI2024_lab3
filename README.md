# N-Puzzle Path Search

The objective of this Computational Intelligence lab was to implement and compare different path search algorithms to solve the N-Puzzle problem. Specifically, we were required to:

1. Implement different Path Search Algorithms.
2. Use the algorithms to solve different n-puzzle configurations.
3. Measure and compare the performance of each algorithm based on solution quality, total cost, and efficiency.

## Problem Setup

### Initial Implementation (3x3 Puzzle)

#### Puzzle Configuration
- Puzzle Dimension: 3x3 (8-puzzle)
- Initial State:
```
2 3 4
6 0 1
7 5 8
```
- Goal State: Standard ordered configuration (1-8, with 0 as empty space)
```
1 2 3
4 5 6
7 8 0
```

### Performance Metrics
- Solution Quality: Number of moves in the solution path
- Total Cost: Number of states evaluated during search
- Run time: The amount of time it took for evaluation and finding a solution path.

### Results for 3x3 Puzzle

| Algorithm | Solution Quality | Total Cost | Run Time |
|-----------|-----------------|------------|------------|
| A* Search | 12 moves | 42 states  |  0.1   |
| DFS max depth 60 | 50 moves | 138444 states | 3.3 s |
| BFS | 12 moves | 2062 states | 6.6s |

- Overall, **A\*** shows clear advantages in both computational efficiency and solution optimality for the 3x3 puzzle.

## Solvability Analysis and Implementation

During the implementation of larger puzzles (4x4 and 5x5), I encountered a significant challenge: some randomly generated initial states were unsolvable. This became apparent when the A* algorithm couldn't find a solution even after running for over an hour.

### Solvability Detection
To address this issue, I implemented a solvability check using the concept of inversions. An inversion occurs when a tile precedes another tile with a lower number in the puzzle configuration. The solvability rules are:
- For odd-sized puzzles (e.g., 3x3, 5x5):
  - The puzzle is solvable if the number of inversions is even
- For even-sized puzzles (e.g., 4x4):
  - The puzzle is solvable if (blank_row_from_bottom + inversions) is even

### Implementation Enhancement
I modified the initialization process to:
1. Generate an initial random state
2. Check its solvability
3. If unsolvable, perform additional randomization attempts (max 10)
4. Continue until a solvable state is found or maximum attempts are reached


## Extended Results (Larger Puzzles)

### 4x4 Puzzle Results

| Algorithm | Solution Quality | Total Cost | Run Time |
|-----------|------------------|------------|----------|
| A* Search | 50 moves         | 4,652,822 states | 17.7 minutes |
| DFS (max depth 120) | -                | -          | >150 minutes (timed out) |
| BFS       | -                | -          | >140 minutes (timed out) |

### Notes
- **DFS and BFS:** Both algorithms were unable to complete the search within a reasonable time for the 4x4 puzzle. DFS ran for over 150 minutes and BFS for over 140 minutes before being manually terminated. No solution was found in either case.
- **A\*** significantly outperformed BFS and DFS, successfully finding a solution in 17.7 minutes despite evaluating over 4.6 million states.
- **Scalability Issues:** As the puzzle size increases, the performance gap between A\* and other algorithms widens significantly. BFS and DFS become impractical for larger puzzles.

## Observations
1. **Solvability Check:** The implementation of a solvability check was crucial for larger puzzles to avoid wasting computational resources on unsolvable configurations.
2. **Algorithm Performance:** A\* proved to be the most efficient algorithm for larger puzzles due to its heuristic-guided search.
3. **Scalability Challenges:** The exponential growth in the state space makes uninformed search algorithms like BFS and DFS infeasible for larger puzzles.
