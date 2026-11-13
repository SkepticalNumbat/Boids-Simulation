# Boids-Simulation
Flock simulation using Boids Model
 Swarm Intelligence: Emergent Collective Motion & Decision-Making

**Name:** [Tu Nombre Aquí]  
**Affiliation:** [Tu Institución / Universidad Aquí]  

---

## Main Aim

The primary objective of this project is to achieve **swarm intelligence**, establishing that coherent collective motion requires no leader, no central plan, and no individual agent capable of perceiving the entire group.

Through local interactions alone, the simulated flock demonstrates emergent capabilities to:
* **Split around obstacles** and reform smoothly on the far side.
* **Change direction** cohesively as a single body.
* **Recover coherence** after external disruption.

> **Note:** None of these macroscopic behaviors are explicitly programmed; they emerge naturally from local rules.

---

## Theoretical Framework

### The Boids Model
**Boids** is an agent-based model of flocking developed by Craig Reynolds in 1986 and presented at SIGGRAPH in 1987 (*"Flocks, Herds, and Schools: A Distributed Behavioral Model"*). Each simulated bird—a *boid* (bird-oid object)—follows three simple steering rules that reference only its nearby neighbors. Flocking is the emergent result.

### Agent-Based Modeling (ABM)
Agent-based modeling simulates a complex system by representing its individuals explicitly—their state, rules, and interactions—and letting aggregate behavior arise from executing them. It stands in contrast to equation-based modeling, which posits aggregate variables and writes down their global dynamics directly.

An ABM consists of three core elements:
1. **Agents:** Autonomous entities with specific attributes and behaviors.
2. **Environment:** The spatial domain the agents occupy and act upon.
3. **Rules:** The local logic governing how agents interact with each other and their environment.

---

##  Methodological Framework

### 1. Boids: The Three Local Rules

Each boid computes three steering behaviors based solely on flockmates within its local perception radius:

* **Separation:** Steers away from crowding, with repulsive force increasing as neighbors get closer. This prevents collisions and maintains minimum spacing.
* **Alignment:** Steers toward the average heading of local neighbors. This produces parallel motion and coordinated turns.
* **Cohesion:** Steers toward the average position (center of mass) of local neighbors. This holds the flock together, balancing separation.

Because no boid knows the flock's overall shape, size, or heading, **locality** is what allows the system to scale and makes its behavior truly emergent rather than choreographed.

#### Mathematical Formulation
For boid $i$ at position $\mathbf{p}_i$ with velocity $\mathbf{v}_i$:

**Separation**, over neighbors $N_i$ within the separation radius, using inverse-square repulsion:

\mathbf{F}_{\text{sep}, i} = \sum_{j \in N_i} \frac{\mathbf{p}_i - \mathbf{p}_j}{\lVert \mathbf{p}_i - \mathbf{p}_j \rVert^2}

\mathbf{F}_{\text{align}, i} = \left( \frac{1}{|A_i|} \sum_{j \in A_i} \mathbf{v}_j \right) - \mathbf{v}_i

\mathbf{F}_{\text{coh}, i} = \left( \frac{1}{|C_i|} \sum_{j \in C_i} \mathbf{p}_j \right) - \mathbf{p}_i

\mathbf{F}_i = w_{\text{sep}}\mathbf{F}_{\text{sep}, i} + w_{\text{align}}\mathbf{F}_{\text{align}, i} + w_{\text{coh}}\mathbf{F}_{\text{coh}, i}



Collective Decision-Making Model
The most common commitment mechanism is a threshold. Support for an option accumulates; once it crosses a quorum T, the group commits.

P(\text{commit} \mid n) = \begin{cases} 0 & \text{if } n < T \\ f(n) & \text{if } n \ge T \end{cases}
  
 
where n is the support level and f increases above threshold. The nonlinearity is the point: it converts a graded, noisy signal into a categorical, decisive action.

Quorums do four things at once. They prevent premature commitment, forcing adequate evaluation. They filter noise, distinguishing a real trend from a fluctuation. They enable decisiveness, providing a sharp transition from deliberation to action rather than an indefinite drift. And they create hysteresis — reversing a decision requires more evidence than making it did, which stabilizes the group against thrashing.

Choosing T is a speed–accuracy tradeoff and nothing else. Low thresholds decide fast and wrong; high thresholds decide slowly and right.


