# Weird Algorithm

This problem is also known as *Collatz conjecture*, *3n + 1* Problem. The question asks us to print out all numbers in this sequence, which is known as **Hailstone Sequence**.

There is not a more clever way or a mathematical method to solve this problem. Brute force is the only choice left for us.

There is one point I need to mention. If you Google Hailstone Sequence, you can find that sometimes the height of the highest number can excess the range of `int`. So, I use `unsigned long long` to handle this overflow issue. Because all numbers are positive.

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
    ull n;
    cin >> n;
    while (n != 1) {
        cout << n << ' ';
        if (n & 1) {
            n = 3 * n + 1;
        } else {
            n >>= 1;
        }
    }
    cout << 1;
}
```
