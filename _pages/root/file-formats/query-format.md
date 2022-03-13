---
title: "File Formats"
permalink: /file-formats/query-format/
---

## Query File Format (only applies to Marginal MAP task)
Query variables for marginal MAP inference are specified in a separate file. This file has the same name as the original network file but with an added **.query** suffix. For instance with respect to the UAI model format, _problem.uai_ will have evidence in _problem.uai.query_.

The query file consists of a single line. The line will begin with the number of query variables, followed by the indexes of the query variables. The indexes correspond to the ones implied by the original problem file.

If, for our example Markov network given [here](./model-format.md), we want to use Y as the query variable the file _example.uai.query_ would contain the following:

```
1 1
```
