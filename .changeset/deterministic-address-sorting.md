---
"permissionless": patch
---

fix: use deterministic byte-wise address sorting instead of locale-dependent localeCompare. If you computed and funded a counterfactual Safe (ERC-7579) or Nexus address on a host with a da/nb/nn/no/fo/haw default locale, re-derive the address before sending further funds.
