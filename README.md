# fetcher-gomod

<p align="center">
  <img src="docs/assets/jobs-logo.jpg" alt="JOBS — Jonas' Own Build System" width="520">
</p>

The JOBS **`gomod`** fetcher as a standalone, JOBS-buildable repo.

`gomod` fetches one Go module (path + version) into a `cache/download/...` tree, for
offline `go build` (it is driven by the `goplugin` build plugin, which turns a
`go.sum` into one `gomod` import per module).

It is a shell script (no compilation). The JOBS fetcher manifest (`fetchers.toml`,
entry `gomod`) fetches a pinned tarball of this repo and builds it with `BUILD.jobs`
— which simply places `fetch` at the artifact root using the seeded shell — then
promotes the output to `fetcher:gomod:<platform>`.

## Build it

```
jobs develop --source .
```
