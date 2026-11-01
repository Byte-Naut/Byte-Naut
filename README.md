# Systems correctness, fault diagnosis, and runtime engineering.

I work on correctness failures at stateful boundaries: resource ownership in runtimes, compiled-call ABIs, distributed query and control paths, and versioned artifact transfer. My recent work spans Wasmtime, WasmEdge, GreptimeDB, DuckDB, workerd, TestSprite, and CUDA.

Current focus: **WebAssembly runtimes**, especially resource ownership, trap-safe cleanup, and compiler ABI behavior across concurrent and compiled execution modes.

## Selected work

- **Wasmtime — Component Model resource lifecycle.** Five merged PRs add concurrent guest-resource destruction, fix synthetic-borrow conversion, protect fiber handoffs against trap and cancellation cleanup failures, document ownership transfer, and remove temporary white-box tests after validation. A related reader-cancellation API investigation was deferred pending a concrete use case. [#14362](https://github.com/bytecodealliance/wasmtime/pull/14362) · [#14384](https://github.com/bytecodealliance/wasmtime/pull/14384) · [#14434](https://github.com/bytecodealliance/wasmtime/pull/14434) · [#14620](https://github.com/bytecodealliance/wasmtime/pull/14620) · [#14681](https://github.com/bytecodealliance/wasmtime/pull/14681) · [Ownership case](https://github.com/Byte-Naut/systems-work/blob/main/cases/wasmtime-resource-lifecycle.md) · [Cleanup case](https://github.com/Byte-Naut/systems-work/blob/main/cases/wasmtime-traps-cancellation.md).
- **WasmEdge — LLVM lowering and compiled-call ABI.** Fixed a SIMD store representation cliff; an open follow-up passes multi-value results through caller-owned buffers so same-type `musttail` recursion remains constant-stack across AOT, JIT, and LazyJIT. [#5329](https://github.com/WasmEdge/WasmEdge/pull/5329), merged · [#5440](https://github.com/WasmEdge/WasmEdge/pull/5440), open · [Cases](https://github.com/Byte-Naut/systems-work#selected-cases).
- **GreptimeDB — query and cluster-control correctness.** Added session-aware SQLness regressions for query options and merge-scan plans, then changed distributed `SHOW PROCESSLIST` to return an error instead of a partial cluster view when a peer RPC fails. [#9956](https://github.com/GreptimeTeam/greptimedb/pull/9956) · [#9999](https://github.com/GreptimeTeam/greptimedb/pull/9999), merged October 26–28, 2026 · [Case](https://github.com/Byte-Naut/systems-work/blob/main/cases/greptimedb-query-control.md).
- **workerd — socket lifetime and garbage collection.** Traced a pending-close retention cycle across native captures, streams, and AsyncLocalStorage; proposed a fix with direct-socket and RPC regression tests. [#7258](https://github.com/cloudflare/workerd/pull/7258), open.
- **DuckDB — SQL correctness.** Fixed `BETWEEN` NULL handling in expression execution and statistics rewrites, with regression coverage for representation-dependent results. [#25394](https://github.com/duckdb/duckdb/pull/25394), merged September 10, 2026.
- **TestSprite CLI — versioned definition transfer.** Proposed deterministic export/import for backend test definitions with bounded reads, optimistic concurrency, staged idempotency, and atomic file output. [#417](https://github.com/TestSprite/testsprite-cli/pull/417), open · [Case](https://github.com/Byte-Naut/systems-work/blob/main/cases/testsprite-definition-transfer.md).
- **CUDA — Q/K per-head RMSNorm.** Recorded B200 result: SOL Score **0.577614**, Fast₁ **16/16**. [Public B200 leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/38/B200) · [Results](https://github.com/Byte-Naut/systems-work/blob/main/cases/sol-execbench-rmsnorm.md).

[Case studies and evidence](https://github.com/Byte-Naut/systems-work) include contribution boundaries, test records, and performance tradeoffs.

## Collaboration

I work through written specifications, reproducible tests, and asynchronous review. For a scoped systems task, send the repository, observed behavior, and acceptance criteria.

[Working together](https://github.com/Byte-Naut/systems-work/blob/main/WORKING_TOGETHER.md) · [Byte-Naut@proton.me](mailto:Byte-Naut@proton.me) · [2025llxe@gmail.com](mailto:2025llxe@gmail.com)

*Statuses checked November 1, 2026. Benchmark values describe a recorded result, not a live ranking.*
