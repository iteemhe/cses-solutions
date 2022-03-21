# Number Spiral

The key to this question is to find the patter of layers of spirals. It is impractical to construct a matrix, without mentioning the upper bound of input can be $10^9$. There is a mathematical way to solve this question.

By observing the number of the first element of each row, we can find that for odd rows(1-index based), the number is $2^{i} - 1$, but for even rows the number is $2^n$. And we know each layer of spiral is a $i \times i$ square. So the number we are looking for is located on the $max(row, col)$ layer.

Here is the solution based on my thought.

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
    ll t;
    cin >> t;
    for (ll i = 0; i < t; ++i) {
        ll r, c;
        cin >> r >> c;
        ll pos = max(r, c); // The pos is determined by max(row, col)
        if (pos & 1) {
            cout << (pos - 1) * (pos - 1) + c + abs(pos - r);
        } else {
            cout << pos * pos - c + 1 - abs(pos - r);
        }
        cout << '\n';
    }
}
```
