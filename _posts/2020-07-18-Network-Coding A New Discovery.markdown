---
layout: post
title:  "Network Coding A New Discovery"
date:   2020-07-18
categories: jekyll update
---


The motivation of network coding theory is best illustrated by the following diagram. For all $(i,j)\in\{1,2\}^2$, $s_i$ needs to send message $b_i$ to $t_j$ via the directed communication graph. 

In a usual paradigm, nodes in network are not supposed to do nothing but copy the received data. In this case, to fulfill all the communication tasks, the communication between Node $1$ and Node $2$ needs to send $b1$ and $b2$ separately.

In the paradigm of network coding, between Node $1$ and Node $2$ we can communicate the message $b1\bigoplus b2$ ($\bigoplus$ meaning the bit-wise XOR operation between two bit-strings), which can then be deciphered by $t1$ and $t2$ separately to retrieve the information they need. 



![Screenshot 2020-07-18 at 04.00.30](/Users/Datoclement1/Documents/Datoclement_github_io/Datoclement.github.io/_posts/_resources/Butterfly-Network.png)



Further Readings:

* *Network Coding: An Introduction* by Tracy Ho and Desmond S. Lun