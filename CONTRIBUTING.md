# Contributing

This guide applies to every Stillproof Labs repository without its own. The
projects take part in the [Stellar Wave](https://www.drips.network/wave/stellar)
program; Wave issues are labeled with their complexity.

## Repositories and their checks

| Repository | Language | Before you push |
|---|---|---|
| [stillproof](https://github.com/stillproof-labs/stillproof) | Go 1.25+ | `gofmt -l .`, `go vet ./...`, `go test -race ./...`, `golangci-lint run` |
| [stillproof-anchor](https://github.com/stillproof-labs/stillproof-anchor) | Go 1.26+ | `gofmt -l .`, `go vet ./...`, `go test -race ./...`, `golangci-lint run` |
| [stillproof-app](https://github.com/stillproof-labs/stillproof-app) | Node 24, Expo SDK 58 | `npm test`, `npm run typecheck`, `npm run lint` |

`go.mod` and `package.json` pin the toolchains. CI runs the Go checks on Linux,
macOS and Windows, plus govulncheck. The core also builds the WebAssembly
verifier and checks embedded receipts with c2patool; the app builds an Android
APK and an iOS simulator build.

## Ground rules

- **Get assigned first.** Comment on the issue and wait for assignment. Pull
  requests for unassigned issues are closed.
- **One issue, one PR.** Link it with `Closes #N`.
- **The spec comes first.** A change to claims, receipts, the tree or the
  anchor transaction changes [SPEC.md](https://github.com/stillproof-labs/stillproof/blob/main/SPEC.md)
  in the same PR, and `testdata/vectors.json` if bytes change. The Go and
  TypeScript implementations must reproduce the vectors exactly.
- **Tests come with the change.** A verification change needs a test that would
  have failed without it.
- **Fail closed.** When a check can't be completed, the verdict says so. Never
  report a hardware level, a validator check or a step as passed unless it was
  checked.
- **Never claim more than the caveat.** A receipt proves a file is unchanged
  and when it existed, not that the scene is genuine. UI text, docs and
  verdicts keep to that.
- **Photos stay on the device.** Only hashes and signed claims leave it.
- **Keep the tree clean.** Don't commit notes, summaries, PR drafts, backup
  files or secrets.

## Design

The app and the web verifier follow
[DESIGN.md](https://github.com/stillproof-labs/stillproof/blob/main/docs/DESIGN.md):
the darkroom palette, Gloock, Schibsted Grotesk and Fragment Mono, the
fingerprint grid and the proof strip. UI changes include a screenshot in the PR.

## Commit messages

[Conventional Commits](https://www.conventionalcommits.org): `feat(receipt): …`,
`fix(store): …`, `docs: …`, `test: …`.
