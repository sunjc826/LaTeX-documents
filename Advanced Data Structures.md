March 2022

Book: Advanced Data Structures (ADS)

## Preface
### Time complexity
**Proposition** $f(n) = O(g(n))$ iff $\exists C, \forall n\in \mathbb{N} f(n) < Cg(n)$

$(\implies)$ Suppose $f(n) = O(g(n))$. Then, $\limsup_{n\rightarrow \infty}\frac{f(n)}{g(n)} = c < \infty$. From mathematical analysis we know that $\forall \epsilon > 0, \exists N\in\mathbb{N}, \frac{f(n)}{g(n)} < c+\epsilon$, that is $f(n) < (c+\epsilon)g(n)$.
We then define $C:=c+\epsilon$ for a particular (arbitrary) choice of $\epsilon$. Next, by possibly redefining $g$, i.e. $\forall n\leq N, g(n)\gets \max\{g(n), C^{-1}f(n)\}$, we can assume that $\forall n\in\mathbb{N}, f(n)\leq Cg(n)$, which is the desired result. Furthermore, redefining $g$ on a finite set does not change its asymptotic behavior.

$(\impliedby)$ Conversely, suppose $\forall n\in\mathbb{N}, f(n) < g(n)$. Then any convergent subsequence $(\frac{f(n_k)}{g(n_k)})$ converges to a real number $<c$. Hence $f(n) = O(g(n))$. 
$\square$

**Discussion** We examine two varying definitions of amortized complexity.
In CLRS, $T(n)$ denotes the total time of n operations. For clarity, we will use $S(m)$ instead, as S stands for sum and $m$ is the number of operations on an object. Anyways, in CLRS, to say that the amortized time is $O(f(m))$ means that $\frac{S(m)}{m} = O(f(m))$.
In ADS, to say that the amortized time is $O(f(n))$ means that when any sequence of $m$ operations are conducted on an object whose size is bounded above by $n$ (during these $m$ operations), the total time $S(m) = \sum_{1\leq i\leq m}T_i(n_i) \leq g(n) + mCf(n)$, where $n_i$ is the size of the object at the i-th operation and $T_i$ is the time taken. This implies
$$
    \frac{S(m) - g(n)}{m} = O(f(n))
$$

Evidently, there are some differences between the 2 definitions. By my understanding, in CLRS, the lack of an $n$ variable suggests that $m$ is somewhat of proxy for the size of the object, and the change in size of the object across the $m$ operations is accounted for with just the $m$ variable. The initial size of the object is not so important as $m$ tends to infinity.
In ADS, the number of operations and size of object are separated. However, note that ADS makes a slightly stronger statement, since the $g(n) + mCf(n)$ is not asymptotic. Consider the case when $m=1$. ADS then says that $S(1) \leq g(n) + Cf(n)$, where the $g(n)$ term accounts for a possibly larger initial object size.

From the previous 2 segments, we see that ADS' complexity definitions does not rely so much on asymptotics, but rather universal quantification over the entirety of $\mathbb{N}$.





