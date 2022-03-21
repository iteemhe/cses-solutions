# Tower of Hanoi

I will not spend much time on explaining this problem. Here is the solution on Wikipedia, <https://en.wikipedia.org/wiki/Tower_of_Hanoi#Recursive_solution>.

I recommend using the recursive method. It is more clear. The idea is basically split disks into two parts and switch the target and auxiliary pag every time we move. Finally, we will reach the base case that the number of disks is $1$.

My code is translated from the pseudoscope on Wikipedia.

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

inline static void h(const ll &n, const ll &source, const ll &target,
                     const ll &aux) {
    if (n > 0) {
        h(n - 1, source, aux, target);
        cout << source << ' ' << target << '\n';
        h(n - 1, aux, target, source);
    }
}

inline static void solve() {
    ll n;
    cin >> n;
    cout << pow(2, n) - 1 << '\n';
    h(n, 1, 3, 2);
}
```
