# Trailing Zeros

First of all, you could not compute the number and then count the number of trailing zeros. That would cause overflow and TLE. We need to come up with a more clever way to solve this.

Intuitively, trailing zeros can only be formed by multiplying $5$ and a even number. And we can find that, the multiple of $5$ can form one trailing zero(excluding multiple of $25$, $125$, ...). And $25$ can yield two trailing zeros, $125$ can yield three...

You might ask how can we find even numbers to form trailing zeros. Well, I cannot give you a very rigorous proof, but I can use density to explain. Obviously, the density of even numbers are higher than the density of multiple of $5$, $25$, ... . So, we do not need to worry about how many even numbers there are, we can guarantee there are enough even numbers to yield trailing zeros.

Now, let us decompose factorial. For example, the factorial of $100$ is $100 \times 99 \times 98 \times 97 \times ...$. The number of multiple of $5$(also consider multiple of $25$, $125$, ...) is $\frac{100}{5} = 20$. And the number of multiple of $25$ is $\frac{100}{25} = 4$, ... . It seems like we count some numbers many times. For example, $100$ is the multiple of $5$ but also a multiple of $25$. However, $100$ can yield two zeros, we count it twice on purpose.

Above is the start point of our algorithm. The sum of numbers of multiple of $5$, $25$, $125$, $625$, ... is the number of trailing zeros.

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
    ll n, ans = 0;
    cin >> n;
    for (ll i = 5; n / i >= 1; i *= 5) {
        ans += n / i;
    }
    cout << ans;
}
```
