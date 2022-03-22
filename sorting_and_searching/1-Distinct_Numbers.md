# Distinct Numbers

This problem can be solved easily by using ***Set***. But the only problem is that we need to reserve space to prevent rehashing, which is extremely time consuming.

Here is my solution.

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
    unordered_set<ui> s(n);
    while (n-- > 0) {
        ui num;
        cin >> num;
        s.insert(num);
    }
    cout << s.size();
}
```
