# Option Pricing Analysis with Dynamic Programming

## Overview
This project implements and compares different approaches to pricing Asian, European, and American options using recursive and dynamic programming methods in a binomial tree model.

## Features
- Implementation of three option types:
  - Asian Options (arithmetic average)
  - European Options
  - American Options
- Two calculation methods:
  - Pure recursive approach
  - Dynamic programming with memoization (@lru_cache)
- Visualization:
  - Binomial tree structures
  - Node visit heat maps
  - Runtime comparisons
  - Complexity analysis

## Key Findings
1. **Performance Comparison**
   - Dynamic Programming (DP) significantly outperforms pure recursive approaches
   - The speedup is particularly noticeable for larger time steps (T)
   - Asian options show the highest computational complexity due to the additional state variable

2. **Complexity Analysis**
   - Recursive methods show exponential growth with increasing time steps
   - DP methods demonstrate much better scaling
   - European options compute faster than Asian options due to simpler state space

3. **Memory vs Speed Trade-off**
   - DP methods trade memory usage for speed by caching results
   - The heat maps visualize the number of repeated calculations avoided by DP

## Model Parameters
- Initial Stock Price (S0): 4
- Up Factor (u): 2
- Down Factor (d): 0.5
- Risk-free Rate (r): 0.25
- Risk-neutral Probabilities (p_tilde, q_tilde): 0.5, 0.5
- Strike Price: 4
- Time Steps (T): Variable (5-25 for complexity analysis, can go for higher periods, but may slow down)

## Visualization Tools
- Binomial tree structures
- Runtime comparisons using both linear and logarithmic scales
- Heat maps showing node visit frequencies
- Complexity growth analysis across different time steps
