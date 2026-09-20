# Upstream synchronization strategy

The forks keep KDE upstream history intact while isolating product work on `develop`.

## Remotes

For a development checkout:

- `origin`: `ShadowUR0/kdeconnect-android` or `ShadowUR0/kdeconnect-kde`
- `upstream`: the corresponding `KDE/` repository

## Branch roles

- `master`: clean upstream-tracking branch. Do not add product commits here.
- `develop`: integration branch for this project.
- short-lived feature/fix branches may branch from `develop` when useful.

## Updating from KDE

1. Fetch `upstream`.
2. Fast-forward fork `master` to `upstream/master` when there are no fork-only commits.
3. Merge updated `master` into `develop` with normal history-preserving merges.
4. Do not force-push or rewrite shared history.
5. For an urgent isolated upstream security/protocol fix, cherry-pick only when a full upstream merge is inappropriate and record the original upstream commit SHA.

## Principles

- Preserve KDE copyright and license notices.
- Keep protocol/core changes reviewable and separate from product UI work.
- Prefer upstream fixes when they apply cleanly.
- Resolve product divergence on `develop`, never by editing or rebasing published `master`.
