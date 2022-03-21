# Coin Piles

The direct way to solve and think about this problem is not that intuitive. Therefore, we can approach this reversely.

Now, the problem becomes ***If we have need to form two piles of coins, and we can only place 1 and 2 or 2 and 1 to two piles respectively, there could be how many coins in each pile?***

1. The sum of number of coins must be the multiple of $3$. Because we always put 1 and 2 or 2 and 1 to each pile. $1 + 2 = 3$.

2. The maximum coins in the $min(a, b)$ must be greater than or equal to $\frac{max(a, b)}{2}$. Because it is impossible to form such piles. Consider we always put 1 and 2. The number of coins in $a$ is $n$ and in $b$ is $2n$. So, in the most extreme case, $2a = b$.

Then, we can solve this problem easily.

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
    while (n-- > 0) {
        ll a, b;
        cin >> a >> b;
        if (2 * min(a, b) < max(a, b) || (a + b) % 3) {
            cout << "NO\n";
        } else {
            cout << "YES\n";
        }
    }
}
```
