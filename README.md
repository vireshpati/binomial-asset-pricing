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

## Option Type Comparison

### 2. Computational Complexity

#### Recursive Implementation
- **Asian Options**: Highest complexity (O(2^n * n))
  - Requires tracking both price and running sum
  - Shows exponential growth in computation time
  - Most severely affected by the curse of dimensionality

- **European Options**: Moderate complexity (O(2^n))
  - Simpler state space (only price and time)
  - Significantly faster than Asian options
  - Still shows exponential growth

- **American Options**: Similar base complexity to European (O(2^n))
  - Additional comparison at each node for early exercise
  - Slightly slower than European due to extra calculations
  - Maintains exponential growth pattern

#### Dynamic Programming Implementation
- **Asian Options**: Most improved by DP
  - Reduces to O(n^2) complexity
  - Greatest relative speedup compared to recursive version
  - Still slowest among the three types due to extra state variable

- **European Options**: Most efficient
  - Reduces to O(n) complexity
  - Fastest computation times
  - Most memory-efficient due to simpler state space

- **American Options**: Similar to European with DP
  - Slightly higher constants due to early exercise checks
  - Maintains O(n) complexity
  - Efficient reuse of computed values

### 3. Memory Usage Patterns

#### State Space Requirements
- **Asian Options**: Largest state space
  - Requires storing (time, price, running sum) triplets
  - Highest memory usage in DP implementation
  - Most benefit from memoization

- **European/American Options**: Smaller state space
  - Only stores (time, price) pairs
  - More efficient memory utilization
  - Faster cache lookups in DP implementation
