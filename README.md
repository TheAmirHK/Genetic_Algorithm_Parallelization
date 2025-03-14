# Genteic Algorithm

Genetic algorithms (I confess that this algorithm is one of my favorite ones) are inspired by Darwinian evolution, which explains how species adapt and improve over time through natural selection. This process allows organisms with advantageous traits to survive and reproduce, passing on their genes to the next generation.
They are particularly interesting because they offer a way to solve complex problems by mimicking the process of natural selection. This algorithm has a facinating history rather than just an optimization algorithm. 
- **Charles Darwin**’s "*On the Origin of Species*" (1859) introduced the idea of natural selection—organisms with beneficial traits survive and pass their genes to the next generation.
Though Darwin didn’t use mathematical models, his ideas laid the foundation for optimization through selection.
- In 1930s, **Ronald Fisher**  applied probability theory to evolution, showing how traits evolve mathematically. His work in population genetics inspired the fitness function in GAs.
- In 1950s, **Alan Turing** in his paper "*Computing Machinery and Intelligence*", Turing speculated about machines that evolve like living organisms. He suggested that a computer could improve itself through mutation and selection, an idea similar to GAs.
- In 1970s, **John Holland** at the University of Michigan introduced the first formal genetic algorithm in his book "*Adaptation in Natural and Artificial Systems*".
He developed a mathematical framework to apply natural selection to optimization problems. Following that year, **Kenneth De Jong**, Hollands student tested GA performance on real-world problems.
- In 1990s, **David Goldberg**, again another student of Holland, used GAs for optimizing pipeline networks. Afterward, he published "Genetic Algorithms in Search, Optimization & Machine Learning" (1989), popularizing GAs in engineering and AI.
- From 2000s till today GA used in robotics, game AI, logistics, finance, Neuroevolution, Quantum GAs and yet no stop to that.
 ### How GA works and how to parallelize it ?
The foundation and understanding of a genetic algorithm are not that complicated. At its core, it’s just a trial-and-error search process inspired by evolution.
It is a population-based search method that evolves solutions over multiple generations using mechanisms inspired by biological evolution:
1. Initialization: A population of candidate solutions (chromosomes) is randomly generated.
2. Selection: The best individuals (based on a fitness function) are chosen to pass their traits to the next generation.
3. Crossover (Recombination): Selected individuals swap parts of their genetic code (analogous to reproduction).
4. Mutation: Small random changes are introduced to maintain diversity and prevent premature convergence.
5. Evaluation: The fitness of new individuals is assessed.
6. Repeat: This cycle continues until an optimal or satisfactory solution is found.

***Parallelization method***: A most-common method in parllelization is called the "Island Model", also known as the Distributed Genetic Algorithm. This method was introduced by Martin, W. N. (1997) and it enhances genetic algorithms (GAs) by dividing the population into multiple subpopulations, referred to as "islands." Each island evolves independently, applying selection, crossover, and mutation operators within its local population. Periodically, a migration process occurs where selected individuals are exchanged between islands, promoting genetic diversity and aiding in the exploration of the solution space. Aside from this method, several others can also be found that have their own ups and downs, methods such as Master-Slave Model or Fine-Grained Model and also another method so-called SIMD (Single Instruction, Multiple Data) approach. knwoing them is just fun !

<p align="center">
<img width="33%" src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/blob/main/GA.jpg">
<img width="33%" src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/blob/main/PGA.jpg">
</p>

<p align="center">
<img src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/raw/main/GA_result.png" alt="GA" width="400" height="auto">
<img src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/raw/main/PGA_result.png" alt="PGA" width="400" height="auto">
</p>

Martin, W. N. (1997). Island (migration) models: evolutionary algorithms based on punctuated equilibria. Handbook of evolutionary computation.

# NSGA-II: Non-dominated Sorting Genetic Algorithm II
NSGA-II extends the concept of genetic algorithms (GAs) to handle multiple conflicting objectives effectively. Instead of a single optimal solution, NSGA-II finds a Pareto front—a set of solutions where no solution is strictly better than another across all objectives.
The Evolution of NSGA-II is also intresting to know and the idea of multi-objective optimization dates back to the early 20th century, but the modern form took shape through genetic algorithms:

- 1950s: **Richard Bellman** introduced the concept of dynamic programming, which later influenced multi-objective decision-making.
- 1960s: **Vilfredo Pareto**’s work on efficiency in economics became a foundation for Pareto optimality in optimization.
- 1980s: **David Goldberg** and **John Holland** explored genetic algorithms for constrained optimization, laying the groundwork for evolutionary multi-objective optimization.
- 1995: **Srinivas** and **Deb** introduced NSGA (Non-dominated Sorting Genetic Algorithm), an early version that used non-dominated sorting but had high computational complexity.
- 2002: **Kalyanmoy Deb** and colleagues developed NSGA-II, introducing fast non-dominated sorting, crowding distance, and elitism, making it more efficient and widely adopted.
- 2000s-Present: NSGA-II became a standard in solving engineering, logistics, finance, and AI problems, inspiring other algorithms like NSGA-III for many-objective problems.

### How NSGA-II works ?

NSGA-II refines the standard genetic algorithm to maintain diversity and find well-distributed Pareto-optimal solutions. It follows these key steps:

1. Initialization: A population of candidate solutions (chromosomes) is generated randomly.
2. Non-dominated Sorting: Solutions are ranked into different Pareto fronts based on dominance (solutions that are not worse in any objective).
3. Crowding Distance: A density metric is calculated to ensure diverse solutions are selected.
4. Selection: Using a tournament selection method that prefers lower-rank (better) solutions and diverse individuals.
5. Crossover & Mutation: Solutions exchange genetic information and undergo small mutations to explore the search space.
6. Elitism & Replacement: The best solutions from parents and offspring survive to the next generation.
7. Repeat Until Convergence: The process continues until a stopping criterion (e.g., max generations) is met.
<p align="center">
<img width="33%" src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/blob/main/NSGA2.jpg">
</p>

# NSGA-III: Non-dominated Sorting Genetic Algorithm III
NSGA-III is an extension of the NSGA-II algorithm designed specifically for solving many-objective optimization problems. It was introduced by Deb and Jain in 2013 to improve the performance of evolutionary multi-objective optimization algorithms in handling high-dimensional objective spaces.

### How NSGA-III works ?
 
1. Initialization: Generate a random population and define reference points in the objective space.
2. Non-Dominated Sorting: Rank solutions into Pareto fronts.<br>
3. Selection (different from NSGA-II!):<br>- If a front fits in the population, then Add all solutions.<br>- If not, then use Reference-Point Niching to select solutions closest to underrepresented reference points.<br>
4. Crossover & Mutation: Apply Simulated Binary Crossover (SBX) and Polynomial Mutation.
5. Repeat Until Convergence.



# Key differences between GA, NSGA-II, and NSGA-III 
| Feature                   | Genetic Algorithm (GA)                                  | NSGA-II                                        | NSGA-III                                      |
|---------------------------|-------------------------------------------------------|------------------------------------------------|----------------------------------------------|
| **Type**                     |  Single Evolutionary Algorithm                        | Multi-Objective Evolutionary Algorithm | Multi-Objective Evolutionary Algorithm  |
| **Objective Handling**       | Typically single-objective                           | Handles multiple objectives effectively       | Designed for many-objective optimization |
| **Selection Mechanism**      | Roulette wheel, tournament, or rank-based selection  | Non-dominated sorting + crowding distance     | Non-dominated sorting + reference points    |
| **Diversity Preservation**   | Mutation and crossover help maintain diversity        | Crowding distance ensures diversity           | Reference points ensure even distribution   |
| **Computational Complexity** | O(M ⋅ N ⋅ log N) (M: objectives, N: population size) | O(M ⋅ N²) (improved from NSGA)               | O(M ⋅ N²) (similar to NSGA-II but different sorting approach) |
| **Scalability to Many Objectives** | Poor without modifications                   | Works well for up to 3 objectives            | Scales well for 4+ objectives               |
| **Sorting Mechanism**        | Not inherently based on Pareto ranking               | Fast non-dominated sorting                    | Reference point-based non-dominated sorting |
| **Strengths**             | Simple, general-purpose, easy to implement            | Efficient for a small number of objectives    | Handles many-objective problems better      |
| **Weaknesses**            | Struggles with multi-objective trade-offs             | Struggles with more than 3 objectives        | Requires predefined reference points        |



