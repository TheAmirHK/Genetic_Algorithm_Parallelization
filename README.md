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
 ## How GA works and how to paralleize it ?
The foundation and understanding of a genetic algorithm are not that complicated. At its core, it’s just a trial-and-error search process inspired by evolution.
It is a population-based search method that evolves solutions over multiple generations using mechanisms inspired by biological evolution:
1. Initialization: A population of candidate solutions (chromosomes) is randomly generated.
2. Selection: The best individuals (based on a fitness function) are chosen to pass their traits to the next generation.
3. Crossover (Recombination): Selected individuals swap parts of their genetic code (analogous to reproduction).
4. Mutation: Small random changes are introduced to maintain diversity and prevent premature convergence.
5. Evaluation: The fitness of new individuals is assessed.
6. Repeat: This cycle continues until an optimal or satisfactory solution is found.
   
<p align="center">
<img width="33%" src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/blob/main/GA.jpg">
<img width="33%" src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/blob/main/PGA.jpg">
</p>

<img src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/raw/main/GA_result.png" alt="Alt Text" width="400" height="auto"><img src="https://github.com/TheAmirHK/Genetic_Algorithm_Parallelization/raw/main/PGA_result.png" alt="Alt Text" width="400" height="auto">

# NSGA-II: Non-dominated Sorting Genetic Algorithm II
NSGA-II extends the concept of genetic algorithms (GAs) to handle multiple conflicting objectives effectively. Instead of a single optimal solution, NSGA-II finds a Pareto front—a set of solutions where no solution is strictly better than another across all objectives.
The Evolution of NSGA-II is also intresting to know and the idea of multi-objective optimization dates back to the early 20th century, but the modern form took shape through genetic algorithms:

- 1950s: **Richard Bellman** introduced the concept of dynamic programming, which later influenced multi-objective decision-making.
- 1960s: **Vilfredo Pareto**’s work on efficiency in economics became a foundation for Pareto optimality in optimization.
- 1980s: **David Goldberg** and **John Holland** explored genetic algorithms for constrained optimization, laying the groundwork for evolutionary multi-objective optimization.
- 1995: **Srinivas** and **Deb** introduced NSGA (Non-dominated Sorting Genetic Algorithm), an early version that used non-dominated sorting but had high computational complexity.
- 2002: **Kalyanmoy Deb** and colleagues developed NSGA-II, introducing fast non-dominated sorting, crowding distance, and elitism, making it more efficient and widely adopted.
- 2000s-Present: NSGA-II became a standard in solving engineering, logistics, finance, and AI problems, inspiring other algorithms like NSGA-III for many-objective problems.

## How NSGA-II works ?

NSGA-II refines the standard genetic algorithm to maintain diversity and find well-distributed Pareto-optimal solutions. It follows these key steps:

1. Initialization: A population of candidate solutions (chromosomes) is generated randomly.
2. Non-dominated Sorting: Solutions are ranked into different Pareto fronts based on dominance (solutions that are not worse in any objective).
3. Crowding Distance: A density metric is calculated to ensure diverse solutions are selected.
4. Selection: Using a tournament selection method that prefers lower-rank (better) solutions and diverse individuals.
5. Crossover & Mutation: Solutions exchange genetic information and undergo small mutations to explore the search space.
6. Elitism & Replacement: The best solutions from parents and offspring survive to the next generation.
7. Repeat Until Convergence: The process continues until a stopping criterion (e.g., max generations) is met.
