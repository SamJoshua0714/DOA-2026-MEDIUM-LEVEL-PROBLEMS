# DOA 2026 Questions: Medium

Nine medium-difficulty problems in the same format as the Hard set. Each one is a themed rework of a standard LeetCode medium, with a small twist so it is not a copy of the original.

Reference solutions (Python 3) are in [`solutions/`](solutions). Run `python tests/run_samples.py` to check every sample.

| # | Problem | Based on |
|---|---------|----------|
| 1 | Cargo Balance Triples | [3Sum](https://leetcode.com/problems/3sum/) |
| 2 | Cipher Crate Sorting | [Group Anagrams](https://leetcode.com/problems/group-anagrams/) |
| 3 | Crater Fields | [Number of Islands](https://leetcode.com/problems/number-of-islands/) |
| 4 | Fuel Cell Combinations | [Coin Change](https://leetcode.com/problems/coin-change/) |
| 5 | Spore Spread | [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) |
| 6 | Module Boot Order | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) |
| 7 | Telemetry Climb | [Number of Longest Increasing Subsequence](https://leetcode.com/problems/number-of-longest-increasing-subsequence/) |
| 8 | Maintenance Windows | [Merge Intervals](https://leetcode.com/problems/merge-intervals/) |
| 9 | Fuel Flow Intervals | [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) |

## 1. Cargo Balance Triples

### Problem Statement

A cargo bay holds `N` crates, each with a signed weight offset (positive = heavier than standard, negative = lighter). A **balanced triple** is three crates whose offsets sum to exactly `0`. Count the distinct balanced triples, where two triples are the same if they contain the same multiset of values. Crates with equal offsets are interchangeable.

### Input Format

- The first line contains `N`.
- The second line contains `N` integers, the crate offsets.

### Output Format

Print the number of distinct balanced triples.

### Sample Input 1

```
6
-1 0 1 2 -1 -4
```

### Sample Output 1

```
2
```

### Sample Input 2

```
3
0 1 1
```

### Sample Output 2

```
0
```

### Sample Input 3

```
4
0 0 0 0
```

### Sample Output 3

```
1
```

### Explanation

In sample 1, the distinct triples are `(-1, -1, 2)` and `(-1, 0, 1)`. In sample 2, no triple sums to zero. In sample 3, `(0, 0, 0)` counts once even though four crates can form it.

### Constraints

- `3 ≤ N ≤ 3000`.
- `-10^5 ≤ offset ≤ 10^5`.
- Expected time: `O(N^2)`; auxiliary space: `O(1)` beyond sorting.

### Reference

- [3Sum](https://leetcode.com/problems/3sum/)

---

## 2. Cipher Crate Sorting

### Problem Statement

Each of `N` crates is labelled with a lowercase word. Two crates belong to the same group if their labels are anagrams of each other, meaning one can be rearranged into the other. Report how many groups exist and the size of the largest group.

### Input Format

- The first line contains `N`.
- The second line contains `N` space-separated lowercase words.

### Output Format

Print the number of groups and the size of the largest group, separated by a space.

### Sample Input 1

```
6
eat tea tan ate nat bat
```

### Sample Output 1

```
3 3
```

### Sample Input 2

```
1
a
```

### Sample Output 2

```
1 1
```

### Sample Input 3

```
5
ab ba abc cab bca
```

### Sample Output 3

```
2 3
```

### Explanation

In sample 1, the groups are `{eat, tea, ate}`, `{tan, nat}`, and `{bat}`. Sample 2 has a single crate. In sample 3, `{ab, ba}` and `{abc, cab, bca}` form two groups.

### Constraints

- `1 ≤ N ≤ 10^4`.
- `1 ≤ |word| ≤ 100`.
- Words contain only lowercase English letters; duplicates are possible and count separately.

### Reference

- [Group Anagrams](https://leetcode.com/problems/group-anagrams/)

---

## 3. Crater Fields

### Problem Statement

A survey drone maps a region as an `m × n` grid. `1` marks a crater cell and `0` marks flat ground. Craters that touch up, down, left, or right belong to the same crater field. Diagonal contact does not connect cells. Find the number of crater fields and the area (cell count) of the largest one.

### Input Format

- The first line contains `m n`.
- The next `m` lines each contain `n` space-separated values, each `0` or `1`.

### Output Format

Print the number of crater fields and the largest area, separated by a space. Print `0 0` if there are no craters.

### Sample Input 1

```
4 5
1 1 0 0 0
1 1 0 0 0
0 0 1 0 0
0 0 0 1 1
```

### Sample Output 1

```
3 4
```

### Sample Input 2

```
2 2
1 0
0 1
```

### Sample Output 2

```
2 1
```

### Sample Input 3

```
1 3
0 0 0
```

### Sample Output 3

```
0 0
```

### Explanation

In sample 1, the fields have areas `4`, `1`, and `2`. In sample 2, the two craters touch only diagonally, so they are separate. Sample 3 has no craters.

### Constraints

- `1 ≤ m, n ≤ 300`.
- Each cell is `0` or `1`.
- Expected time: `O(mn)`.

### Reference

- [Number of Islands](https://leetcode.com/problems/number-of-islands/)

---

## 4. Fuel Cell Combinations

### Problem Statement

A rover is charged using fuel cells in `N` distinct capacities, with an unlimited supply of each. To reach a target charge of exactly `T`, find the fewest cells needed and the number of distinct combinations that reach `T`. Combinations are unordered, so `1 + 2` and `2 + 1` are the same.

### Input Format

- The first line contains `N T`.
- The second line contains `N` distinct positive integers, the capacities.

### Output Format

Print the minimum number of cells and the number of distinct combinations modulo `1,000,000,007`, separated by a space. Print `-1 0` if `T` cannot be reached.

### Sample Input 1

```
3 11
1 2 5
```

### Sample Output 1

```
3 11
```

### Sample Input 2

```
1 3
2
```

### Sample Output 2

```
-1 0
```

### Sample Input 3

```
3 10
1 5 10
```

### Sample Output 3

```
1 4
```

### Explanation

In sample 1, `5 + 5 + 1` uses three cells, and there are `11` unordered combinations in total. In sample 2, capacity `2` can never sum to `3`. In sample 3, a single `10` is optimal; the four combinations are `10`, `5 + 5`, `5 + 1×5`, and `1×10`.

### Constraints

- `1 ≤ N ≤ 12`.
- `0 ≤ T ≤ 10^4`.
- `1 ≤ capacity ≤ 10^4`.
- Expected time: `O(N · T)`.

### Reference

- [Coin Change](https://leetcode.com/problems/coin-change/)

---

## 5. Spore Spread

### Problem Statement

A greenhouse is an `m × n` grid. Each cell is `0` (empty), `1` (healthy plant), or `2` (infected plant). Every minute, each healthy plant that is directly up, down, left, or right of an infected plant becomes infected. Find the minimum number of minutes until no healthy plant remains, or report that it is impossible.

### Input Format

- The first line contains `m n`.
- The next `m` lines each contain `n` space-separated values from `{0, 1, 2}`.

### Output Format

Print the minimum number of minutes, or `-1` if some healthy plant can never be infected.

### Sample Input 1

```
3 3
2 1 1
1 1 0
0 1 1
```

### Sample Output 1

```
4
```

### Sample Input 2

```
3 3
2 1 1
0 1 1
1 0 1
```

### Sample Output 2

```
-1
```

### Sample Input 3

```
1 1
0
```

### Sample Output 3

```
0
```

### Explanation

In sample 1, the last plant is infected at minute `4`. In sample 2, the plant in the bottom-left corner is cut off by empty cells. In sample 3, there are no healthy plants, so `0` minutes are needed.

### Constraints

- `1 ≤ m, n ≤ 300`.
- Expected time: `O(mn)`.

### Reference

- [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

---

## 6. Module Boot Order

### Problem Statement

A station controller has `N` modules numbered `0` to `N - 1`. Each dependency `a b` means module `a` must boot before module `b`. Among all valid boot orders, print the lexicographically smallest one (compare the sequences element by element). If the dependencies contain a cycle, no order exists.

### Input Format

- The first line contains `N M`.
- The next `M` lines each contain a dependency `a b`.

### Output Format

Print the `N` module numbers in boot order, separated by spaces, or `-1` if no valid order exists.

### Sample Input 1

```
4 4
1 0
2 0
3 1
3 2
```

### Sample Output 1

```
3 1 2 0
```

### Sample Input 2

```
2 2
0 1
1 0
```

### Sample Output 2

```
-1
```

### Sample Input 3

```
3 0
```

### Sample Output 3

```
0 1 2
```

### Explanation

In sample 1, module `3` must come before `1` and `2`, which must both come before `0`; the smaller choice `1` goes first. In sample 2, the two modules wait on each other. In sample 3, there are no dependencies, so the order is ascending.

### Constraints

- `1 ≤ N ≤ 10^5`; `0 ≤ M ≤ 2 × 10^5`.
- `0 ≤ a, b < N`; duplicate dependencies may appear.
- Expected time: `O((N + M) log N)`.

### Reference

- [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)

---

## 7. Telemetry Climb

### Problem Statement

A probe logs `N` sensor readings. A **climb** is a subsequence of readings, in original order, that is strictly increasing. Find the length of the longest climb and the number of distinct longest climbs. Climbs are distinguished by the indices they use, so equal values at different positions count separately.

### Input Format

- The first line contains `N`.
- The second line contains `N` integers, the readings.

### Output Format

Print the longest length and the number of longest climbs modulo `1,000,000,007`, separated by a space.

### Sample Input 1

```
5
1 3 5 4 7
```

### Sample Output 1

```
4 2
```

### Sample Input 2

```
5
2 2 2 2 2
```

### Sample Output 2

```
1 5
```

### Sample Input 3

```
3
5 4 3
```

### Sample Output 3

```
1 3
```

### Explanation

In sample 1, the longest climbs are `1 3 5 7` and `1 3 4 7`. In samples 2 and 3, no reading exceeds an earlier one, so every single reading is a climb of length `1`.

### Constraints

- `1 ≤ N ≤ 2000`.
- `-10^9 ≤ reading ≤ 10^9`.
- Expected time: `O(N^2)`.

### Reference

- [Number of Longest Increasing Subsequence](https://leetcode.com/problems/number-of-longest-increasing-subsequence/)

---

## 8. Maintenance Windows

### Problem Statement

A depot schedules `N` maintenance windows, each a closed integer interval `[l, r]` of hours. Two windows merge if they share at least one hour. Windows that are adjacent but share no hour, such as `[1, 2]` and `[3, 4]`, stay separate. After merging everything, report how many windows remain and the total number of distinct hours covered.

### Input Format

- The first line contains `N`.
- The next `N` lines each contain `l r`.

### Output Format

Print the number of merged windows and the number of distinct hours covered, separated by a space.

### Sample Input 1

```
4
1 3
2 6
8 10
15 18
```

### Sample Output 1

```
3 13
```

### Sample Input 2

```
2
1 4
4 5
```

### Sample Output 2

```
1 5
```

### Sample Input 3

```
2
1 2
3 4
```

### Sample Output 3

```
2 4
```

### Explanation

In sample 1, the merged windows are `[1, 6]`, `[8, 10]`, and `[15, 18]`, covering `6 + 3 + 4 = 13` hours. In sample 2, the windows share hour `4`. In sample 3, no hour is shared.

### Constraints

- `1 ≤ N ≤ 10^5`.
- `0 ≤ l ≤ r ≤ 10^9`.
- Input intervals are not sorted.
- Expected time: `O(N log N)`.

### Reference

- [Merge Intervals](https://leetcode.com/problems/merge-intervals/)

---

## 9. Fuel Flow Intervals

### Problem Statement

A pipeline sensor records the net fuel change `x[i]` for each of `N` consecutive minutes. Count the contiguous time intervals whose net change is exactly `K`. Intervals are counted by their start and end positions, so equal intervals at different positions count separately.

### Input Format

- The first line contains `N K`.
- The second line contains `N` integers, the per-minute net changes.

### Output Format

Print the number of contiguous intervals whose sum equals `K`.

### Sample Input 1

```
3 2
1 1 1
```

### Sample Output 1

```
2
```

### Sample Input 2

```
3 3
1 2 3
```

### Sample Output 2

```
2
```

### Sample Input 3

```
3 0
1 -1 0
```

### Sample Output 3

```
3
```

### Explanation

In sample 1, the intervals covering positions `0..1` and `1..2` each sum to `2`. In sample 2, positions `0..1` (`1 + 2`) and position `2` (`3`) each sum to `3`. In sample 3, the intervals `[1, -1]`, `[0]`, and `[1, -1, 0]` each sum to `0`.

### Constraints

- `1 ≤ N ≤ 2 × 10^5`.
- `-1000 ≤ x[i] ≤ 1000`; `-10^9 ≤ K ≤ 10^9`.
- The answer fits in a signed 64-bit integer.
- Expected time: `O(N)`.

### Reference

- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
