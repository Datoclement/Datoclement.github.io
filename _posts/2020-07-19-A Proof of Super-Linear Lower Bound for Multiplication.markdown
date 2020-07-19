---
layout: post
title:  "A Proof of Super-Linear Lower Bound for Multiplication"
date:   2020-07-19
categories: jekyll update
---

Super-linear lower bounds are hard to prove. Even for the simplest operation such as multiplication, the best established lower bound time complexity is linear, a self-evident result regarding the input sized linearly. However, last year a breakthrough has been made by the paper *[Lower bounds for multiplication via network coding](https://arxiv.org/abs/1902.10935)*, which based on the assumption of  a conjecture (NCC) from network coding community proves that the boolean-circuit size-complexity of multiplication is at least $\Omega(n\log n)$. What's more remarkable in their result is that they proved bit-shift operation is actually $\Omega(n\log n)$. As shift operation can be reduced to multiplication, the result comes naturally.



Caveat is that this is a result on the *boolean-circuit size complexity* rather than the usual *time complexity*. It has been proven that it is possible for an operation of complexity $\mathcal{O}(n)$ to need a circuit size $\Omega(n\log n)$ to compute, see paper [On Relating TIme and Space to Size and Depth](https://pdfs.semanticscholar.org/4b5a/9490e85b90925a28079e541029bdc3561bf2.pdf). But still, this is surprising enough for the lack of important advancement in this field.



Here we will briefly introduce the proof and the conjecture.

#### The Conjecture 

Network coding can't improve information transmission on undirected graphs. (Best network coding rate is equal to the maximal flow on the undirected graph.)



#### Japanese Theorem

A flow vector is feasible if and only if the vector dot-multiplied by the vector of the shortest distances for each commodity is maximized by the total capacity. $C\geq \vec{f}.\vec{d}$



#### The Proof

Consider the shift operation that receives a bit-string $a$ sized $n$ and an index $j$ sized $\log n$. The output of the operation is defined as a bit-string $s$ of length $2n$ such that `s=a<<j` to put it in a programming language, that is, $s_i=a_{i-j}$ for all $j\leq i< j+n$ and $s_i=0$ otherwise.

Consider a boolean-circuit $C$ with gate input size constantly bounded that compute the shift operation.

On the undirected graph $G$ underlined by this boolean circuit $C$, due to the gate input size being bounded, each input node has at most $n^\epsilon$ nodes whose distance to it is of the order $\epsilon\log n$. Among $n^2$ pairs (input node, target output node of $j$ shift), only $n\times n^\epsilon$ pairs have distance less than $\epsilon\log n$. Thus there exists $j_0$ for which order of $n$ input nodes distance itself with $j_0$ target node for at least $\log n$.

For this fixed $j_0$, the boolean-circuit becomes a coding network ($n$ inputs being the sources and the $j_0$ target node being the sinks), which means coding does not improves the information transmission rate on $G$, meaning we can see the network as non-coding network, and its maximal flow vector will not change. As we know that in coding network the maximal flow vector is at least the one vector, so is in a routing setting.

The total capacity is the number of edges in the circuit, proportional to the number of nodes $N$, that is, the size complexity (because of the bounded sized input gate). The maximal routing flow vector is the one vector and is realized by achieving maximal flow for each commodity. According to the Japanese Theorem, 

$$N\geq \vec{1}.\vec{d}=\Omega(n\log n)$$, which finalizes the proof.







Further Readings:

* *[Lower bounds for multiplication via network coding](https://arxiv.org/abs/1902.10935)* by Peyman Afshani, Casper Benhamin Freksen, Lior Kamma, Kasper Greem Larsen