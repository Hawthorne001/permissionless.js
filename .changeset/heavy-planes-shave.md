---
"permissionless": patch
---

Fixed extreme TypeScript type-checking slowness (~80s per call site, issue #500) when a client created by `createSmartAccountClient`, `createPimlicoClient`, or `createPasskeyServerClient` is checked against the bare `SmartAccountClient` / `PimlicoClient` / `PasskeyServerClient` alias (e.g. `useQuery<SmartAccountClient>`). The client type aliases now use an inline mapped-type body with variance annotations (the same pattern viem ships in `SimulateContractReturnType`, wevm/viem#2557) so TypeScript compares instantiations argument-by-argument instead of expanding the full action surface structurally. Return-type precision is unchanged.
