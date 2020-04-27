# Optimization of a Terzaghi vertical consolidation model

This repository contains a numerical implementation of the Terzaghi model to simulate vertical consolidation. The numerical implementation allows for multiple load steps, loading and unloading and is linked to a <img src="https://render.githubusercontent.com/render/math?math=$C_c$">, <img src="https://render.githubusercontent.com/render/math?math=$C_r$"> compressibility model. It is set-up with an explicit and implicit (backward) finite difference method, solving the Terzaghi partial differential equation given by:

<img src="https://render.githubusercontent.com/render/math?math=\frac{\partial u}{\partial t}=C_v\frac{\partial^2 u}{\partial z^2}+\frac{\partial\sigma}{\partial t}">

The goal is to automatically fit the model to data by use of numerical optimization. An example of this automatic parameter fitting is given with a number of algorithms. It is possible to test out different algorithms and compare the results right away. All iterations are saved for further evaluation. 

This repository is associated with a paper presented at the 16th International Conference of IACMAG. A preprint of the paper is available at researchgate. 

[comment]: <> (Installation; if I compile the package as an installable module)

## Custom multi-start algorithm
Optimization trials for these kind of physics-based consolidation models indicate that the problem suffers significantly from local optima, especially if no manual prefitting is done to limit the parameter space. Efficient local optimization algorithms therefore lead to suboptimal solutions, but global optimization schemes, which do converge, require a prohibitive amount of iterations. The shape of the loss convection lends itself to a more optimal global optimization by using random multistart optimization with local searches. Once a threshold (three is found to be sufficient) local optima are found which are the lowest in the overall space and converge to (approximately) the same position, the algoritm asssumes to have found the global optimum. Benchmarks show favourable results with theoretical solutions optimizing 6 parameters with a physicial meaning. 

[comment]: <> (Add figure)
