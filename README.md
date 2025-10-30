# SLAPRP.jl

Branch-Cut-and-Price algorithm for solving the Storage Location Assignment and Picker Routing Problem.

## Description

This repository implements the code from the paper "The Storage Location Assignment and Picker Routing Problem: A Generic Branch-Cut-and-Price Algorithm" authored by T. Prunet, N. Absi and D. Cattaruzza, and published in the *European Journal of Operational Research*. 

## Requirements

Running with package requires `Julia >= 1.6`. The Linear programs are solved using the commercial solver `ILOG CPLEX 20.1`. Please refer to [https://github.com/jump-dev/CPLEX.jl](https://github.com/jump-dev/CPLEX.jl) to get a licence and interface CPLEX with Julia.

## Reproducing our results

To reproduce our result, you should first clone the repository. Open a Julia REPL at its root, and run the following commands:

```julia
using Pkg
Pkg.activate(".")
Pkg.instantiate()
include("test/main.jl")
```

Then you can run the experiments with the command 
```julia
run(dataset, policy)
```
where dataset is the name of the dataset and policy is the routing policy. The field data set can take the values "silva" and "guo".
The field policy can take the values "exact", "return", "sshape", "midpoint", "largest". The detailed description of the datasets and routing policies is 
provided in the related publication. Note that "return" is the only policy available for the guo dataset.

For instance, run the following command to reproduce the results for the silva dataset with the return routing policy. This will create a csv file with the detailed results.

```julia
run("silva","return")
```

Beware that this command will run the algorithm on the whole testbed, which may be time consuming.

## Reference

```
@article{prunet2025storagelocationassignmentpicker,
title = {The storage location assignment and picker routing problem: A generic branch-cut-and-price algorithm},
journal = {European Journal of Operational Research},
volume = {327},
number = {3},
pages = {857-874},
year = {2025},
issn = {0377-2217},
doi = {https://doi.org/10.1016/j.ejor.2025.05.041},
url = {https://www.sciencedirect.com/science/article/pii/S0377221725004394},
author = {Thibault Prunet and Nabil Absi and Diego Cattaruzza}
}
```
