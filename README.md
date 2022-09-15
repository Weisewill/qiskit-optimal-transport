# Optimal Transport problem 
  
## Introduction

In the 18th centry the Franch mathematician Gaspard Monge formulated the problem of minimizing a worker's overall effort of moving sands in a construction site to a predescribed shape using the Optimal Transport (OT) theory. Since then, OT has been studied in different eras of history and a lot of applicaitons in logistics and economics have been developed by mathematicians such as Tolstoi, Kantorovich, Hitchcock, and Koopmans. Solving a OT problem remained a difficult problem. In 1949 Danzig re-formulated OT into an linear programming form and solved it numerically by optimization method. Recently, approximation algorithms, such as entropy-regularized OT, made solving largse-scale OT problems much cheaper in computation. Researchers have applied OT to several machine learning problems such as OT-GAN. 

Quantum computing is a promising method to solve a large-scale OT problem exactly due to its powerful capability of solving combinatorial optimization problems. In the notebook, I cast the integer OT problem to linear programming, transform it to Quadratic Unconstrained Binary Optimization (QUBO)form within Qiskit's framework, and finally solve it by Qiskit's Quantum Approximate Optimization Algorithm (QAOA).

## Mathematical formulation

Following the Monge-Kontorovitch formulation, the objective of the optimal transport problem is to find a transpotation plan which minimizes the overall cost:


References:   
[1] C. Villani, "Optimal Transport, old and new" (2008).  
[2] G. Peyre and M. Cuturi, "Computational Optimal Transport" (2020).  
[3] https://qiskit.org/documentation/optimization/tutorials/06_examples_max_cut_and_tsp.html  

