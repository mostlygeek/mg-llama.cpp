This fork is maintained for llama-swap's unified container.

It tracks [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp) and keeps `master` rebased on top of
upstream `master`. For llama.cpp usage, build and backend docs, see the upstream repository.

## Fork changes

- `server`: report model loading progress in `/health` and `/v1/health`. While the model is still loading,
  these endpoints return `progress` (0.0-1.0) and a human readable `message` for the current loading stage.
  Works in both standalone and router modes. See ggml-org/llama.cpp#24822
- CI: `rebase-upstream-llama-cpp` workflow rebases `master` onto upstream `master` every 6 hours, and on
  demand. It force-pushes with `--force-with-lease`, so local clones must `git fetch` then
  `git reset --hard origin/master` after each run
