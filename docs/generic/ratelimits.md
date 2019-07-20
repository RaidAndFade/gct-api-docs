# Ratelimits

Ratelimits are limits on requests in specific intervals, to prevent flooding of the APIs.

## Ratelimits currently in place

Ratelimits are in the form of BUCKETS, meaning that any path, account, ip, endpoint, could have their own ratelimit. Ofcourse this causes things to be confusing so I will try my best to keep it simple.

As of right now, there are very basic **GLOBAL** ratelimits in place:

- All unregistered users have 4 requests per 10 seconds (this is based on IP).
- All regisered users have 4 per second.
- All *UPGRADED* users have 12 per second.

These ratelimits are reported to users in the typical format of `X-Ratelimit` headers

## Ratelimit Headers

Header | Type | Meaning
--- | Type | ---
X-RateLimit-Limit | Int | The limit on the specific path you are trying to access
X-RateLimit-Remaining | Int | How many requests you have left until you reach your limit
X-RateLimit-Reset | Float | The epoch time in seconds(with decimal milliseconds) until your bucket expires (and your ratelimit refreshes)
Retry-After | Float | The time in seconds(with decimal milliseconds) until you may access the path again.

### Final Note

*Because of the Header Bucket system, Ratelimits are always subject to change, and you should **ALWAYS** refer to the headers, not to this documentation.*