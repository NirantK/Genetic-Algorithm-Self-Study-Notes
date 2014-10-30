Notes on Genetic Algorithms
=======================
## Contents
- [Introduction](#introduction)
- [Biological Background](#biological-background)
- [How it Works]
	-[PseudoCode]
- Motivation / Advantages
- [Applications](#applications)
- Key Terms and Jargon
	- Crossing Over
	- Mutation
	- Fitness Criteria
	- Termination Evaluation Criteria
- Comparitive Study
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
2. Evaluation - Each member of the population is then evaluated and we calculate a 'fitness' for that individual. The fitness value is calculated by how well it fits with our desired requirements. These requirements could be simple, 'faster algorithms are better', or more complex, 'faster algorithms should have high accuracy and easy to implement'
3. Selection - We want to be constantly improving our populations overall fitness. Selection helps us to do this by discarding the bad designs and only keeping the best individuals in the population.  There are a few different selection methods but the basic idea is the same, make it more likely that fitter individuals will be selected for our next generation.
4. Crossover - During crossover we create new individuals by combining aspects of our selected individuals. We can think of this as mimicking how sex works in nature. The hope is that by combining certain traits from two or more individuals we will create an even 'fitter' offspring which will inherit the best traits from each of it's parents.
5. Mutation - We need to add a little bit randomness into our populations' genetics otherwise every combination of solutions we can create would be in our initial population. Mutation typically works by making very small changes at random to an individuals genome.
6. ** And repeat! ** - Now we have our next generation we can start again from step two until we reach a termination condition.

_Termination Condition_
The termination condition decides when the algorithms stop running. The most likely reason is that your algorithm has found a solution which is good enough and meets a predefined minimum criteria. Other reasons for terminating could be constraints such as computational time.

### PSEUDOCODE
Algorithm GA is

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
end GA.

## Motivation / Advantages

## Applications

## Bibliography

1. [Introduction to Genetic Alogrithms, Obitko](http://www.obitko.com/tutorials/genetic-algorithms/ga-basic-description.php)
2. [Tutorial on Genetic Algorithms, ibug, UK](http://ibug.doc.ic.ac.uk/media/uploads/documents/courses/GeneticAlgorithm-tutorial.pdf)
3. [Creating a genetic algorithm for beginners, TheProjectSpot](http://www.theprojectspot.com/tutorial-post/creating-a-genetic-algorithm-for-beginners/3)
4. [What's a Genetic Algorithm (GA)?, CMU](http://www.cs.cmu.edu/Groups/AI/html/faqs/ai/genetic/part2/faq-doc-2.html)
5. [](http://www.doc.ic.ac.uk/~nd/surprise_96/journal/vol1/tcw2/article1.html)
6. [Index of Most Important Applications of the Genetic Algorithms, Nov 97](http://neo.lcc.uma.es/TutorialEA/semEC/cap03/cap_3.html)
7. []()