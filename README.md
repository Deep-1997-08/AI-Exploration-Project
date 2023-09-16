# Exploratory Mission in a Mysterious Terrain Gridworld
## AI Exploration Project

In this unique exploration, I venture into an unconventional gridworld characterized by a square grid of dimensions dim * dim. Each cell within this grid may be obstructed with a likelihood of 0.3, making navigation a challenge. The navigable cells are varied, potentially featuring flat, hilly, or forest terrains, differentiated within my model as 1 (blocked), 2 (flat terrain), 5 (hilly terrain), and 8 (forest terrain) in a NumPy array representation.

## Strategy and Implementation:
An autonomous robot embarks on a journey from a random starting point, aiming to uncover a concealed target within this complex gridworld. Employing the A* algorithm, I evaluate the feasibility of the robot's mission by ensuring the target is accessible from its initial position. Should the path to the target prove impassable, I reinitiate the process with a new grid configuration until a solvable scenario emerges.

### Navigational Intelligence:
- **Adaptive Learning**: The robot is equipped with a dynamic agent gridview, initially presuming an open path (all zeroes) and progressively adapting its knowledge based on encountered terrains and obstacles.
- **Sensory Perception**: The robot, though restricted in vision (blindfolded), gains insight into the terrain of an unblocked cell upon entry, enabling it to refine its gridview with actual terrain values (0’s for unknown, 1’s, 2’s, 5’s, and 8’s for known terrains).
- **Movement**: It maneuvers through the grid in four cardinal directions, with a strategy built on a `children_hash` that outlines potential next steps derived during the exploration process.

### Target Detection Mechanism:
- **Probabilistic Examination**: The robot inspects its current location for the target, contending with terrain-dependent false-negative rates (0.2 for flat, 0.5 for hilly, and 0.8 for forest terrains). Success means locating the target, as false positives are non-existent in this model.
- **Belief State Management**: A comprehensive belief state, structured as a dim*dim NumPy array, encapsulates the probability of the target's presence in each cell. This probabilistic map evolves with the robot's findings, guiding its subsequent moves.

### Collaborative Exploration:
Although operating under a shared belief framework, the distinct agent—each with its unique decision-making logic—navigates this gridworld independently, aiming to efficiently locate the hidden target through strategic exploration and analysis.
