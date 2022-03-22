# Coin Combinations I

This problem is excatly the same as *Dice Combinations*. 

Here is my solution.

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
    ll x;
    cin >> n >> x;
    vector<ll> coins(n);
    for (ull i = 0; i < n; ++i) {
        cin >> coins[i];
    }
    sort(coins.begin(), coins.end());
    vector<ll> dp(x + 1);
    dp[0] = 1;
    for (ull i = 1; i <= x; ++i) {
        for (const auto &c : coins) {
            if (i < c) {
                break;
            }
            dp[i] += dp[i - c];
            if (dp[i] >= inf) {
                dp[i] -= inf;
            }
        }
    }
    cout << dp.back();
}
```

