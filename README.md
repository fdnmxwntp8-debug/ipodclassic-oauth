# iPod Classic Spotify OAuth bridge

Spotify now requires HTTPS redirect URIs for new applications. iOS can receive the
authorization result through the custom `ipodclassic://callback` scheme, so this
static page bridges the two:

1. Spotify redirects to `https://fdnmxwntp8-debug.github.io/ipodclassic-oauth/`.
2. This page forwards the same query string to `ipodclassic://callback`.
3. `ASWebAuthenticationSession` inside the app intercepts that custom scheme.

The page contains no secrets. Authorization codes are bound to the PKCE verifier
that never leaves the device.
