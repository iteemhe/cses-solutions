# Concert Tickets

Our goal is to find the maximum price possible price that does not exceed the bided price. Therefore, `std::lower_bound` combined with `std::multiset` is the ideal way to solve this problem.

`std::lower_bound` will find the minimum element in a sorted data structure such as `std::multiset` that is at least as large as the target value. So, the previous element of `std::lower_bound` is the highest possible prices we can charge.

Here is my solution.

```c++
ll n, m, h, t;
void solve() {
    cin >> n >> m;
    multiset<ll, greater<ll>> s;
    rep(i, 0, n) {
        cin >> h;
        s.ep(h);
    }
    while (m--) {
        cin >> t;
        auto it = s.lower_bound(t);
        if (it == s.end()) {
            cout << "-1\n";
        } else {
            cout << *it << '\n';
            s.erase(it);
        }
    }
}
```
