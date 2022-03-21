# Creating Strings

This is a standard problem that can be solved by using **Backtracking**. That is why the constraint is not very high.

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

static inline void backtracking(array<int, 26> &map, vector<string> &ans,
                                string &curr, const ull &in) {
    if (curr.size() == in) {
        ans.emplace_back(curr);
        return;
    }

    for (ull i = 0; i < 26; ++i) {
        if (map[i] > 0) {
            --map[i];
            curr.push_back(i + 'a');
            backtracking(map, ans, curr, in);
            curr.pop_back();
            ++map[i];
        }
    }
}

inline static void solve() {
    string in;
    cin >> in;
    array<int, 26> map{};
    for (const auto &c : in) {
        ++map[c - 'a'];
    }
    vector<string> ans;
    string curr;
    backtracking(map, ans, curr, in.size());
    cout << ans.size() << '\n';
    for (const auto &s : ans) {
        cout << s << '\n';
    }
}
```