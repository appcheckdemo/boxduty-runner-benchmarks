# Boxduty cache comparison

This branch adapts the [RunsOn cache suite](https://github.com/runs-on-demo/benchmark-public/blob/4e2f0dd8c72c1d9638d6902aff5a341f85d21f7f/.github/workflows/cache.yml).
Both runners generate 4 GiB of random bytes, save it with the same
`actions/cache` revision, remove the file, and immediately restore and check its
size. Both lanes use the GitHub Actions cache service. The generation step is
recorded separately from save and restore.

The private qualification repository dispatches the reusable workflow once.
GitHub's Jobs API supplies job creation, start, completion, and phase timestamps.
Report queue and cache timings independently and keep failed jobs in the results.
The Boxduty pool starts with zero idle runners, with 2 vCPUs, 6 GiB RAM, and a
12 GiB workspace. The hosted lane uses the repository's `ubuntu-latest` runner.
