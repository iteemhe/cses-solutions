# Palindrome Reorder

We can easily know that in palindromes either the number of all elements are even or there is only one odd element(we can place the extra in the middle).

Now, we can solve this problem by using **Radix Sort**, since our constraint is alphabets in A-Z. The time is linear and space is 26, which is constant.

Here is my solution

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
    string in;
    cin >> in;
    array<int, 26> map{};
    for (const auto &c : in) {
        ++map[c - 'A'];
    }
    ll count = 0;
    for (const auto &c : map) {
        count += c & 1;
    }
    if (count > 1) {
        cout << "NO SOLUTION";
        return;
    }
    string lhs, mid;
    lhs.reserve(in.size() >> 1);
    for (ull i = 0; i < 26; ++i) {
        lhs += string(map[i] / 2, i + 'A');
        if (map[i] % 2) {
            mid += i + 'A';
        }
    }
    cout << lhs + mid + string(lhs.rbegin(), lhs.rend());
}
```
