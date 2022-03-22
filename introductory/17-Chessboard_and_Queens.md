# Chessboard and Queens

This is a classic problem. The solution I always use to solve **8-Queen**, **N-Queen** and other variants is backtracking.

If you are unfamiliar with this kind of problem. There are many detailed explanations on Google.

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

inline static bool is_valid(const array<string, 8> &mat, const ll &r,
                            const ll &c) {
    auto valid = [&](const ll &r, const ll &c) {
        return r >= 0 && c >= 0 && r < 8 && c < 8;
    };
    for (ll i = 0; i < 8; ++i) {
        if (mat[i][c] == 'Q' ||
            (valid(r - i, c - i) && mat[r - i][c - i] == 'Q') ||
            (valid(r - i, c + i) && mat[r - i][c + i] == 'Q')) {
            return false;
        }
    }
    return true;
}

inline static void nq(array<string, 8> &mat, const ull &r, ll &ans) {
    if (r == 8) {
        ++ans;
        return;
    }
    for (ull i = 0; i < 8; ++i) {
        if (mat[r][i] != '.') {
            continue;
        }
        if (is_valid(mat, r, i)) {
            mat[r][i] = 'Q';
            nq(mat, r + 1, ans);
            mat[r][i] = '.';
        }
    }
}

inline static void solve() {
    array<string, 8> mat{};
    for (ull i = 0; i < 8; ++i) {
        cin >> mat[i];
    }
    ll ans = 0;
    nq(mat, 0, ans);
    cout << ans;
}
```
