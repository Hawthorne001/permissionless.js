---
"permissionless": patch
---

Fixed published-package type-checking for consumers on legacy `moduleResolution: "node"` (node10): every exported subpath directory now ships a proxy package.json pointing at the compiled `_types`/`_esm`/`_cjs` output, so `tsc` resolves declarations instead of pulling raw `.ts` sources into the consumer's program (#522). Barrel subpath modules (`actions/{erc7579,pimlico,passkeyServer,etherspot,smartAccount}` and `clients/{pimlico,passkeyServer}`) moved from single files into directories with index files — package-specifier imports are unaffected, only private deep imports of `_esm`/`_cjs`/`_types` file paths change. Test files and vitest config are no longer included in the npm tarball; `.ts` sources are still shipped for debuggability. The codebase now compiles under `noUncheckedIndexedAccess`, so sources stay error-free even when consumer projects type-check them with that flag enabled.
