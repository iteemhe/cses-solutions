# Ferris Wheel

This is actually a **Two Pointers** problem. But we need to sort the weight of kids first.

Here is my solution.

```c++
#pragma GCC optimize("Ofast,unroll-loops")
#pragma GCC target("avx,avx2,abm,bmi,bmi2,popcnt,lzcnt,fma")
#define NDEBUG
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
    ull n, x;
    cin >> n >> x;
    vector<ull> c(n);
    for (ull i = 0; i < n; ++i) {
        cin >> c[i];
    }
    sort(c.begin(), c.end());
    ull ans = 0;
    ull l = 0, r = c.size() - 1;
    while (l < r) {
        while (l < r && c[l] + c[r] > x) {
            ++ans;
            --r;
        }
        if (l == r) {
            break;
        }
        if (l < r && c[l] + c[r] <= x) {
            ++ans;
            ++l, --r;
        }
    }
    ans += (l == r);
    cout << ans << '\n';
}
```

