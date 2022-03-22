# Dice Combinations

Every integer can be divided into $n -1$, $n - 2$ ... $n - 6$. Because dices can only produce an outcome between $1$ and $6$, which means for each additional throw, there are $6$ possible previous outcomes.

Now, we see the relationship between the number $n$ and previous six elements. Intuitively, we can write a top-down DP solution now. But the constraint is $10^6$, which is too large for top-down DP solution.

Fortunately, we can optimize the algorithem by memorization, and convert top-down to a bottom-up solution.

Thus, we can solve this problem in linear time and linear space. Here is my solution.

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
    vector<ull> dp(n + 1);
    dp[0] = 1; // Consider there is only one way to get zero
    for (ull i = 1; i <= n; ++i) {
        for (ull j = 1; j <= 6; ++j) {
            if (i < j) {
                break;
            }
            dp[i] += dp[i - j];
            if (dp[i] >= inf) { // % is less efficient than subtraction
                dp[i] -= inf;
            }
        }
    }
    cout << dp.back();
}
```

