# Preempted Single Machine Scheduling Problem

## Introduction

Combinatorial optimization is a topic where we need to apply mathematical techniques to find optimal solutions within a finite set of possible solutions. For some problems, there are algorithms that are able to find optimal solutions in polynomial time. However, we face NP-hard problems where it may be necessary to search through an exponential number of solutions. A well-known NP-complete combinatorial optimization problem is the 0-1 Knapsack Problem.

In the context of this project, we study an application of the Linear Assignment Problem (LAP) as a relaxation of the single machine scheduling problem, minimizing the total weighted completion time within a new scheme of the Branch-and-Bound Alorithm (BnBA). We provide a computational study of all ingredients of our BnBA, namely, the tolerance based Branching Rules (upper, lower and bottleneck tolerances) as well as Lower and Upper Bounds (to the unknown optimal values of our problem) improved by the chosen values of tolerances and heuristic based on the Weighted Shortest Remaining Processing Time (WSRPT) rule respectively. Recent discoveries show that we are able to find optimal solutions for the Scheduling Problem (SP) in instances with hundreds of jobs in very few CPU time.

Read full PDF: [report.pdf](report.pdf)

## Example (summarized)

Given several weighted job instances (which can be split in many parts), can find an optimal solution very quickly.

Let 3 jobs such as:
- The first job contains `2` parts, the release time is `1` and the weight is `2`.
- The second job contains `3` parts, the release time is `2` and the weight is `8`.
- The thirds job contains `2` parts, the release time is `3` and the weight is `10`.

During our experiment, we reduce the problem to a Linear Assignment Problem (LAP):

| t       | 1 | 2 | 3 | 4  | 5  | 6  | 7  |
|---------|---|---|---|----|----|----|----|
| J_{1,1} | 0 | 0 | 0 | 0  | 0  | 0  | -  |
| J_{1,2} | - | 2 | 4 | 6  | 8  | 10 | 12 |
| J_{2,1} | - | 0 | 0 | 0  | 0  | -  | -  |
| J_{2,2} | - | - | 0 | 0  | 0  | 0  | -  |
| J_{2,3} | - | - | - | 8  | 16 | 24 | 32 |
| J_{3,1} | - | - | 0 | 0  | 0  | 0  | -  |
| J_{3,2} | - | - | - | 10 | 20 | 30 | 40 |

And we find that the best solution (which minimizes the cost) is this sequence:
- J_{1,1}
- J_{2,1}
- J_{2,2}
- J_{1,2}
- J_{2,3}
- J_{3,1}
- J_{3,2}
