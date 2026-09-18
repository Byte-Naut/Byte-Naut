# Byte-Naut

Systems correctness, fault diagnosis, and runtime engineering.

I work on failures where language semantics, runtime lifetimes, and low-level implementation choices interact. My recent work includes upstream fixes in DuckDB and WasmEdge, a garbage-collection fix proposed to workerd, and CUDA kernel optimization on NVIDIA B200.

Current focus: **WebAssembly runtimes**, particularly memory semantics, resource lifetimes, and host integration.

## Selected work

- **WasmEdge — SIMD memory lowering.** Changed the LLVM representation behind a `v128.store` performance cliff, with trap checks and endian-path validation. [PR #5329](https://github.com/WasmEdge/WasmEdge/pull/5329), merged September 14, 2026.
- **workerd — socket lifetime and garbage collection.** Traced a pending-close retention cycle across native captures, streams, and AsyncLocalStorage; proposed a fix with direct-socket and RPC regression tests. [PR #7258](https://github.com/cloudflare/workerd/pull/7258), open.
- **DuckDB — SQL correctness.** Fixed `BETWEEN` NULL handling in expression execution and statistics rewrites, with regression coverage for representation-dependent results. [PR #25394](https://github.com/duckdb/duckdb/pull/25394), merged September 10, 2026.
- **CUDA — Q/K per-head RMSNorm.** Recorded B200 result: SOL Score **0.577614**, Fast₁ **16/16**. [Kernel #38](https://research.nvidia.com/benchmarks/sol-execbench/kernel/38) · [Result scope](https://github.com/Byte-Naut/systems-work/blob/main/cases/sol-execbench-rmsnorm.md).

[Case studies and evidence](https://github.com/Byte-Naut/systems-work) include contribution boundaries, test records, and performance tradeoffs.

## Collaboration

I work through written specifications, reproducible tests, and asynchronous review. For a scoped systems task, send the repository, observed behavior, and acceptance criteria.

[Working together](https://github.com/Byte-Naut/systems-work/blob/main/WORKING_TOGETHER.md) · [Byte-Naut@proton.me](mailto:Byte-Naut@proton.me)

*Upstream PR statuses checked September 18, 2026. Benchmark values describe a recorded result, not a live ranking.*
