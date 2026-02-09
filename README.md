# MPI Parallelization of an MD Code

In the `src/main.cpp` file, you will find a very simple molecular dynamics code that uses a Lennard-Jones potential to account for interactions between particles.

## Task 1

Parallelize the code using **MPI**.

Your grade for this assignment will be partially based on the degree to which your parallelization efforts represent an efficient and intelligent application of MPI parallelization, including considerations for load balancing, communication costs, and memory usage.
Ensure that in your parallelized code, the amount of memory required for the simulation does not substantially increase when the code is run on larger numbers of ranks.
In particular, when running on large numbers of ranks, no rank should ever hold the entire set of particle coordinates simultaneously (this same rule also applies to the forces and velocities).
You will likely find that these requirements necessitate substantially refactoring the code.

Note that in the double loop that evaluates forces, this code actually evaluates the interaction between each pair of atoms twice:

```c++
        for (int iparticle = 0; iparticle < nparticles; ++iparticle) {
            for (int jparticle = 0; jparticle < nparticles; ++jparticle) {
                if ( iparticle != jparticle ) { // Only compute the interactions between different particles
```

In addition to parallelizing the code, modify it so that the interaction between each unique pair of particles is only evaluated once.

The initial velocities for the system are generated in such a way that you should get the same results regardless of the number of ranks you run on (at least, within the span of short simulations, such as we are using here).

You are not required to implement a neighbor list, but may do so if you wish.

## Task 2

In at least a couple of paragraphs, explain your parallelization strategy.
This explanation should include a clear description of how you distribute data across ranks and how you distribute the work of the calculation.
It should identify the key choices you made when selecting this parallelization strategy and any associated performance trade-offs.
Add your answer to the section provided below.

## Answer
