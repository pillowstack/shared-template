## GitHub Packages Setup

This package publishes to GitHub Packages. Configure the following before publishing or CI runs:

- Required repository secrets:
  - `PKG_GH_READ`: A fine-grained or classic token with `read:packages` permission (used by CI to install).
  - `PKG_GH_WRITE`: A token with `write:packages` permission (used by the publish workflow).

### 1) Create tokens

- Navigate to GitHub → Settings → Developer settings → Personal access tokens.
- Create two tokens (or reuse one with both permissions):
  - `read:packages` for `PKG_GH_READ`.
  - `write:packages` (and `read:packages`) for `PKG_GH_WRITE`.

For organizations, prefer a fine-grained PAT scoped to this repo with the above permissions.

### 2) Add repository secrets

- Go to your repo → Settings → Secrets and variables → Actions → New repository secret.
- Add `PKG_GH_READ` and `PKG_GH_WRITE` with the corresponding tokens.

### 3) .npmrc configuration

This repo includes `.npmrc` configured for GitHub Packages. CI sets `NODE_AUTH_TOKEN` so npm can authenticate.

Locally, you can set (temporary shell env):

```bash
export NODE_AUTH_TOKEN=ghp_yourTokenHere
```

Or configure a user-level `.npmrc` entry:

```
//npm.pkg.github.com/:_authToken=ghp_yourTokenHere
@pillowstack:registry=https://npm.pkg.github.com/
```

### 4) Publishing flow

1. Update `package.json` version (SemVer).
2. Push a tag `vX.Y.Z` on `main`.
3. The `Publish Package` workflow publishes using `PKG_GH_WRITE`.

See README “Publishing” for details.
