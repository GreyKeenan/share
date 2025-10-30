MATH1520 251030 lecture (11.3 to 11.5?)
========================================

<br>

<!-- INDEX -->
* [About The Integral Test (again)](#about-the-integral-test-again)
  * [Example: using the integral test to find convergence (1)](#example-using-the-integral-test-to-find-convergence-)
* [Estimating the value that some series converges to (chapter 11.3)](#estimating-the-value-that-some-series-converges-to-chapter-)
  * [Proof for the rule](#proof-for-the-rule)
  * [Example: estimating the value of convergence](#example-estimating-the-value-of-convergence)
* [The Direct Comparison Test (chapter 11.4)](#the-direct-comparison-test-chapter-)
  * [Direct Comparison example 1](#direct-comparison-example-)
  * [Direct Comparison example 2](#direct-comparison-example-)
* [The Limit Comparison Test (chapter 11.4)](#the-limit-comparison-test-chapter-)
  * [Limit Comparison Example 1](#limit-comparison-example-)
  * [Limit Comparison Example 2](#limit-comparison-example-)

<br>

### Info for Tyler:

* `x_y` is an `x` with subscripted `y`.
* `x[something]` is `x` with subscripted `something`.
* `x^[something]` or `x^y` is x with superscripted text.
* `SIGMA` is the summation symbol, capital-sigma
* `INTEGRAL` or `INT` is the integral symbol, long-s
* `inf` is infinity

Sorry if the notation is hard to visualize. I'm used to it.
Maybe try transcribing any formulas I have here down on paper
to see it better?

Also, she handed out a cheatsheet for this unit.
I grabbed one for you.
We get to use it during the test, apparently!

Also also, the index above links to the headers below.


About The Integral Test (again)
========================================

(I assume you remember)
The rules of the integral test are:

> Given some series `SIGMA[n=1]^inf a_n`
if `f(n) = a_n` for all values of `n`
and `f(x)` is continuous, positive, and decreasing on `[c, inf)`
(where `c` is some constant value),
then `INTEGRAL[c]^inf` converges if and only if `SIGMA[n=c]^inf a_n` converges.


Example: using the integral test to find convergence (1)
----------------------------------------

Determine if the following converges:

	SIGMA[n=1]^inf 1/e^n

---

	let f(x) = 1/e^x = e^-x

`f(x)` is continuous, positive, and decreasing on `[1, inf)`.
So, we can use the integral test.

	INT[1]^inf(e^-x)dx

Doing the algebra, *the integral* converges to `1/e`.
Therefore, the given series must converge as well.
(Note that the series doesn't converge to the same value.)


Example: using the integral test to find convergence (2)
----------------------------------------

Determine if the following converges:

	SIGMA[k=2]^inf 1/(kln(k))

---

	let f(x) = 1/(xln(x))

`f(x)` is continuous, positive, and decreasing on `[2, inf)`.
So, we can use the integral test.

	INT[2]^inf (1/lnx)(1/x)dx

Doing the algebra, the integral diverges to `ln|inf| - ln|ln2|`.
Therefore, the given series must diverge as well.
(Note that the series doesn't converge to the same value.)


Estimating the value that some series converges to (chapter 11.3)
========================================

If we know that a series converges *by the integral test*,
we can use interals to estimate the value which the series converges to.
Let's look at what the rule is and then see how to prove it.

First, recall that a partial sum is defined as:

	s_n = SIGMA[k=1]^n a_n
	s = s[inf]

So, the value we are trying to estimate is `s`.

The rule is as follows:

	(s_n + INT[n+1]^inf f(x)dx) < s < (s_n + INT[n]^inf f(x)dx)

This relationship is what we will be using to estimate the value of `s`.
Don't forget that it must pass the Integral Test
before you can use this rule.


Proof for the rule
----------------------------------------

TODO

(the proof is in the textbook if you really need it, sorry.
I'll add it when I get around to it.)

<!--
A partial sum is the sum of *part* of a series,
but not the entire infinite sum.
The *remainder* is everything in a series that is *not* in the partial sum.
In other words, if `R_n` refers to the remainder
corresponding to the partial sum `s_n`:

	s - s_n = R_n
-->


Example: estimating the value of convergence
----------------------------------------

> Note: Recall how p-serieses work from the last lecture.
Let `p` be some constant.
`SIGMA[n=1]^inf 1/n^p` converges (by the integral test) if `p > 1`.

**Task:** approximate `SIGMA[n=1]^inf (1/n^3)` with `n = 5`.

Lets use the rule above:

	(s_n + INT[n+1]^inf f(x)dx) < s < (s_n + INT[n]^inf f(x)dx)

... and plug in our values:

	(s_5 + INT[6]^inf (x^-3)dx) < s < (s_5 + INT[5]^inf (x^-3)dx)

Working on it in parts, let's start with `s_5`:

	s_5 = 1 + 1/8 + 1/27 + 1/64 + 1/125 ~= 1.856

Now, the integrals. I trust that you can do this if you need.

	INT[6]^inf (x^-3)dx
	= -(1/2)(1/inf - 1/36)
	= 1/72

	INT[5]^inf (x^-3)dx
	= (-1/2)(1/inf - 1/25)
	= 1/50

Putting it all together:

	1.856 + 1/72 < s < 1.857 + 1/50
	1.1994 < s < 1.2057

> (notice that `1.856` is rounded down for the lesser-side,
and rounded up to `1.857` for the greater-side.
This is to account for potential rounding errors.)

So, we have a rough estimation of the value of `s`.
We can pick any value between there,
but its simplest to just take the midpoint:

	s ~= (1.1994 + 1.2057) / 2
	s ~= 1.20255

Tada.

Our maximum error, then, can be given as:

	|1.1994 - 1.2057| / 2 = 0.00315

... when we consider that the actual value of `s`
must be between those two values.


The Direct Comparison Test (chapter 11.4)
========================================

Say we have two serieses:

	SIGMA[n=1]^inf a_n = seriesA
	SIGMA[n=1]^inf b_n = seriesB

If `0 <= a_n <= b_n` for all values of `n`, we can say:
(Be careful not to do a logical fallacy here.)

* If seriesB converges, seriesA also converges.
* If seriesA diverges, seriesB also diverges.


Direct Comparison example 1
----------------------------------------

Determine if the series converges:

	SIGMA[n=1]^inf 1/(n^2 + 5)

Let's use the direct comparison test.
First, we need to pick some other series to compare it to.
Let's use:

	SIGMA[n=1]^inf 1/n^2 = seriesB

... because it is conveniently similar,
and we solved its convergence in the last lecture.

Consider that the following is true:

	0 < 1/(n^2 + 5) < 1/n^2

So, we can use the comparison test with these two.
We know that seriesB converges by the integral test.
(It's a p-series with `p > 1`, so it must converge.)
So, since seriesB converges, seriesA must also converge.


Direct Comparison example 2
----------------------------------------

Determine if the series converges:

	SIGMA[n=1]^inf (4 + sin(n)) / 3^n

Let's try to set this up for the comparison test.

	-1 <= sin(n) <= 1
	3 <= 4 + sin(n) <= 5

	3/3^n <= (4 + sin(n))/3^n < 5/3^n

	3/3^n > 0

	0 <= (4 + sin(n))/3^n < 5/3^n

Now, we can use `5/3^n` for our other sequence to compare against.

	SIGMA[n=1]^inf (5/3^n)
	= (5)SIGMA[n=1]^inf (1/3)^n

That's a geometric series, so we can tell that it converges.
SeriesB converges, so seriesA must also converge.





The Limit Comparison Test (chapter 11.4)
========================================

Say we have two serieses:

	SIGMA[n=1]^inf a_n = seriesA
	SIGMA[n=1]^inf b_n = seriesB

If `a_n > 0` and `b_n > 0` for all `n`,
and `lim[n->inf] (a_n / b_n) > 0` (and that limit doesn't diverge).
then we can say:

* If seriesB converges, seriesA also converges.
* If seriesB diveregs, seriesA also diverges.


Limit Comparison Example 1
----------------------------------------

Does this diverge:

	SIGMA 1/(n+1)

First, lets the direct comparison test, what we used before:

	0 < 1/(n+1) < 1/n

Unfortunately, `1/n` diverges,
so we cannot make any conclusion about `1/(n+1)`
from the direct comparison test (using that sequences at least).

Now, let's try the limit comparison test.
We can guess that `1/(n+1)` will behave similarly to
`1/n` because they have the same degree in the denominator.
Let's prove that hypothesis using the test.

First, we must establish that the test's requirements have been met.
We have to show that the test is applicable in this case:

	a_n = 1/(n + 1)   > 0
	b_n = 1/n         > 0

	a_n / b_n
	... algebra
	= 1 + 1/n

	lim[n->inf] (1 + 1/n) = 1

	lim[n->inf] (a_n / b_n) > 0

The conditions have been met.
Therefore, since seriesB diverges, seriesA must diverge as well.


Limit Comparison Example 2
----------------------------------------

Does this diverge:

	SIGMA (n + 6^n)/(n + 5^n)

> (do it with the Limit Comparison Test, not the Divergence Test)

We'll guess that it behaves like:

	SIGMA (6^n / 5^n) = SIGMA (6/5)^n

Now, for the limit comparison test algebra:

	a_n / b_n
	...
	= (n6^n + 30^n) / (n5^n + 30^n)

Now, taking the limit of that and considering the positive terms:

	lim[n->inf] (that) = 1 > 0

The limit comparison test is applicable.
SeriesB diverges, so seriesA must diverge as well.




# END OF LECTURE
