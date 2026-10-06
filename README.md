# Systems correctness, fault diagnosis, and runtime engineering.

I work on failures where language semantics, runtime lifetimes, and low-level implementation choices interact. My recent work includes a connected series of merged resource-lifecycle contributions to Wasmtime, upstream fixes in DuckDB and WasmEdge, a garbage-collection fix proposed to workerd, and CUDA kernel optimization on NVIDIA B200.

Current focus: **WebAssembly runtimes**, particularly ownership across host/guest boundaries, resource lifetimes, and concurrent execution.

## Selected work

- **Wasmtime — resource ownership, borrowing, and concurrent destruction.** Three merged PRs build on one another: a concurrent guest-resource drop API establishes the execution path and regression; synthetic-borrow conversion refines the shared cleanup model; an official embedding example carries those rules forward and reuses the earlier resource tests. [#14362](https://github.com/bytecodealliance/wasmtime/pull/14362) → [#14384](https://github.com/bytecodealliance/wasmtime/pull/14384) → [#14434](https://github.com/bytecodealliance/wasmtime/pull/14434), merged September 22–29, 2026. [Delivery record](https://github.com/Byte-Naut/systems-work/blob/main/cases/wasmtime-resource-lifecycle.md).
- **WasmEdge — SIMD memory lowering.** Changed the LLVM representation behind a `v128.store` performance cliff, with trap checks and endian-path validation. [PR #5329](https://github.com/WasmEdge/WasmEdge/pull/5329), merged September 14, 2026.
- **workerd — socket lifetime and garbage collection.** Traced a pending-close retention cycle across native captures, streams, and AsyncLocalStorage; proposed a fix with direct-socket and RPC regression tests. [PR #7258](https://github.com/cloudflare/workerd/pull/7258), open.
- **DuckDB — SQL correctness.** Fixed `BETWEEN` NULL handling in expression execution and statistics rewrites, with regression coverage for representation-dependent results. [PR #25394](https://github.com/duckdb/duckdb/pull/25394), merged September 10, 2026.
- **CUDA — Q/K per-head RMSNorm.** Recorded B200 result: SOL Score **0.577614**, Fast₁ **16/16**. [Public B200 leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/38/B200) · [Results](https://github.com/Byte-Naut/systems-work/blob/main/cases/sol-execbench-rmsnorm.md).

[Case studies and evidence](https://github.com/Byte-Naut/systems-work) include contribution boundaries, test records, and performance tradeoffs.

## Collaboration

I work through written specifications, reproducible tests, and asynchronous review. For a scoped systems task, send the repository, observed behavior, and acceptance criteria.

[Working together](https://github.com/Byte-Naut/systems-work/blob/main/WORKING_TOGETHER.md) · [Byte-Naut@proton.me](mailto:Byte-Naut@proton.me) . [2025llxe@gmail.com](2025llxe@gmail.com)

*Wasmtime series checked October 4, 2026; other upstream statuses recorded September 18, 2026. Benchmark values describe a recorded result, not a live ranking.*
