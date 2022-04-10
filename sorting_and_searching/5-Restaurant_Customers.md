# Restaurant Customers

If we store the time duration that a customer stays in the restaurant as a pair, and sort them in ascending order. By sorting, there are only two possible relationships between two consecutive durations, overlap and separate.

By tracing the leaving time of all customers in a min heap, `std::priority_queue` and `std::greater`, we can know how many customers staying in the restaurant at any given time. We can thus find the maximum number of customers.

Here is the solution.

```c++
ll n, a, b;
void solve() {
    cin >> n;
    vpll c(n);
    all(c) cin >> e.first >> e.second;
    sort(c);
    priority_queue<ll, vll, greater<ll>> pq;
    ll curr = 0, ans = 0;
    all(c) {
        while (pq.size() && pq.top() < e.first) {
            pq.pop();
            --curr;
        }
        pq.ep(e.second);
        ans = max(ans, ++curr);
    }
    cout << ans << '\n';
}
```
