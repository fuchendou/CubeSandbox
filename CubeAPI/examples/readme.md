# Examples

See the top-level [examples/](../../examples/) directory for standalone, runnable examples:

- [host-mount](../../examples/host-mount/) — mount host directories into a sandbox
- [network-policy](../../examples/network-policy/) — control outbound network access
- [browser-sandbox](../../examples/browser-sandbox/) — Playwright browser automation via CDP
- [code-sandbox-quickstart](../../examples/code-sandbox-quickstart/) — basic sandbox operations

## Sandbox inventory pagination

`GET /v2/sandboxes` returns the existing JSON array plus `X-Next-Token`. Pass the opaque header value as `nextToken` on the next request, keeping the same filters. `limit` is the number of raw node records examined per page (1–200, default 100), not the number of returned sandboxes. A page may be empty after filtering while still carrying a next token. Stop only when the header is empty; sparse node indices and a full final node window may require one additional empty page. The root `/sandboxes` response remains compatible.

The cursor version `cube-nodes-v1` records the next raw node index. It is an observation cursor, not a consistent cluster snapshot; list results cannot prove that resources are absent.
