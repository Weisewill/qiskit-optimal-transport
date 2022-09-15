# Solve Optimal Transport problem with Qiskit
  
## Introduction to Optimal Transport 

In the 18th centry the Franch mathematician Gaspard Monge formulated the problem of minimizing a worker's overall effort of moving sands in a construction site to a predescribed shape using the Optimal Transport (OT) theory. Since then, OT has been studied in different eras of history and a lot of applicaitons in logistics and economics have been developed by mathematicians such as Tolstoi, Kantorovich, Hitchcock, and Koopmans. Solving a OT problem remained a difficult problem. In 1949 Danzig re-formulated OT into an linear programming form and solved it numerically by optimization method. Recently, approximation algorithms, such as entropy-regularized OT, made solving largse-scale OT problems much cheaper in computation. Researchers have applied OT to several machine learning problems such as OT-GAN. 

Quantum computing is a promising method to solve a large-scale OT problem exactly due to its powerful capability of solving combinatorial optimization problems. In the notebook, I cast the discrete integer OT problem to linear programming, transform it to Quadratic Unconstrained Binary Optimization (QUBO) form within Qiskit's framework, and finally solve it by Qiskit's Quantum Approximate Optimization Algorithm (QAOA).

## Mathematical formulation of Optimal Transport

Following the Monge-Kontorovitch formulation, the objective of the discrete optimal transport problem is to find a transpotation plan, $T$, which minimizes the overall cost $L_{C}$:

$$ L_C(\mu,\nu) = \min_{T \in U(\mu,\nu)} \left< C, T \right>, $$  

given the row and column marginals $\mu$ and $\nu$ which have dimension of $m$ and $n$, respectively, and a size $m \times n$ cost function $C$. $\left< \cdot, \cdot \right>$ is the Euclidan dot-product between vectors and $U(\mu,\nu)$ is a set of discrete coupling measures.

To solve it, we first convert the original problem into a linear program. Define a matrix $A$ for linear constraints:

$$ A = \left[
\begin{matrix}
\mathbb{1}_n^T \otimes \mathbb{I}_m \\
\mathbb{I}_n  \otimes \mathbb{1}_m^T \\
\end{matrix} \right]^{(m+n)\times mn},
$$

where $\mathbb{I}_n$ is for the size $n \times n$ identity matrix and $\otimes$ stands for the Kroneker's product. With the help of the $A$ matrix, we can rewrite the original OT problem in linear program:

$$
\begin{array}{ll}
\text{minimize}  & c^T t \\
\text{subject to}& At = \left[
  \begin{matrix}
  \mu \\
  \nu
  \end{matrix} \right]
\end{array}
$$

where $c$ and $t$ are mn-dimensional vectors whose elements are stacked columns contained in $C$ and $T$. The above linear program can then be casted into QUBO form and solved by Qiskit's QAOA method.

References:   
[1] C. Villani, "Optimal Transport, old and new" (2008).  
[2] G. Peyre and M. Cuturi, "Computational Optimal Transport" (2020).  
[3] https://qiskit.org/documentation/optimization/tutorials/06_examples_max_cut_and_tsp.html  

