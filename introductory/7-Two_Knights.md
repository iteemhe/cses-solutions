# Two Knights

I think there is a DP solution to this problem. But ultimately, I came up with a mathematical solution.

There are only two possible situations that two knights can attack each other, when they are in a $2 \times 3$ or $3 \times 2$ grid. Therefore, we only need to calculate there are how many possible such grids in the grid.

The number of $2 \times 3$ grids is $(n - 1) \times (n - 2)$. When counting the number of such grid, it is equivalent to moving a grid horizontally and vertically. That is why we subtract $n$ by $1$ and $2$.

The total number of placement of two knights on a $n \times n$ grid is $n^2$ choose 2, $C_{n^2}^{2}$, which is $\frac{n^{2}(n^2 - 1)}{2}$.

Because the number of $2 \times 3$ and $3 \times 2$ grids are equal, and there are two possible ways to place knights in such grid. The total number of possible ways to place two knights without letting them attack each other is $C_{n^2}^{2} - 4(n - 1)(n - 2)$. This equation still holds when $n < 2$.

So here is our solution

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
    for (ll i = 1; i <= n; ++i) {
        cout << (i * i * (i * i - 1) / 2 - 4ll * (i - 1) * (i - 2)) << '\n';
    }
}
```
