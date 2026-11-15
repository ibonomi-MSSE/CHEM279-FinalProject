### CHEM279-FinalProject
## Optimization methods for SCF Convergence and Molecular Geometry Using Direct Inversion in the Iterative Subspace (DIIS) and Broyden-Fletcher-Goldfarb-Shanno (BFGS)

#### Collaborators: Isabella Bonomi, Cris Zong, Robert Wallace

Our project aims to improve computational efficiency and accuracy of our existing Hartree-Fock and CNDO/2 approximation framework by implementing two additional optimization methods: DIIS and BFGS. First, we will implement the DIIS method to accelerate self consistent field convergence (SCF) by extrapolating previous Fock matrices using a weighted combination of their error matrices to minimize the magnitude of error using Lagrange multipliers. Next, we will implement the quasi-Newton BFGS algorithm to improve the approximation of molecular geometry using energy gradients and the inverse Hessian matrix. We will evaluate both methods across a diverse set of molecules, comparing efficiency, convergence rates, optimized geometries, and energy against our existing implementation (from HW5) and experimental values. 
