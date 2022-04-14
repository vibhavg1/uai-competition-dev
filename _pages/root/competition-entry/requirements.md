---
title: "Competition Entry"
permalink: /competition-entry/requirements/
---

## Solver Requirements

### Execution Environment

The evaluations will be run on Linux machines up to 8 GB memory made available.
We request that solvers be 64-bit executables, using only a single core (i.e., no parallel processes/threads). 
A solver will have available the following environment variables:


The solver's exit status will be recorded, treating 0 as normal and other numbers as an error. 
Processes exceeding time or memory limits will be killed (via a SIGKILL signal), and 
the final output solution (see format below) will be taken as the solver solution. 


### Command-line Format (TBD)

A solver will receive as input a filename of the model, a filename for the evidence, the query filename, and the task to solve. 
The query filename is only relevant to the marginal MAP task. 
Solvers working on the other three tasks should ignore this file.
```
./solver <input-model-file> <input-evidence-file>  <input-query-file>  <PR|MPE|MAR|MMAP|MLC>
```
The formats are described here:
* [Model Format](../file-formats/model-format.md)   
* [Evidence Format](../file-formats/evidence-format.md)
* [Query variables](../file-formats/query-format.md) (only applies to the marginal MAP task)
* [Result format](../file-formats/result-format.md)
    

### Result Format
The solver should generate a file and write the results to it. 
The output file should have the same name as the input model file, 
but with the added suffix “.XXX” where XXX is the task being solved (PR, MAR etc.). For example, after calling:
```
./solver Nets/grid5X5.uai Evid/grid5X5.uai.evid Query/grid5x5.uai.query  PR
```

