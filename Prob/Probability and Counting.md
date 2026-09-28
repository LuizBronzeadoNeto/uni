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
Notice we have the first $k$ factors of $n!$, to get the remaining ones, we multiply and divide by $(n-k)!$ $$\binom{n}{k} = \frac{n(n-1) ... (n-k+1)(n-k)(n-k-1)...1}{(n-k)!k!}$$
Therefore:
$$\binom{n}{k} = \frac{n!}{(n-k)!k!}$$
for $k > n$, we have $\binom{n}{k} = 0$
Often however, the first expression in this theorem is better for calculation, as factorials grow extremely quickly.


