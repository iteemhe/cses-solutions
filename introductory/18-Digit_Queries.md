# Digit Queries

This one is more like a mathematical problem instead of a programming one.

For each additional digits, there are 9, 90, 900, 9000... numbers. For example, 10 to 99 contains 90 numbers with 2 digits.

That is how we know how many digits the number have.

Then, since we already know the digits of the query number. It is easy to know the position of that number.

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
    for (ll i = 0; i < n; ++i) {
        ll k;
        cin >> k;
        ll l = 0, d = 1;
        while (l + d * 9 * (ll)pow(10, d - 1) < k) {
            l += d * 9 * (ll)pow(10, d - 1);
            ++d;
        }
        k -= l;
        ll s = (ll)pow(10, d - 1); // the start of range
        ll pos = k / d;            // the position of number
        ll num = s + pos;          // the number that the query asks for
        k = k % d;
        if (k == 0) {
            --num;
            k = d;
        }
        cout << to_string(num)[(ull)k - 1] << '\n'; // the digit
    }
}
```
