# Permutations

Firstly, let us observe a few small number solutions for this problem.

```plain
N = 1
YES

N = 2
NO, 1 2 cannot be rearranged to form such sequence

N = 3
NO, 1 2 3 cannot be rearranged to form such sequence

N = 4
YES, 2 4 1 3 is the unique combination

N = 5
YES, 2 4 1 3 5 (1 3 5 2 4 is also possible)

N = 6
YES, 2 4 6 1 3 5
```

We can find an interesting pattern. All possible combinations are composed with two parts. The first half of such sequence is all even numbers and second half is all odd numbers. By the way, the reverse of possible solutions are also valid solutions. For convenience, I choose the first half is even. Because this is not a mathematical proof, I cannot guarantee there are no other combinations. But my method is more intuitive.

Intuitively, when you draw **Beautiful Permutations** on a piece of paper, your instinct tells you to draw a upward/downward sloping curve. However, if you make the difference between any two consecutive numbers two, there is no way you can form such permutation with integers in $[1, n]$, because they are an **Arithmetic Progression** with a common difference $1$.

Then, the distance between any two consecutive odd or even numbers are two. You might want to split integers in $[1, n]$ into two piles, odd and even, and sort them in ascending order. Now, if you try to draw the Beautiful Permutations on a piece of paper, you will find that your graph contains two upward sloping curves and a cliff in the middle.

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
    if (n == 2 || n == 3) {
        cout << "NO SOLUTION";
        return;
    }
    for (ull i = 2; i <= n; i += 2) {
        cout << i << ' ';
    }
    for (ull i = 1; i <= n; i += 2) {
        cout << i << ' ';
    }
}
```

Here is another way to form beautiful permutation, but is less intuitive, but it was the first solution I came up with. This method constructs the sequence backward for odd numbers and from the front for even numbers.

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
    ll n;
    cin >> n;
    if (n % 2 == 1) {
        for (ll i = n - 1; i > 0; i -= 2) {
            cout << i << " ";
        }
        for (ll i = n; i > 0; i -= 2) {
            cout << i << " ";
        }
    } else {
        for (ll i = 2; i <= n; i += 2) {
            cout << i << " ";
        }
        for (ll i = 1; i <= n; i += 2) {
            cout << i << " ";
        }
    }
}
```
