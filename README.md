# Swarm Intelligence: Emergent Collective Motion & Decision-Making

Name: Martín Campos 
Affiliation: Univesidad Nacional Autónoma de México (UNAM)

Main aim:

The main result is achive swarm intelligence, it established that coherent collective motion requires no leader, no plan, and no individual that perceives the group.

Flock would be capable of:

Split around obtacles and reformes on the far side
Change direction as a body
Recover coherence after disroption

This behaviors will not be programmed!

Theoretical Framework:

Boids is an agent-based model of flocking, developed by Craig Reynols in 1986 and presented at SIGGRAPH in 1987 as Flocks, Herds, and Schools: A Distributed Behavioral Model. Each simulated bird — a boid, for bird-oid object — follows three steering rules that reference only its nearby neighbours. Flocking is what happens.

Agent-based modeling  simulates a system by representing its individuals explicitly — their state, their rules, their interactions — and letting aggregate behaviour arise from running them. It stands opposed to equation-based modeling, which posits aggregate variables and writes down their dynamics directly.

Three elements. Agents are autonomous entities with attributes and behaviours. The environment is the space they occupy and act upon. Rules govern what they do.


Methodological Framework:


Boids.
The three local rules
Each boid computes three steering behaviours over the flockmates within its perception radius.

Separation steers away from crowding, with force increasing as neighbours close. This prevents collision and maintains spacing.

Alignment steers toward the average heading of neighbours. This produces parallel motion and coordinated turns.

Cohesion steers toward the average position of neighbours. This holds the flock together, balancing separation.

Each rule uses only local information. No boid knows the flock’s shape, size, or heading. Locality is what makes Boids scale and what makes its behaviour emergent rather than choreographed.c

For boid i at position pi with velocity vi:

Separation, over neighbours Ni within the separation radius, with inverse-square repulsion:
Fsep,i= j∈Ni∑[pi−pj)/ ∥pi−pj∥^2 pi−pj]

Alignment, over neighbours Ai, within the alignment radius:
F align,i = [∣Ai∣ ∑ j∈A i vj/  ∣Ai∣] − vi

Cohesion, over neighbours Ci, within the cohesion radius:
Fcoh,i = [∑ j∈Ci pj/∣Ci∣]−pi

Combined by weights, and integrated:

Fi =wsepFsep,i+walignFalign,i+wcohFcoh,i

Collective Decision-Making Model
The most common commitment mechanism is a threshold. Support for an option accumulates; once it crosses a quorum T, the group commits.

P(commit∣n)=
{0   n<T
f(n) n≥T
  
 
where n is the support level and f increases above threshold. The nonlinearity is the point: it converts a graded, noisy signal into a categorical, decisive action.

Quorums do four things at once. They prevent premature commitment, forcing adequate evaluation. They filter noise, distinguishing a real trend from a fluctuation. They enable decisiveness, providing a sharp transition from deliberation to action rather than an indefinite drift. And they create hysteresis — reversing a decision requires more evidence than making it did, which stabilizes the group against thrashing.

Choosing T is a speed–accuracy tradeoff and nothing else. Low thresholds decide fast and wrong; high thresholds decide slowly and right.

# Boids-Simulation
Flock simulation using Boids Model 
