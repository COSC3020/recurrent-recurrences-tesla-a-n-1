# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

Observing the pattern:
```
      T(n) = T(n/13) + 5

           = T(n/13^2) + 5 + 5
  
           = T(n/13^3) + 5 + 5 + 5
  
           = T(n/13^k) + 5k
  ```
Since the recursion stops when n <= 1 then

n/13^k<=1$ or $n<=13^k

k=log<sub>13</sub>n

After substituting the formula is $T(n) = T(n/13^k) + 5k$

=1+5log<sub>13</sub>n

Since log<sub>13</sub>n grows logarithmically, the asymptotic complexity of T(n) is
$T(n) \in \Theta(log n)$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

Using the (Master Theorem)[https://towardsdatascience.com/all-about-mater-theorem-with-its-proof-93455cdb6a4e] where '$T(n) = aT(n/b) + O(n^d)$' and it's three cases
```
Case 1: d < log(a) [base b] => Time Complexity = O(n ^ log(a) [base b])

Case 2: d = log(a) [base b] => Time Complexity = O((n ^ d) * log(n) )

Case 3: d > log(a) [base b] => Time Complexity = O((n ^ d))
```
In this case a = 13, b = 13, d = 0 (since the constant is O(1)) and the recurrence has the form: T(n) = 13T(n/13) + O(1)

Comparing d and log<sub>b</sub>a, d = 0 and log<sub>b</sub>a = log<sub>13</sub>13 = 1

d < log<sub>b</sub>a This is Case 1 so the time complexity = O(n^log<sub>b</sub>a) = O(n^1) = $T(n) \in \Theta(n)$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$

The same Master Theorem rules apply here, the only difference is 2n instead of 5.

This makes a = 13, b = 13, and d = 1

log<sub>b</sub>a is still log<sub>13</sub>13 which is also still just 1

In this recurrence, d = log<sub>b</sub>a which is case 2 in the Master Theorem

Time Complexity = O(n^1 * log(n)$ = O(nlog(n))

$T(n) \in \Theta(n log n)$

## Sources

I referenced the Master Theorem and it's cases at https://towardsdatascience.com/all-about-mater-theorem-with-its-proof-93455cdb6a4e Otherwise: "I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice."

This was my submission from last semester
