# Movie Festival

This question can be solved by greedy. Though I cannot prove the greedy algorithm mathematically, the idea is to find the movie that ends as earlier as possible to save time for other later movies.

So, here comes my solution.

```c++
ll n, a, b;
void solve() {
    cin >> n;
    vpll m(n);
    all(m) cin >> e.second >> e.first;
    sort(m);
    ll prev = -1, ans = 0;
    all(m) {
        if (e.second >= prev) {
            prev = e.first;
            ++ans;
        }
    }
    cout << ans << '\n';
}
```
