<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/stillproof-labs/.github/main/assets/wordmark.svg">
    <img src="https://raw.githubusercontent.com/stillproof-labs/.github/main/assets/wordmark-print.svg" alt="Stillproof" height="64">
  </picture>
</p>

<p align="center"><b>Prove a photo is unedited, and when it was taken.</b></p>

<p align="center"><a href="https://stillproof-labs.github.io/stillproof/"><b>Check a photo in your browser →</b></a></p>

Stillproof doesn't guess whether a photo looks real. The phone signs the
photo's SHA-256 the moment it is taken, with a key held in its secure hardware.
An anchoring service batches those signatures into a Merkle tree and records
the root on Stellar. Anyone can then check the file, with no account and no
trust in us: the signature, the tree, and the anchor, confirmed by the Stellar
validators' own signatures through
[Externalize](https://github.com/Externalize-Labs/externalize).

| Repository | Language | What it does |
|---|---|---|
| [stillproof](https://github.com/stillproof-labs/stillproof) | Go | The protocol ([SPEC.md](https://github.com/stillproof-labs/stillproof/blob/main/SPEC.md)), test vectors, the `stillproof` CLI, attestation checks, C2PA embedding, and the browser verifier |
| [stillproof-anchor](https://github.com/stillproof-labs/stillproof-anchor) | Go | The anchoring service: takes signed claims, anchors Merkle roots on Stellar, serves receipts and lookups by photo hash |
| [stillproof-app](https://github.com/stillproof-labs/stillproof-app) | TypeScript, React Native | The capture app for Android and iOS: signs at capture with a hardware key, keeps receipts, checks any photo |

**What a receipt proves:** the file is unchanged since a given key signed it,
and it existed no later than a given Stellar ledger closed. It does not prove
the scene is genuine, and every verdict says so.

**Contributing:** we take part in the
[Stellar Wave](https://www.drips.network/wave/stellar) program; issues are
labeled by complexity. Read [CONTRIBUTING](https://github.com/stillproof-labs/.github/blob/main/CONTRIBUTING.md)
first, and report security issues privately as described in
[SECURITY](https://github.com/stillproof-labs/.github/blob/main/SECURITY.md).
