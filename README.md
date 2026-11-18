# Swarm Intelligence: Emergent Collective Motion & Decision-Making

**Name:** Martín Campos  
**Affiliation:** National Autonomous University of Mexico (UNAM) 

---

## Main Aim

The primary objective of this project is to achieve **swarm intelligence**, establishing that coherent collective motion requires no leader, no central plan, and no individual agent capable of perceiving the entire group.

Through local interactions alone, the simulated flock demonstrates emergent capabilities to:
* **Split around obstacles** and reform smoothly on the far side.
* **Change direction** cohesively as a single body.
* **Recover coherence** after external disruption.

> **Note:** None of these macroscopic behaviors are explicitly programmed; they emerge naturally from local rules.

---

##  Theoretical Framework

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

$$
\mathbf{F}_{sep, i} = \sum_{j \in N_i} \frac{\mathbf{p}_i - \mathbf{p}_j}{\|\mathbf{p}_i - \mathbf{p}_j\|^2}
$$

**Alignment**, over neighbors $A_i$ within the alignment radius:

$$
\mathbf{F}_{align, i} = \left( \frac{1}{|A_i|} \sum_{j \in A_i} \mathbf{v}_j \right) - \mathbf{v}_i
$$

**Cohesion**, over neighbors $C_i$ within the cohesion radius:
$$
\mathbf{F}_{coh, i} = \left( \frac{1}{|C_i|} \sum_{j \in C_i} \mathbf{p}_j \right) - \mathbf{p}_i
$$

**Total Steering Force**, combined by scalar weights and integrated over time:

$$
\mathbf{F}_i = w_{sep}\mathbf{F}_{sep, i} + w_{align}\mathbf{F}_{align, i} + w_{coh}\mathbf{F}_{coh, i}
$$

### 2. Collective Decision-Making Model.

The most common commitment mechanism in collective systems is a quorum threshold. Support for a given option accumulates among individuals; once it crosses a threshold $T$, the group commits to the action:
$$
P(commit \mid n) = \begin{cases} 0 & \text{if } n < T \\ f(n) & \text{if } n \ge T \end{cases}
$$

where $n$ represents the current support level and $f(n)$ is a monotonically increasing function above the threshold. This nonlinearity is essential: it converts a graded, noisy signal into a categorical, decisive collective action.

### Role of Quorum Thresholds
Quorums perform four critical functions simultaneously:
1. **Prevent premature commitment:** Forces adequate evaluation before acting.
2. **Filter noise:** Distinguishes a genuine environmental trend from random fluctuations.
3. **Provides a sharp transition** from deliberation to action rather than indefinite drift.
4. **Create hysteresis:** Reversing a decision requires more evidence than making it did, stabilizing the group against rapid oscillation (thrashing).
The Speed–Accuracy Tradeoff: Choosing the threshold $T$ governs the balance between reaction speed and decision quality. Low thresholds lead to fast but error-prone decisions; high thresholds yield slow but accurate collective choices.EOF

