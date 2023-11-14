---
layout: post
title: Gossip Averaging
tags: Decentralized_Learning
---

Gossip averaging is an important component in consensus-based decentralized learning algorithms. [Gossip-Based Computation](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=1238221) can be used to compute random samples, quantiles, or any other aggregate-based queries in a decentralized manner. In this post, we will look into the gossip-averaging algorithm which aims to compute the average of the given decentralized system with fixed graph topology in linear time. In the decentralized setup, every node only communicates with its neighbors and the time (hops) required to pass the information from node $i$ to %j$ is equal to the shorted path length from $i$ to %j$.

Note that there are many ways to implement distributed averaging. One straightforward method is [flooding](https://www.sciencedirect.com/science/article/pii/S0167691104000398). In this method, each node maintains a table of the initial values of all the nodes, initialized with its own node value. At each iteration, the nodes exchange the non-trivial information from their own tables with their neighbors. After a number of iterations equal to the diameter of the network, every node knows all the initial values of all the nodes, so the average can be computed. However, the flooding algorithm has a memory overhead proportional to the number of nodes in the system. Gossip averaging gets rid of this memory overhead.

**Notations:**
1. *Goal:* Compute the average of initial values in an $n$-node decentralized system.
2. *Connectivity:* Sparse graph topology G(N,E). N = set of nodes = { $1,...,n$ }. E = set of edges.
3. *Adjacency/Mixing Matrix (W):* $w_{ij} \neq 0$ for { $i,j$ } $\in E$ and $0 \leq w_{ij} \leq 1$.
4. *Neighbors of node-$i$:* $N_i$ represents all $j$'s such that $w_{ij} \neq 0$.
5. *Initial values:* $x_i^{(0)}$   $\forall i \in [1,...,n]$

![Gossip Averaging]({{ '/assets/gossip_avg.png' | relative_url }}) 
<div align="center">
<strong>Figure 1: Illustrating a single iteration of gossip averaging using a 4-node ring topology.</strong>
</div>
<br>


At every iteration of gossip averaging, there are three steps (refer to Figure 1):
1. *Information Split:* Each node first splits the information based on corresponding column weights of W.
2. *Communication:* Communicates the split information to respective neighbors.
3. *Aggregation:* Each node updates its value by adding the received information.

In summary, the matrix representation of one iteration of gossip averaging is given by $X_t = W X_{t-1}$. Unrolling the recursion: $X_t = W^t X_0$.

where $X_t^T = [x_1^t, x_2^t,...,x_n^t]$ and $x_i^t$ is the data/value on $i^{th}$ node at iteration $t$. 

**Convergence:**

The gossip averaging algorithm converges in linear time with respect to the number of nodes i.e., $\mathcal{O}(n)$. The following are the constraints required for the linear convergence of the gossip averaging algorithm.

1. *Strongly Connected Graph:* There is a path from each node to every other node.
2. *Self Loops:* Each node is connected to itself.
3. *Doubly Stochastic Mixing Matrix:* This implies two conditions
    *  *Column stochasticity:* Each column sums to one. This ensures that the average of the system is preserved at each iteration.
    *  *Row stochasticity:* Each row sums to one. This ensures that the addition of received information results in a valid weighted averaging.
4. *Symmetric weight matrix:* This property helps in the convergence analysis and makes the practical realization of doubly stochastic mixing possible.


  
