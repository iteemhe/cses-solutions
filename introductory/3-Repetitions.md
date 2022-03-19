# Repetitions

This problem is asking for a standard **Two Pointers** solution. So, it can be solved in linear time and using constant space.

We use two pointers, `l` and `r`, stand for **left-hand side** and **right-hand side** respectively. Also, we use `cl` to keep track of the current length starts from last letter to find the maximum length.

There is nothing special need to be addressed. This is a standard solution.

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
    cin.tie(nullptr);
    solve();
}

inline static void solve() {
    string s;
    cin >> s;
    ull ans = 1, cl, l = 0, r = 0, n = s.size();
    while (r < n) {
        cl = 0;
        while (s[r] == s[l]) {
            ++r, ++cl;
        }
        ans = max(ans, cl);
        l = r;
    }
    cout << ans;
}
```
