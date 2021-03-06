# Gray Code

To solve this problem, we need to know some basic properties of Gray Code. Generally, Gray Code can be generated by Bit Manipulation, `n xor n >> 1`.

After knowing that, we have a straightforward solution.

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

inline static void to_binary(const ll &length, ll n) {
    string ans(length, '0');
    for (ll i = length - 1; i >= 0; --i) {
        ans[i] = (n & 1) + '0';
        n >>= 1;
    }
    cout << ans << '\n';
}

inline static void solve() {
    ll n;
    cin >> n;
    ll s = 1ll << n; // total number of gray code
    for (ll i = 0; i < s; ++i) {
        to_binary(n, i ^ (i >> 1));
    }
}
```
