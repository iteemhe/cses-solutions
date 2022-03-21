# Two Sets

Here are a few properties of possible sets.

1. If numbers can be divided into two groups with equal sum, the sum of all numbers must be a even number. (with 2, we do not need to check this.)

2. Any four consecutive natural number can be divided into two groups with equal sum. However, $1\ 2\ 3$ is an exception. We can split them into $1\ 2$ and $3$.

> Proof: We let $n$ be the start of such sequence, if we want to split them into two groups with the equal sum, there are three possible combinations, but $n + (n + 1) = n + 2$ is the only one that yields a valid integer, so $n$ can only be $1$. But if we want to let $n + (n + 3) = (n + 1) + (n + 2)$, this holds for every natural number.

So, firstly we need to check if the sum is even. Then, we check if the number is divisible by four. If it cannot be divided by four, we check if $n - 3$ is divisible by four.

Here is my solution

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
    ll n;
    cin >> n;
    if (n < 3 || (n % 4 != 0 && (n - 3) % 4 != 0)) {
        cout << "NO";
        return;
    }
    vector<int> l, r; // for output
    if (n % 4) {
        l = {1, 2};
        r = {3};
        for (ll i = 4; i <= n - 3; i += 4) {
            l.emplace_back(i);
            l.emplace_back(i + 3);
            r.emplace_back(i + 1);
            r.emplace_back(i + 2);
        }
    } else {
        for (ll i = 1; i < n; i += 4) {
            l.emplace_back(i);
            l.emplace_back(i + 3);
            r.emplace_back(i + 1);
            r.emplace_back(i + 2);
        }
    }
    cout << "YES\n";
    cout << l.size() << '\n';
    for (const auto &a : l) {
        cout << a << ' ';
    }
    cout << '\n';
    cout << r.size() << '\n';
    for (const auto &a : r) {
        cout << a << ' ';
    }
}
```
