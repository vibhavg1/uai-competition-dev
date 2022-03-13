---
title: "File Formats"
permalink: /file-formats/evidence-format/
---

## Evidence Format
Evidence is specified in a separate file. This file has the same name as the original network file but with an added **.evid** suffix. For instance with respect to the UAI model format, _problem.uai_ will have evidence in _problem.uai.evid_.

The evidence file consists of a single line. The line will begin with the number of observed variables in the sample, followed by pairs of variable and its observed value. For example, given a binary variable we specify 0 as false and 1 as true. The indexes correspond to the ones implied by the original problem file.

If, for our example Markov network given [here](./model-format.md), Y has been observed as having its first value and Z with its second value, the file _example.uai.evid_ would contain the following:

```
2 1 0 2 1
```
