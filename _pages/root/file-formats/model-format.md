---
title: ""
permalink: /file-formats/model-format/
---

## Model Format
> We use the simple text file format specified below to describe problem instances (Markov networks). 
The format is a generalization of the Ergo file format initially developed by Noetic systems Ergo software.
We use the **.uai** suffix for the challenge benchmark network files.

### Structure
A file in the UAI format consists of the following two parts, in that order:
```
<Preamble>
<Function tables>
```
The contents of each section (denoted <…> above) are described in the following:

### Preamble
Our description of the format will follow a simple Markov network with three variables and two functions. A sample preamble for such a network is:

```
MARKOV
3
2 2 3
2
2 0 1
2 1 2
```

The preamble starts with one line denoting the type of network. Generally, this can be either BAYES (if the network is a Bayesian network) or MARKOV (in case of a Markov network). However, note that this year all networks will be given in a Markov networks (i.e. Bayesian networks will be moralized).

The second line contains the number of variables. The next line specifies the cardinalities of each variable, one at a time, separated by a whitespace (note that this implies an order on the variables which will be used throughout the file). The fourth line contains only one integer, denoting the number of cliques in the problem. Then, one clique per line, the scope of each clique is given as follows: The first integer in each line specifies the number of variables in the clique, followed by the actual indexes of the variables. The order of this list is not restricted. Note that the ordering of variables within a factor will follow the order provided here.

Referring to the example above, the first line denotes the Markov network, the second line tells us the problem consists of three variables, let's refer to them as X, Y, and Z. Their cardinalities are 2, 2, and 3 respectively (from the third line). Line four specifies that there are 2 cliques. The first clique is X,Y, while the second clique is Y,Z. Note that variables are indexed starting with 0.


### Function tables
In this section each factor is specified by giving its full table (i.e, specifying value for each assignment). The order of the factor is identical to the one in which they were introduced in the preamble, the first variable have the role of the 'most significant’ digit. For each factor table, first the number of entries is given (this should be equal to the product of the domain sizes of the variables in the scope). Then, one by one, separated by whitespace, the values for each assignment to the variables in the function's scope are enumerated. Tuples are implicitly assumed in ascending order, with the last variable in the scope as the 'least significant’. To illustrate, we continue with our Markov network example from above, let's assume the following conditional probability tables:

| X | P(X) |
| :--- | :----: | 
| 0 | 0.436 |
| 1 | 0.456 |


| X |	Y |	P(Y,X) |
| :--- | :--- | :----: | 
| 0 |	0 |	0.128  |
| 0 |	1 |	0.872 |
| 1 |	0 |	0.920 |
| 1 |	1 |	0.080 |


| Y | 	Z | 	P(Z,Y) | 
| :--- | :--- | :----: | 
| 0 | 	0 | 	0.210 | 
| 0 | 	1 | 	0.333 | 
| 0 | 	2 | 	0.457 | 
| 1 | 	0 | 	0.811 | 
| 1 | 	1 | 	0.000 | 
| 1 | 	2 | 	0.189 | 

```
2
 0.436 0.564

4
 0.128 0.872
 0.920 0.080

6
 0.210 0.333 0.457
 0.811 0.000 0.189
```
(Note that line breaks and empty lines are effectively just a whitespace, exactly like plain spaces “ ”. They are used here to improve readability.)

### Summary
In summary, a problem file consists of 2 sections: the preamble and the full the function tables, the names and the labels. For our Markov network example above, the full file will look like:
```
MARKOV
3
2 2 3
3
1 0
2 0 1
2 1 2

2
 0.436 0.564

4
 0.128 0.872
 0.920 0.080

6
 0.210 0.333 0.457
 0.811 0.000 0.189
```

