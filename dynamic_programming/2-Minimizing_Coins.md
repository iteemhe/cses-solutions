# Minimizing Coins

This question is very similar to the previous problem, *Dice Combinations*.

The only thing we need to concern is that the input coins array is not guaranteed to be sorted. So we must sort it before running other parts of the algorithm.

Here is my solution. Linear time with linear space.

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
    vector<ll> dp(x + 1, inf);
    dp[0] = 0;
    for (ull i = 0; i < n; ++i) {
        for (ll j = coins[i]; j < dp.size(); ++j) {
            dp[j] = min(dp[j], dp[j - coins[i]] + 1);
        }
    }
    cout << (dp.back() == inf ? -1 : dp.back());
}
```

