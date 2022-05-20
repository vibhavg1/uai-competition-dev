---
title: "New Learned Multi-Label Classification Challenge!"
usemathjax: true
permalink: /competition-entry/new-mlc-challenge/
---

This year we are excited to include a new challenge of learning **multi-label classification**.<br/>
This challenge will have two phases: 
* an offline learning phase (for which you will use your own hardware)
* an online prediction phase (for which we will use our hardware).


## Offline Training Phase

For the offline training phase, you will be provided with the following:
1. several full Markov networks (without evidence) in the UAI format
2. a data generator for each network (python code) that will:
  * generate random q 
4. a partition of the set of variables \\(X\\) of each Markov network into three subsets:
  * hiddenvariables \\(H\\), 
  * observed or evidence variables \\(E\\)
  * query variables \\(Q\\) 
  * Namely, \\(H \\cup E \\cup Q = X\\), \\(H \\cap E = \\emptyset\\), \\(H \\cap Q = \\emptyset\\), and \\(H \\cap E = \\emptyset\\).

The data generator will generate samples from the probability distribution represented by the
Markov network. It will take as input (1) a Markov network, (2) number of samples m and (3)
path of the file where the m samples will be stored in a comma-separated (csv) format.

The Markov networks, partition of variables into query, hidden and evidence variables for each
network as well as the data generators will be published on the competition website. <br/>
You can use
your own computational resources (and therefore this phase is offline) to compile each Markov
network plus data to a relevant representation such that the following multi-label classification
task can be solved accurately and efficiently: *find the most-probable assignment (w.r.t. the Markov
network) to the query variables given an assignment of values to the evidence variables*.

Example representations include but are not limited to neural networks, graph neural networks,
auto-regressive models, junction trees, arithmetic circuits, AND/OR graphs, sum-product networks,
cutset networks, and probabilistic circuits. Note that you can use the Markov network
or the data or both to learn a *new representation*.

Technically, given a Markov network M, this task is equivalent to the marginal maximum-aposteriori
(MMAP) task and thus approaches that forgo the compilation phase and solve the prediction
task at test time using a MMAP solver can also participate in this task.


## Online Prediction Phase

You will provide us your compiled/learned models \\(C_k\\) (if any) for
each Markov network \\(M_k\\) and a program which takes as input (1) your compiled model \\(C_k\\) (if a
compiled model is not provided, we will assume that \\(C_k = M_k\\)) and (2) a csv file containing test
dataset D having t examples where each example is an assignment of values to all the evidence
variables, and outputs the most-probable assignment to all the query variables for each assignment
(test example) to the evidence variables given in D.
