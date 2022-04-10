# Bit Strings

By using some basic combinatorics, we know that there are $2^n$ combinations. But the question is how to calculate it faster with constraint $10^6$, so `std::pow` will not work in this problem.

The solution is to use bit manipulation.

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
    cout.tie(nullptr);
    cin.tie(nullptr);
    solve();
}

inline static void solve() {
    ll n, ans = 1;
    cin >> n;
    while (n-- > 0) {
        ans <<= 1;
        ans %= inf;
    }
    cout << ans;
}
```

There is actually a $O(logN)$ solution. But since the constraints are pretty low, it would not make much difference.

```c++
ll pow(const ll &x) {
    if (x == 1) {
        return 2;
    }
    ll a = pow(x >> 1);
    return a * a * (x & 1 ? 2 : 1) % mod;
}

void solve() {
    cin >> n;
    cout << pow(n);
}
```
