# Sum of Two Values

This question can be solved by HashMap, `std::unordered_map`.

```c++
ll n, x;
void solve() {
    cin >> n >> x;
    vll nums(n);
    all(nums) cin >> e;
    unordered_map<ll, ll> m;
    m.reserve(n);
    rep(i, 0, n) {
        if (m.find(x - nums[i]) != m.end()) {
            cout << m[x - nums[i]] + 1 << ' ' << i + 1 << '\n';
            return;
        }
        m[nums[i]] = i;
    }
    cout << "IMPOSSIBLE\n";
}
```
