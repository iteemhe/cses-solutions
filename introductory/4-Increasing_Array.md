# Increasing Array

We can solve this problem by subtracting previous element with the current element to get the steps we need to even out the difference. Do not write extra and meaningless loops for this problem.

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
    ll n, ans = 0, p, c;
    cin >> n >> p;
    for (ll i = 0; i < n - 1; ++i) {
        cin >> c;
        if (p > c) {
            ans += p - c;
        } else {
            p = c;
        }
    }
    cout << ans;
}
```