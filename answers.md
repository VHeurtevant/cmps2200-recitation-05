# CMPS 2200 Reciation 5
## Answers

**Name:** Viv Heurtevant


Place all written answers from `recitation-05.md` here for easier grading.







- **1b.**

Randomized Results: 
|      n |   qsort-fixed-pivot |   qsort-random-pivot |   tim-sort |
|--------|---------------------|----------------------|------------|
|    100 |               0.141 |                0.086 |      0.007 |
|    200 |               0.162 |                0.180 |      0.013 |
|    500 |               0.534 |                0.527 |      0.043 |
|   1000 |               1.133 |                1.592 |      0.185 |
|   2000 |               3.232 |                4.744 |      0.504 |
|   5000 |               8.616 |                9.842 |      0.462 |
|  10000 |              18.327 |               17.201 |      1.069 |
|  20000 |              31.129 |               38.095 |      2.465 |
|  50000 |             109.938 |              108.178 |      7.096 |
| 100000 |             221.239 |              273.143 |     15.280 |

Already Sorted Results (Note: maximum n is reduced to avoid recursion depth error)
|   n |   qsort-fixed-pivot |   qsort-random-pivot |   tim-sort |
|-----|---------------------|----------------------|------------|
| 100 |               0.460 |                0.118 |      0.002 |
| 200 |               1.433 |                0.213 |      0.002 |
| 500 |               9.976 |                0.815 |      0.006 |

In the already sorted results, the fixed pivot will always be the 'worst' decision so the work recurrence will be W(n) = W(n-1)+n which is O(n^2) , while the span is S(n)= S(n-1)+lg(n) which is O(nlgn). The random choice has expected O(n) work and O(lgn) span in this case- it is very unlikely it will have multiple worst picks while the deterministic fixed pivot will in the sorted case. This is reflected in the results, where the random pivot performs much better for sorted list.

The results are closer for the randomized list- there are even some cases where the fixed pivot performs better. The bounds become clearer at larger values of n, though, as seen when n=100,000.
 - **1c.**

See the charts in 1b for timsort's performance. Timsort has the advantage of looking for natural sorted subsequences, making it good for both the randomized and sorted case. Insertion is used to build up smaller subsequences. Then, resulting subsequences are merged until there is eventually one sorted list. Merging is considered whenever the run is either slightly less than or equivalent to a power of two. Timsort has a worst and average time complexity of O(nlogn). When the data is mostly sorted, it is O(n). Finding the local subsequences can be parallelized as well, making it efficient.
