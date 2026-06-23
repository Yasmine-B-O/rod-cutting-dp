# Rod Cutting — Dynamic Programming

A complete walkthrough of the classic **rod-cutting optimization problem**, progressing from a naive
exponential-time recursive solution to a fully optimized iterative dynamic programming algorithm.

## Problem

Given a rod of length `n` and a price list `p` where `p[i]` is the price of a piece of length `i`,
find the maximum total value obtainable by cutting the rod into integer-length pieces — and reconstruct
**which cuts** produce that value.

```
p = [0, 2, 3, 7, 10]   # p[0] = 0 by convention
n = 4  ->  max value = 10  (sell the whole rod as one piece of length 4)
n = 5  ->  max value = 12  (cut into lengths 1 + 4)
```

## What's inside

The notebook builds up the solution in four stages:

| Stage | Approach | Time | Space | Practical limit |
|---|---|---|---|---|
| 1 | Naive recursion | Θ(2ⁿ) | O(n) call stack | n ≈ 25 |
| 2 | Naive recursion + cut reconstruction | Θ(2ⁿ) | O(n) | n ≈ 25 |
| 3 | Top-down memoization | O(n · \|p\|) | O(n) | n ≈ 900 (Python recursion limit) |
| 4 | Bottom-up iterative DP | O(n · \|p\|) | O(n) | n ≥ 100,000 |

Along the way it includes:
- **Empirical complexity validation** — timing the naive recursive solution against rod length and plotting
  the exponential blow-up.
- **Memoization** to eliminate redundant subproblem recomputation.
- **Solution reconstruction** — not just the optimal value, but the actual sequence of cuts that achieves it.
- **Iterative bottom-up rewrite** to remove Python's recursion limit entirely, scaling to rods of length
  100,000+ in well under a second.

## Why this problem matters

Rod cutting is a canonical introduction to dynamic programming: it has **overlapping subproblems**
(the same sub-rod length gets evaluated repeatedly under naive recursion) and an **optimal substructure**
(the optimal solution for a rod of length `n` is built from optimal solutions to shorter rods). The same
pattern — recursion → memoization → bottom-up tabulation — applies directly to coin change, knapsack,
longest common subsequence, edit distance, and optimal binary search tree construction.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook rod_cutting.ipynb
```

**Requirements:** Python 3.10+, `numpy`, `matplotlib`

## Repository structure

```
.
├── rod_cutting.ipynb   # main notebook
├── requirements.txt
└── README.md
```

## Related work

- [Optimal Binary Search Tree (DP)](https://github.com/YOUR_USERNAME/optimal-bst-dp) — applies the same
  bottom-up DP pattern to building search trees that minimize expected search cost given key frequencies.

## Author

Yasmine Bouaboud — Computing student, UM6P
