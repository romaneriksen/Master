# Progress for master thesis

## Week 41
- Installed Revolve2 - a framework for simulating modular robots.
- Get to know how Revolve2 works by playing with examples.
- Reading the code to understand how to set up my own simulations.

## Week 42
- Set up a workspace environment on a remote computer for faster simulations.
- Run some of the demanding example simulations to understand what Revolve2 produces.

## Week 43
- Combine two different revolve example programs into one single program that combines evolution and learning
- Use multiNEAT to perform neuroevolution searching for good genomes representing a modular robot. here, MultiNEAT implements CPPNs (Compositional Pattern Producing Network) as generative encodings and evolves them using genetic algorithms.
- The robots represented by the CPPNs are then sent as input a learner method that creates a brain from the robot's structure. The brains consist of multiple CPGs with connections between each other. The number of connections and CPGs are decided based on how many active hinge modules exist in the robot, and if the active hinge has any nearby neighbor modules that also are active hinges.
- The learner method is a CMA-ES (Covariance Matrix Adaptation Evolution Strategy) that attempts to maximize the robot's displacement by searching for the best brain  (controller) parameters by iteratively evolving the different solutions.

## Week 44
- Experiment with different population sizes and learning time for the robots.

## Week 45
- Experiment with the boundary values in the CMA-ES, increasing them for more exploration (more "extreme" controller values).

## Week 46
- Change the objective fitness function from xy-displacement to either x- or y-displacement

## Week 47
- Adapt the Mujoco configuration files to track the robot by double-clicking on one of its components before starting the rerun simulation displaying how the robot performed. 

## Week 48

## Week 49
- Implement inheritance of brain parameters. Offspring can now inherit values for their controller from their parents. If a CPG exists in the same grid position for both parent and offspring, the offspring can inherit the values. 


