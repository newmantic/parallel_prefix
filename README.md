# parallel_prefix


Parallel Prefix (Scan) Algorithms are fundamental in parallel computing, used to perform operations like prefix sums, prefix products, and other associative operations efficiently over a sequence of elements. The main advantage of these algorithms is that they can compute results in parallel, significantly reducing the time complexity compared to sequential approaches.


Prefix Sum (Scan):
The prefix sum of a sequence is the set of running totals of the sequence.
Inclusive Prefix Sum: The i-th element of the output is the sum of all elements up to and including the i-th element.
Exclusive Prefix Sum: The i-th element of the output is the sum of all elements before the i-th element.


For a sequence x_1, x_2, ..., x_n:
Inclusive Prefix Sum:
y_i = sum(x_j for j in range(1, i+1))
for i = 1, 2, ..., n
Exclusive Prefix Sum:
y_i = sum(x_j for j in range(1, i))
for i = 1, 2, ..., n
For the exclusive prefix sum, y_1 = 0.


Parallel Computation:
The goal of a parallel prefix algorithm is to compute these sums (or other associative operations) in parallel, which significantly reduces the time complexity compared to a sequential approach.

Associative Operation:
An operation ⊕ is associative if:
(a ⊕ b) ⊕ c = a ⊕ (b ⊕ c)
Common associative operations include addition, multiplication, logical AND/OR, etc.

Up-Sweep (Reduce) Phase:
In the up-sweep phase, partial sums are computed in a tree-like structure.
Each pair of elements is combined, and their result is propagated upwards in a binary tree.
The height of the tree is log2(n), where n is the number of elements.
The result at the root of the tree is the total sum of all elements.

Down-Sweep Phase:
The down-sweep phase (used for exclusive scans) propagates the prefix sums back down the tree.
At each level, the sum is split into its components, and the results are passed to the lower levels of the tree.


Time Complexity:
The parallel prefix algorithm has a time complexity of O(log n), assuming an idealized parallel machine where each operation can be performed in constant time.
