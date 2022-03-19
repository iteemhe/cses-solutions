# Missing Number

This problem can be solved in linear time with constant space by using a mathematical method.

The given sequence contains $n - 1$ distinct integers in range $[1, n]$, which can be treated as an **Arithmetic Progression**.

By convention, we denote the sum of all integers in $[1, n]$ as $S_n$. If we assume the index of the missing integer is $i$, then the missing number is $a_i$.

Then, by finding the sum of integers in the given array, we have the relationship such that $S_n - S_{missing} = a_i$.

```c++
#include <bits/stdc++.h>
using namespace std;
using ui = unsigned int;
using ll = long long int;
using ull = unsigned long long int;
using ld = long double;
[[maybe_unused]]                                     //
inline static constexpr const ll inf = 1000000007ll; // 1e9 + 7
inline static void solve();
int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    solve();
}

inline static void solve() {
    ull n, num, sum = 0;
    cin >> n;
    for (ull i = 0; i < n - 1; ++i) {
        cin >> num;
        sum += num;
    }
    cout << ((1 + n) * n >> 1) - sum;
}
```
