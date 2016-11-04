###Code 1
```
library(arules)
library(arulesViz)

admissions <- read.table("binary.csv", header=T, sep=",")
col_names <- names(admissions)
admissions[,col_names] <- lapply(admissions[,col_names], factor)

str(admissions)

rules <- apriori(admissions,  parameter=list(minlen=2, supp=0.01, conf=0.02), appearance=list(rhs=c("admit=1"), default="lhs"), control=list(verbose=F))
rules.sorted <- sort(rules, by="confidence")

inspect(rules.sorted)

plot(rules.sorted)
plot(rules.sorted, method="grouped")
plot(rules.sorted, method="graph")
plot(rules.sorted, method="graph", control=list(type="items"))
plot(rules.sorted, method="paracoord", control=list(reorder=T))
```

###Code 2
```
source("http://bioconductor.org/biocLite.R")
biocLite("Rgraphviz")
```


###Project Status:
####I have developed an implementation that includes the parts of the original MineBot project involving the task of detecting running Minesweeper processes, reading relevant information from running processes from memory directly into my program, and then implementing procedures which allow for input move choices. I have also successfully completed the "cheat" portion of the project, so that 100% of Minesweeper grids can be solved by reading directly from memory. Most of the work remaining now involves the solving process of Minesweeper grids without "cheating".
