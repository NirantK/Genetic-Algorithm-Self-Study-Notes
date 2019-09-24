Genetic Algorithms
=======================
##### Self Study Notes 
Made while learning to Classify Satellite Images on basis of land use pattern
###### Compiled by [Nirant Kasliwal](nirantk.com)


## Contents
- [Introduction](#introduction)
- [Biological Background](#biological-background)
- [How it Works](#how-it-works)
	- [PseudoCode](#pseudocode)
- [Motivation / Advantages](#why-ga)
- [Applications](#applications)
- [Concepts](#concepts)
	- [Crossing Over](#crossing-over)
	  - [Methods of selection of Chromosomes](#methods-of-selection-of-chromosomes)
	- [Mutation](#mutation)
	- [Fitness Function](#fitness-function)
	- [Selection](#selection)
		- [Roulette-Wheel Selection](#roulette-wheel-selection)
		- [Stochastic Universal Sampling](#stochastic-universal-sampling)
	- Termination Evaluation Criteria
- [Bibliography](#bibliography)


## Introduction

A genetic algorithm (GA) is great for finding solutions to complex search problems. 
They're often used in engineering to create incredibly high quality products thanks to their ability to search a through a huge combination of parameters to find the best match. 

For example, they can search through different combinations of materials and designs to find the perfect combination of both which could result in a stronger, lighter and overall, better final product. They can also be used to design computer algorithms, to schedule tasks, and to solve other optimization problems. 

Genetic algorithms are based on the process of evolution by natural selection which has been observed in nature. They essentially replicate the way in which life uses evolution to find solutions to real world problems. Surprisingly although genetic algorithms can be used to find solutions to incredibly complicated problems, it is claimed that they are themselves pretty simple to use and understand.

In a broader usage of the term a genetic algorithm is any population based model that uses selection and recombination operators to generate new sample points in a search space. 
Many genetic algorithm models have been introduced by researchers largely working from an experimental perspective.

Many of these researchers are application oriented and are typically interested in genetic algorithms as optimization tools. 

## Biological Background
In each cell of a living organism there is a set of chromosomes. These chromosomes are unique for each individual organism irrespective of species or any other classification. The chromosomes are same for every cell in a single organism. 

Chromosomes are strings of [DNA](http://www.wikiwand.com/en/DNA) and serve as a model for the whole organism. A chromosome consist of genes. Genes are blocks of DNA. 
Each gene encodes a particular protein. For simplicity's sake, we assume that each gene encodes a trait, for example color of eyes. Possible settings for a trait (e.g. blue, brown) are called _alleles_. 
Each gene has its own position in the chromosome. This position is called _locus_.

Complete set of genetic material (all chromosomes) is called _genome_. Particular set of genes in genome is called _genotype_. The genotype is with later development after birth base for the organism's phenotype, its physical and mental characteristics, such as eye color, intelligence etc.

## How It Works?

![Flowchart for Basic Process](/images/genetic_flowchart_process.png "Flowchart for Basic Process")

The basic process for a genetic algorithm is:

1. Initialization - Create an initial population. This population is usually randomly generated and can be any desired size, from only a few individuals to thousands.
2. Evaluation - Each member of the population is then evaluated and we calculate a 'fitness' for that individual. The fitness value is calculated by how well it fits with our desired requirements. These requirements could be simple, 'faster algorithms are better', or more complex, 'faster algorithms should have high accuracy and easy to implement' .
3. Selection - We want to be constantly improving our populations overall fitness. Selection helps us to do this by discarding the bad designs and only keeping the best individuals in the population.  There are a few different selection methods but the basic idea is the same, make it more likely that fitter individuals will be selected for our next generation.
4. Crossover - During crossover we create new individuals by combining aspects of our selected individuals. We can think of this as mimicking how sex works in nature. The hope is that by combining certain traits from two or more individuals we will create an even 'fitter' offspring which will inherit the best traits from each of it's parents.
5. Mutation - We need to add a little bit randomness into our populations' genetics otherwise every combination of solutions we can create would be in our initial population. Mutation typically works by making very small changes at random to an individuals genome.
6.   And __repeat__! - Now we have our next generation we can start again from step two until we reach a termination condition.

_Termination Condition_
The termination condition decides when the algorithms stop running. The most likely reason is that your algorithm has found a solution which is good enough and meets a predefined minimum criteria. Other reasons for terminating could be constraints such as computational time.

### PseudoCode
```
Algorithm GA:

	// start with an initial time
	t := 0;
	
	// initialize a usually random population of individuals
	initpopulation P (t);
	
	// evaluate fitness of all initial individuals of population
	evaluate P (t);
	
	// test for termination criterion (time, fitness, etc.)
	do while not done
	   // increase the time counter
	   t := t + 1;
	
	   // select a sub-population for offspring production
	   P' := selectparents P (t);
	
	   // recombine the "genes" of selected parents
	   crossover P' (t);
	
	   // perturb the mated population stochastically
	   mutate P' (t);
	
	   // evaluate it's new fitness
	   evaluate P' (t);
	
	   // select the survivors from actual fitness
	   P := select P,P' (t);

	endwhile

end GA
```

## Why GA?
* Modular, separate from application 
* Supports multi-objective optimization 
* Good for “noisy” environments 
* Always an answer; answer gets better with time 
* Inherently parallel;
* Relatively easily distributed over multiple systems
* Easy to exploit previous or alternate solutions 
* Flexible building blocks for hybrid applications 
* Substantial history and range of use 

## Applications 

| Domain      | Applications    |       
| :------------- |:-------------|
| Control | [Fluid pipeline](http://waset.org/publications/9997300/a-review-of-genetic-algorithm-optimization-operations-and-applications-to-water-pipeline-systems)  |
| Robotics      | Trajectory Planning |

## Concepts

### Crossing Over

In genetic algorithms, crossover is a genetic operator used to vary the programming of a chromosome or chromosomes from one generation to the next. It is analogous to reproduction and biological crossover, upon which genetic algorithms are based. Cross over is a process of taking more than one parent solutions and producing a child solution from them.

#### One-point crossover
![One-point crossover](/images/two-point.png "One-point crossover")
A single crossover point on both parents' organism strings is selected. All data beyond that point in either organism string is swapped between the two parent organisms. The resulting organisms are the children:


#### Two-point crossover
![Two-point crossover](/images/two-point.png "Two-point crossover")

Two-point crossover calls for two points to be selected on the parent organism strings. Everything between the two points is swapped between the parent organisms, rendering two child organisms:


#### Cut and splice
Another crossover variant, the "cut and splice" approach, results in a change in length of the children strings. The reason for this difference is that each parent string has a separate choice of crossover point.

#### Uniform Crossover and Half Uniform Crossover
![Uniform crossover](/images/uniform.png "Uniform Crossover")

The Uniform Crossover uses a fixed mixing ratio between two parents. Unlike one- and two-point crossover, the Uniform Crossover enables the parent chromosomes to contribute the gene level rather than the segment level.

If the mixing ratio is 0.5, the offspring has approximately half of the genes from first parent and the other half from second parent, although cross over points can be randomly chosen.

The Uniform Crossover evaluates each bit in the parent strings for exchange with a probability of 0.5. Empirical evidence suggest that it is a more exploratory approach to crossover than the traditional exploitative approach that maintains longer schemata. This results in a more complete search of the design space with maintaining the exchange of good information. Unfortunately, no satisfactory theory exists to explain the discrepancies between the Uniform Crossover and the traditional approaches. 

In the uniform crossover scheme (UX) individual bits in the string are compared between two parents. The bits are swapped with a fixed probability, typically 0.5.

In the half uniform crossover scheme (HUX), exactly half of the nonmatching bits are swapped. Thus first the Hamming distance (the number of differing bits) is calculated. This number is divided by two. The resulting number is how many of the bits that do not match between the two parents will be swapped.

#### Arithmetic crossover 
![Arithmetic crossover](/images/arithmetic.png "Arithmetic crossover")

Some arithmetic operation is performed to make a new offspring. This could include boolean operation such as logical AND, OR, XOR etc. or combinations thereof. 

-------------------------------

#### Methods of Selection of Chromosomes

### Mutation

Mutation is a genetic operator used to maintain genetic diversity from one generation of a population of genetic algorithm chromosomes to the next. It is analogous to biological mutation. 
Mutation alters one or more gene values in a chromosome from its initial state. In mutation, the solution may change entirely from the previous solution. 
Hence GA can come to better solution by using mutation. Mutation occurs during evolution according to a user-definable mutation probability. This probability should be set low. If it is set too high, the search will turn into a primitive random search.

The purpose of mutation in GAs is preserving and introducing diversity. Mutation should allow the algorithm to avoid local minima by preventing the population of chromosomes from becoming too similar to each other, thus slowing or even stopping evolution.

### Fitness Function
The fitness function is the function you want to optimize. For standard optimization algorithms, this is known as the objective function.

There is considerable effort involved in designing a workable fitness function. It is the human designer who has to design the fitness function. 
If this is designed badly, the algorithm will either converge on an inappropriate solution, or will have difficulty converging at all.

Moreover, the fitness function must not only correlate closely with the designer's goal, it must also be computed quickly. Speed of execution is very important, as a typical genetic algorithm must be iterated many times in order to produce a usable result for a non-trivial problem.

### Selection
Reproduction (or selection) is an operator that makes more copies of better strings in a new population. Reproduction is usually the first operator applied on a population. Reproduction selects good strings in a population and forms a mating pool. This is one of the reason for the reproduction operation to be sometimes known as the selection operator. Thus, in reproduction operation the process of natural selection cause those individuals that encode successful structures to produce copies more frequently. To sustain the generation of a new population, the reproduction of the individuals in the current population is necessary. For better individuals, these should be from the fittest individuals of the previous population. There exist a number of reproduction operators in GA literature, but the essential idea in all of them is that the above average strings are picked from the current population and their multiple copies are inserted in the mating pool in a probabilistic manner.

#### Roulette-Wheel Selection
The commonly-used reproduction operator is the proportionate reproduction operator where a string is selected for the mating pool with a probability proportional to its fitness. Thus, the ith string in the population is selected with a probability proportional to Fi. Since the population size is usually kept fixed in a simple GA, the sum of the probability of each string being selected for the mating pools must be one. 

One way to implement this selection scheme is to imagine a roulette-wheel with it's circumference marked for each string proportionate to the string's fitness. The roulette-wheel is spun n times. each time selecting an instance of the string chosen by the roulette-wheel pointer. 
The fitness function assigns a fitness to possible solutions or chromosomes. This fitness level is used to associate a probability of selection with each individual chromosome. If f_i is the fitness of individual i in the population, its probability of being selected is p_i = \frac{f_i}{\Sigma_{j=1}^{N} f_j}, where N is the number of individuals in the population.

#### Stochastic Universal Sampling
Stochastic universal sampling (SUS) is a technique used in genetic algorithms for selecting potentially useful solutions for recombination. 

Where FPS chooses several solutions from the population by repeated random sampling, SUS uses a single random value to sample all of the solutions by choosing them at evenly spaced intervals. 

This gives weaker members of the population (according to their fitness) a chance to be chosen and thus reduces the unfair nature of fitness-proportional selection methods.

Other methods like roulette wheel can have bad performance when a member of the population has a really large fitness in comparison with other members. Using a comb-like ruler, SUS starts from a small random number, and chooses the next candidates from the rest of population remaining, not allowing the fittest members to saturate the candidate space.

The pseudocode for the algorithm would be: 
```
SUS(Population, N)
    F := total fitness of population
    N := number of offspring to keep
    P := distance between the pointers (F/N)
    Start := random number between 0 and P
    Pointers := [Start + i*P | i in [0..N-1]]
    return RWS(Population,Pointers)

RWS(Population, Points)
    Keep = []
    i := 0
    for P in Points
        while fitness sum of Population[1~i] < P
            i++
        add Population[i] to Keep
    return Keep
```
Here RWS() describes the bulk of roulette wheel selection (also known as "fitness proportionate selection") - in true fitness proportional selection the parameter Points is always a (sorted) list of random numbers from 0 to F. The algorithm above is intended to be illustrative rather than canonical.

## Bibliography

1. [What's a Genetic Algorithm (GA)?, CMU](http://www.cs.cmu.edu/Groups/AI/html/faqs/ai/genetic/part2/faq-doc-2.html)
2. [Introductory Article of Genetic Algorithm and its Applications, Imperial College, London](http://www.doc.ic.ac.uk/~nd/surprise_96/journal/vol1/tcw2/article1.html)
3. [Introduction to Genetic Alogrithms, Obitko](http://www.obitko.com/tutorials/genetic-algorithms/ga-basic-description.php)
2. [Tutorial on Genetic Algorithms, ibug, UK](http://ibug.doc.ic.ac.uk/media/uploads/documents/courses/GeneticAlgorithm-tutorial.pdf)
3. [Creating a genetic algorithm for beginners, TheProjectSpot](http://www.theprojectspot.com/tutorial-post/creating-a-genetic-algorithm-for-beginners/3)
5. [Index of Most Important Applications of the Genetic Algorithms, Univeristy of Malaga, Nov 97](http://neo.lcc.uma.es/TutorialEA/semEC/cap03/cap_3.html)
7. [Slides on Drexel Univeristy (PDF)](https://www.cs.drexel.edu/~spiros/teaching/SE320/slides/ga.pdf)
8. [Document with Applications of GA on rgu.ac.uk (PDF)](https://www4.rgu.ac.uk/files/chapter13%20-%20applications.pdf)
9. [Fitness functions in evolutionary robotics: A survey and analysis (Adaptive Fuzzy Fitness Granulation) (PDF)](http://www.nelsonrobotics.org/paper_archive_nelson/nelson-jras-2009.pdf)
10. [A Novel General Framework for Evolutionary Optimization(Adaptive Fuzzy Fitness Granulation) (PDF)](http://profsite.um.ac.ir/~davarynej/Resources/CEC'07-Draft.pdf)
11. [JGAP - Genetic Algorithms and Genetic Programming component provided as a Java framework](http://jgap.sourceforge.net/index.html)
12. [GA by Tom V. Mathew (PDF)](http://www.civil.iitb.ac.in/tvm/2701_dga/2701-ga-notes/gadoc.pdf)
13. [Wikiwand](http://www.wikiwand.com/en/)
14. Baker, James E. (1987). "Reducing Bias and Inefficiency in the Selection Algorithm". _Proceedings of the Second International Conference on Genetic Algorithms and their Application_ (Hillsdale, New Jersey: L. Erlbaum Associates): 14–21.
15 [StackOverflow Question on RWS](http://stackoverflow.com/questions/177271/roulette-selection-in-genetic-algorithms)
