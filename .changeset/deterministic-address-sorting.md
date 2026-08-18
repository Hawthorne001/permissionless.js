---
"permissionless": minor
---

BREAKING: use deterministic byte-wise address sorting instead of locale-dependent localeCompare when sorting ERC-7579 attesters. On hosts with a da/nb/nn/no/fo/haw default locale and 2+ attesters configured, `toSafeSmartAccount` (ERC-7579) and `toNexusSmartAccount` now derive a different counterfactual address. The previously derived address was never deployable — the attester registry requires ascending byte order, so any funds already sent to it were unrecoverable before this release. Re-derive your address after upgrading and only fund the new one. Hosts on other locales are unaffected (byte-identical output). Also exports the new `sortAddresses` utility.
