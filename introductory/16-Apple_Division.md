# Apple Division

This is question can also be solved by ***Backtracking***. However, we can also use ***Bit Mask*** in this problem to convert recursive solution to a more efficient iterative solution.

Intuitively, we know that the smallest difference is zero when we evenly split numbers into two piles. That is the approach we will use.

First of all, we calculate the sum of all numbers. Because our goal is to divide numbers into two groups with the same sum, we only need to calculate one group actually.

So, here is my solution.

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
    ull n;
    cin >> n;
    array<ll, 20> arr{};
    ll sum = 0, ans = 0;
    for (ull i = 0; i < n; ++i) {
        cin >> arr[i], sum += arr[i];
    }
    for (ull i = 0; i < (1ull << n); ++i) { // bitmask
        ll cs = 0;
        for (ull j = 0; j < n; ++j) {
            if ((i >> j) & 1) {
                cs += arr[j];
            }
        }
        if ((cs << 1) <= sum) {
            ans = max(ans, cs);
        }
    }
    cout << sum - (ans << 1);
}
```
