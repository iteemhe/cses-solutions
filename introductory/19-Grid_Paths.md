# Grid Paths

The intuition is to use backtracking. However, the time complexity for backtracking is too high, and the constraint is out of the normal range that the standard backtracking can handle.

The key to this problem is $7 \times 7$ grid and $48$ steps. If we draw a path that consists 48 steps from the upper-left corner to the lower-left corner, all cells in that grid must be reached once. This means that tha path can fill the whole grid.

So, in this case, if we find the left- or right-hand side has more than two empty cells, that path cannot be the path we want. We can improve our vanilla backtracking now.

Here is the solution, which is kind of messy. I think you can use bit mask in this question too.

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

inline static ll ans = 0;
inline static array<array<bool, 7>, 7> b{};
inline static string path;
inline static void backtracking(const ull &steps, const ull &r, const ull &c) {
    if (r == 6 && c == 0) {
        ans += (steps == 48);
        return;
    }
    if ( //
        ((r == 0 || (r < 6 && b[r + 1][c] && b[r - 1][c])) && c > 0 && c < 6 &&
         !b[r][c - 1] && !b[r][c + 1]) ||

        ((r == 6 || (r > 0 && b[r - 1][c] && b[r + 1][c])) &&
         (c > 0 && c < 6 && !b[r][c - 1] && !b[r][c + 1])) ||

        ((c == 0 || (c < 6 && b[r][c + 1] && b[r][c - 1])) && r > 0 && r < 6 &&
         !b[r - 1][c] && !b[r + 1][c]) ||

        ((c == 6 || (c > 0 && b[r][c - 1] && b[r][c + 1])) && r > 0 && r < 6 &&
         !b[r - 1][c] && !b[r + 1][c]) //
    ) {

        return;
    }
    b[r][c] = true;
    if (path[steps] == '?') {
        if (r < 6 && !b[r + 1][c])
            backtracking(steps + 1, r + 1, c);
        if (r > 0 && !b[r - 1][c])
            backtracking(steps + 1, r - 1, c);
        if (c < 6 && !b[r][c + 1])
            backtracking(steps + 1, r, c + 1);
        if (c > 0 && !b[r][c - 1])
            backtracking(steps + 1, r, c - 1);
    } else {
        if (r < 6 && path[steps] == 'D' && !b[r + 1][c])
            backtracking(steps + 1, r + 1, c);
        if (r > 0 && path[steps] == 'U' && !b[r - 1][c])
            backtracking(steps + 1, r - 1, c);
        if (c < 6 && path[steps] == 'R' && !b[r][c + 1])
            backtracking(steps + 1, r, c + 1);
        if (c > 0 && path[steps] == 'L' && !b[r][c - 1])
            backtracking(steps + 1, r, c - 1);
    }
    b[r][c] = false;
}

inline static void solve() {
    cin >> path;
    backtracking(0, 0, 0);
    cout << ans << '\n';
}
```
