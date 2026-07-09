---
"@permissionless/wagmi": patch
---

Fixed `useAvailableCapabilities` to return `undefined` instead of throwing when the connected chain has no capabilities entry, and hardened receipt handling in `useWaitForTransactionReceipt`. The package now compiles under `noUncheckedIndexedAccess`.
