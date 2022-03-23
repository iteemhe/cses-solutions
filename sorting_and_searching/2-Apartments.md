# Apartments

In order to maximize the number of people who can get an appartment, we should firstly try to give out appartment to people with lowest requirement.

Also, at the same time, we should distribute the smallest appartments first to those people with lowest requirement.

Then, here is my solution based on my above thought.

```c++
#include <vector>
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
    ull n, m;
    ll k;
    cin >> n >> m >> k;
    vector<ll> d(n);
    for (ull i = 0; i < n; ++i) {
        cin >> d[i];
    }
    sort(d.begin(), d.end());
    vector<ll> app(m);
    for (ull i = 0; i < m; ++i) {
        cin >> app[i];
    }
    sort(app.begin(), app.end());
    ull ans = 0;
    for (ull l = 0, r = 0; r < d.size() && l < app.size();) {
        ll ma = d[r] + k, mi = d[r] - k;
        if (app[l] < mi) { // It is impossible anyone else will accept this appartment.
            ++l;
        } else if (app[l] > ma) { // Current person cannot accept this appartment.
            ++r;
        } else {
            ++ans;
            ++l, ++r;
        }
    }
    cout << ans << '\n';
}
```

