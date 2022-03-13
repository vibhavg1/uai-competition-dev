---
title: "Competition Entry"
permalink: /competition-entry/requirements/
---

## Solver Requirements

#### Execution Environment

The evaluations will be run on Intel i7 machines running Linux with up to 4 GB memory made available (some memory will be reserved for evaluation scripts, etc.). We request that solvers be 64-bit executables, using only a single core (i.e., no parallel processes/threads). A solver will have available the following environment variables:

* INF_TIME: total CPU runtime limit (in seconds, e.g., “600”);
    
* INF_MEMORY: total memory limit (in gigabytes, e.g., “2.5”);
    

The solver's exit status will be recorded, treating 0 as normal and other numbers as an error. Processes exceeding time or memory limits will be killed (via a SIGKILL signal), and the final output solution (see format below) will be taken as the solver solution. In case a solution is not available, a naive one (e.g. bit-wise univariate potential maximum for the MAP task) will be assumed.

#### Command-line Format

A solver will receive as input a filename of the model, a filename for the evidence, the query filename, and the task to solve ( PR| MPE| MAR| MMAP). The query filename is only relevant to the marginal MAP task. Solvers working on the other three tasks should ignore this file.
```
./solver <input-model-file> <input-evidence-file>  <input-query-file>  <PR|MPE|MAR|MMAP>
```
The formats are described here:

* [Model Format](../file-formats/model-format.md)
    
* [Evidence Format](../file-formats/evidence-format.md)
    
* [Query variables](../file-formats/query-format.md) (only applies to the marginal MAP task)
    
* [Result/Output format](../file-formats/result-format.md)
    

#### Output Format

The solver should generate a file and write the results to it. The output file should have the same name as the input model file, but with the added suffix “.XXX” where XXX is the task being solved (PR, MAR etc.). For example, after calling:
```
./solver Nets/grid5X5.uai Evid/grid5X5.uai.evid Query/grid5x5.uai.query  PR
```
The solution should be found in the working directory in a file named grid5X5.uai.PR. Solver output to stdout and stderr will be logged, for debugging purposes.
