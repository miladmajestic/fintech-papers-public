# fintech-papers-public

Companion **public** repository that hosts the Tier-A / Tier-B / Tier-C source PDFs for the fintech.london editorial pipeline.

These PDFs are kept out of the main `fintech-london` repo so it stays under the 20 MB Lovable upload cap. The main repo references them via `scripts/fetch-pdfs.mjs`.

**Canonical GitHub URL:** `https://github.com/miladmajestic/fintech-papers-public.git`
**Raw base URL** (used by the fetcher): `https://raw.githubusercontent.com/miladmajestic/fintech-papers-public/main/`

---

## What goes here

This folder is the **scaffold** of that public repo, committed into the main repo as documentation + structure. The folders `tier-a/`, `tier-b/`, `tier-c/` are intentionally empty (`.gitkeep` only). The next person to take over the project should:

1. Create the public GitHub repo at the URL above (if it doesn't exist yet).
2. Copy the contents of *this* folder (`archive/sources/research-papers-public/`) into the root of that new repo.
3. Drop the actual PDFs into `tier-a/`, `tier-b/`, `tier-c/` of the **public repo** (not here).
4. Commit + push.

After that, anyone working on `fintech-london` can pull the PDFs on-demand into their local working copy by running:

```
node scripts/fetch-pdfs.mjs              # fetch every PDF listed in MANIFEST.md
node scripts/fetch-pdfs.mjs bis-tokenomics.pdf   # fetch a single file
```

Fetched PDFs land in `archive/sources/research-papers/tier-{a,b,c}/` in the main repo and are git-ignored, so they never bloat the upload.

---

## File naming

Match the filenames exactly as referenced by `archive/sources/research-papers/MANIFEST.md`. Example:

```
tier-a/01-blockspace-market.pdf
tier-a/02-defi-liquidity-pricing.pdf
tier-a/03-audit-layer.pdf
tier-b/bis-tokenomics.pdf
tier-b/bitcoin-treasury-guide.pdf
tier-b/openzeppelin-risk-assessment.pdf
tier-b/imf-consensus.pdf
tier-b/imf-tokenization-policy.pdf
tier-b/eu-quantum-finance.pdf
tier-b/stanford-code-and-law.pdf
…
```

The manifest in the main repo (`archive/sources/research-papers/MANIFEST.md`) is the single source of truth for which files should be present and which slots they feed.

---

## Why public

The PDFs are all already-public research artefacts (BIS, IMF, Stanford, EU, OpenZeppelin, etc.). There is no proprietary content here — making the repo public means the fetcher can use plain `https://raw.githubusercontent.com/...` with no auth tokens.

If a private source ever needs to land in the pipeline, it does **not** go in this repo. Add a private-tier protocol then.
