
# Ant_Colony_Optimization

A scheduler built using Ant Colony Optimization algorithm, to manage microservices in a contanarized environment.

## What is ACO?

Ant Colony Optimization (ACO) is a problem-solving technique inspired by how real ants find food. In ACO, simulated ants explore solutions like paths or task assignments, leaving behind a virtual pheromone trail indicating desirability. Each ant considers this pheromone trail along with a problem-specific guide (heuristic) to choose its path. Better solutions (lower cost) strengthen the pheromone trails on those paths, guiding future ants towards better solutions over time. This versatile technique is useful for various optimization problems like routing, scheduling, and assignment.

## Summary of work

The algorithm simulates a scenario where "elements" (like tasks or services) need to be assigned to "targets" (machines or nodes) while considering factors like resource utilization and potentially other problem-specific objectives.

stages of works are:

1. Initialization: It starts by setting up a "pheromone matrix" that reflects the desirability of assigning each element to each target. Initially, these values are low (often 0.1). Additionally, it initializes variables to track the best solution found so far, solution costs, and the number of iterations to be performed.

2. Main Loop (Iterative Search): This is the core of the algorithm and runs for a predefined number of iterations. In each iteration, it simulates multiple "agents" (artificial ants) exploring possible solutions. For each agent:

   a. An empty list is created to keep track of element assignments for each target. Initial available resources (processing power and storage) of each target are retrieved.
   
   b. The agent then considers each element one by one. For each element, it calculates the probability of assigning it to every target. This probability is influenced by two factors: existing pheromone levels (indicating past desirability) and a heuristic that considers how well the element's resource needs fit the target's remaining resources.
   
   c. Based on these probabilities, the agent selects a target for the element (often using a random selection weighted by the probabilities). The chosen target's remaining resources are then updated by subtracting the element's resource requirements. Finally, the element is added to the assignment list for the chosen target.
   
   d. After processing all elements, the agent calculates the total cost of its solution, considering factors like resource utilization, load balancing, and potentially other problem-specific objectives.
   
   e. The agent's solution (assignment list and cost) is stored, and the algorithm checks if this solution has a lower cost than the current best solution. If so, the best solution is updated. Similarly, the worst solution is also tracked.

4. Pheromone Update: After all agents complete their assignments in an iteration, the pheromone levels in the matrix are updated. This update is based on the quality of the solutions found. Solutions with lower costs (better assignments) lead to increased pheromone levels on the paths used in those solutions, making them more attractive for future exploration by the agents.

5. Return Best Solution: Once all iterations are complete, the algorithm returns the best solution (assignment list) found with the lowest cost. This represents the optimal (or near-optimal) way to assign the elements to the targets based on the defined objectives.
