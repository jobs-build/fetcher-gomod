# fetcher-gomod

<p align="center">
  <img src="docs/assets/jobs-logo.jpg" alt="JOBS — Jonas' Own Build System" width="520">
</p>

The JOBS **`gomod`** fetcher as a standalone, JOBS-buildable repo.

`gomod` fetches one Go module (path + version) into a `cache/download/...` tree, for
offline `go build` (it is driven by the `goplugin` build plugin, which turns a
`go.sum` into one `gomod` import per module).

It is a shell script (no compilation) that drives `go mod download`. The JOBS
fetcher manifest (`fetchers.toml`, entry `gomod`) fetches a pinned tarball of this
repo and builds it with `BUILD.jobs`, which places `fetch` at the artifact root and
declares the Go toolchain as a **runtime dep**: since jobs-iroh's hermetic imports a
fetcher runs in a sandbox holding only the static shell userland and its own
runtime closure, so the toolchain's `/jobs/store/<key>` path is baked into
`env.sh`, which `fetch` sources on start. Nothing is taken from the runner host.

## Build it

```
jobs develop --source .
```
