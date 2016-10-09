<!--?title Prefix function. KMP Algorithm-->

# Prefix function. Knuth–Morris–Pratt algorithm

## Prefix function
Suppose we are given a string $s$ of length $n$. The **prefix function** $\pi$ for this string is an array of length $n$ where the $i$-th element $\pi[i]$ is equal to the greatest length of own maximum suffix of substring $s[0...i]$ matching it's prefix (where own maximum suffix means that it doesn't match entire string). In particular, value of $\pi[0]$ is equal to 0.

Definition of prefix function can be written as follows:

$$ \pi[i] = \max_{k=0 \ldots i} k : s[0 \ldots k-1] = s[i-k+1 \ldots i] $$

Let's consider an example. For string $abcabcd$ prefix functions is equal to $[0, 0, 0, 1, 2, 3, 0]$, meaning:

- for string $a$ there is no non-trivial prefix matching suffix
- for string $ab$ there is no non-trivial prefix matching suffix
- for string $abc$ there is no non-trivial prefix matching suffix
- for string $abca$ there is a prefix $a$ of length 1 matching suffix
- for string $abcab$ there is a prefix $ab$ of length 2 matching suffix
- for string $abcabc$ there is a prefix $abc$ of length 3 matching suffix
- for string $abcabcd$ there is no non-trivial prefix matching suffix

As another example, prefix function for string $aabaaab$ is equal to $[0, 1, 0, 1, 2, 2, 3]$

## Trivial algorithm

Following prefix function definition, we can write following algorithm to compute prefix function of of string $s$:

<pre><code>vector<int> prefix_function (string s) {
	int n = (int) s.length();
	vector<int> pi (n);
	for (int i = 0; i < n; i++)
		for (int k = 0; k <= i; k++)
			if (s.substr(0, k) == s.substr(i - k + 1, k))
				pi[i] = k;
	return pi;
}</code></pre>

Complexity of this trivial algorithm is $O(n^3)$.

## Practice Problems

List of tasks that can be solved using preifx function:

* [UVA # 455 "Periodic Strings" [Difficulty: Medium]](http://uva.onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=396)
* [UVA # 11022 "String Factoring" [Difficulty: Medium]](http://uva.onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=1963)
* [UVA # 11452 "Dancing the Cheeky-Cheeky" [Difficuluty: Medium]](https://uva.onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=2447)
