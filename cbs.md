The CBS (Conflict-Based Search) algorithm is a multi-agent pathfinding algorithm used to find conflict-free paths for multiple agents on a grid. It is particularly effective in scenarios like robotics, video games, and automated warehouses where multiple agents need to navigate a shared environment without colliding.

### How it Works

1. **High-Level Search (Constraint Tree)**
   - CBS starts with a root node representing an initial solution where all agents plan their paths independently, ignoring conflicts.
   - Nodes in the constraint tree represent partial solutions with constraints added to avoid conflicts.
   - The algorithm uses a priority queue to explore nodes, starting with the root.

2. **Low-Level Search (Individual Path Finding)**
   - For each node, a low-level search is performed for each agent to find the shortest path from start to goal, given the current constraints.
   - This search is usually done using A* or another optimal pathfinding algorithm.

3. **Conflict Detection**
   - The algorithm checks for conflicts between agents' paths.
   - A conflict occurs when two agents occupy the same position at the same time.

4. **Constraint Addition**
   - When a conflict is detected, CBS adds constraints to resolve it.
   - Two new nodes are created: each node adds a constraint to avoid the conflict for one of the agents involved.
   - These new nodes are added to the priority queue for further exploration.

5. **Iterative Process**
   - The process repeats, with the algorithm selecting the node with the lowest cost from the priority queue, performing the low-level search, detecting conflicts, and adding constraints until a conflict-free solution is found or the priority queue is exhausted.

### Example

- Imagine two robots, A and B, navigating a grid.
- Initially, both robots plan their shortest paths independently.
- If a conflict is detected (e.g., both robots plan to occupy the same cell at the same time), CBS adds constraints to avoid the conflict.
- For instance, a constraint might prevent robot A from occupying a particular cell at a specific time, forcing it to find an alternative route.
- This process continues until a solution is found where no robots collide.

### Advantages

- CBS is optimal and complete for finding conflict-free paths.
- It efficiently handles scenarios with multiple agents, making it suitable for real-world applications.

### Limitations

- The computational complexity can increase significantly with the number of agents and the complexity of the environment.
- In highly constrained environments, finding a solution can become challenging.
