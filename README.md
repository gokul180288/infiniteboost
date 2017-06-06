<img src='https://github.com/arogozhnikov/infiniteboost/blob/master/infiniteboost.png' width=200 align=right />

# InfiniteBoost

Code for a paper  <br />
InfiniteBoost: building infinite ensembles with gradient descent ([arxiv:1706.01109](https://arxiv.org/abs/1706.01109)). <br />
[A. Rogozhnikov](https://github.com/arogozhnikov), [T. Likhomanenko](github.com/tlikhomanenko)

## Description

**InfiniteBoost** is an approach to building ensembles which combines best sides of random forest and gradient boosting. 

Trees in the ensemble encounter mistakes done by previous trees (as in gradient boosting), 
but due to modified scheme of encountering contributions
the ensemble converges to the limit, thus avoiding overfitting (just as random forest).

<img src='https://github.com/arogozhnikov/infiniteboost/blob/master/research/plots/rocauc_higgs.png' width=400 /><img src='https://github.com/arogozhnikov/infiniteboost/blob/master/research/plots/forest_longrun_real-sim.png' width=400 />

More plots of comparison in research notebooks and in research/plots directory.

## Reproducing research

Research is performed in jupyter notebooks 
(if you're not familiar, read [why Jupyter notebooks are awesome](http://arogozhnikov.github.io/2016/09/10/jupyter-features.html)).

You can use docker image `arogozhnikov/pmle:0.01` from docker hub. 
Dockerfile is stored in this repository (ubuntu 16 + basic [sklearn](https://github.com/scikit-learn/scikit-learn) stuff).

To run the environment (sudo is needed on linux):
```bash
sudo docker run -it --rm -v /YourMountedDirectory:/notebooks -p 8890:8890 arogozhnikov/pmle:0.01
```
(and open `localhost:8890` in the browser).


## InfiniteBoost package

Self-written minimalistic implementation of trees as used for experiments against boosting.

Specific implementation was used to compare with random forest and based on the trees from scikit-learn package. 

Code written in python 2, some critical functions in fortran, so you need `gfortran + openmp` installed 
before installing the package (or simply use docker image).

```bash
pip install numpy
pip install .
nosetests tests
```

You can use implementation of trees from the package for your experiments, in this case please cite InfiniteBost paper.

## Planned

Implementation of InfiniteBoost for other boosting packages (help is welcome).
