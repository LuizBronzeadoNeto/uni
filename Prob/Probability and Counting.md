# Naive definition of probability
The earliest definition of probability was to count the number of ways an event could happen and divide it by the total number of possible outcomes.$$P_{naive}(A)= \frac{|A|}{|S|}$$
For the complements of the events considered:$$P_{naive}(A^c)= 1 - P_{naive}(A)$$
The naive definition is very restrictive, as it requires S to be finite, with equal mass for each pebble (event). Nonetheless, there are still several problem types where this definition is applicable, those being **symetrical** problems and when outcomes are equally likely by **design**.
# How to count
### Theorem 1.4.7 (Sampling with replacement)
Consider $n$ objects and making $k$ choices from them with replacement. Then there are $n^k$ possible outcomes (where order matters).
### Theorem 1.4.8 (Sampling without replacement)
Consider $n$ objects and making $k$ choices from them, one at a time without replacement. Then there are $n(n-1)...(n-k+1)$ possible outcomes for $1\leq k \leq n$.
By convention, for $k=1$, $n(n-1) ... (n-k+1) = n$ 
Furthermore, this is where the permutation formula originates, as in a permutation $k =n$, therefore $n(n-1)...(n-n+1) = n!$
### Adjusting for overcounting
In many counting problems, it is not easy to directly count each possibility once and only once. If, however, we are able to count each possibility exactly $c$ times for some $c$, then we can adjust by dividing by $c$.
### Definition 1.4.14 (Binomial coefficient)
For any nonnegative integers $k$ and $n$, the binomial coefficient $\binom{n}{k}$ read as "$n$ choose $k$", is the number of subsets of size $k$ for a set of size $n$ (remember that a set of size $n$ will have $2^n$ subsets).
### Theorem 1.4.15 (binomial coefficient formula)
For $k \leq n$ we have $$\binom{n}{k} = \frac{n(n-1) ... (n-k+1)}{k!}$$
Notice we have the first $k +1$ factors of $n!$, to get the remaining ones, we multiply and divide by $(n-k)!$ $$\binom{n}{k} = \frac{n(n-1) ... (n-k+1)(n-k)(n-k-1)...1}{(n-k)!k!}$$
Therefore:
$$\binom{n}{k} = \frac{n!}{(n-k)!k!}$$
for $k > n$, we have $\binom{n}{k} = 0$
Often however, the first expression in this theorem is better for calculation, as factorials grow extremely quickly.

# Non-naive definition of probability
Given the problems mentioned with the previous definition, it can only take us so far.
### Definition 1.6.1 (General definition of probability)
A probability space consists of a sample space $S$ and a probability function $P$ which takes an event $A \subseteq S$ as input and returns $P(A)$, a real number between 0 and 1, as output. $P$ must satisfy the following axioms:
1. $P(\emptyset) = 0, P(S) =1$ 
2. if $A_1, A_2,...$ are disjoint events then: $$P(\bigcup_{j=1}^\infty A_j)=\sum_{j=1}^\infty P(A_j)$$
	(That is to say the Probability of the arbitrary union of all pairwise disjoint subsets $A$ (mutually exclusive) of $S$ is equal to the sum of the probability of all subsets $A$)
### Properties of probability
For any events $A$ and $B$:
1. $P(A^c) = 1 - P(A)$
2. if $A \subseteq B$ then $P(A) \leq P(B)$
3. $P(a \cup B) = P(A) + P(B) - P(A \cap B)$ 

