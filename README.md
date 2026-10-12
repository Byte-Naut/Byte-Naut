# Systems correctness, fault diagnosis, and runtime engineering.

I work on failures where language semantics, runtime lifetimes, and low-level implementation choices interact. My recent work includes two connected resource-lifecycle series in Wasmtime, upstream fixes in DuckDB and WasmEdge, a garbage-collection fix proposed to workerd, and CUDA kernel optimization on NVIDIA B200.

Current focus: **WebAssembly runtimes**, particularly ownership across host/guest boundaries, trap-safe cleanup, cancellation, and concurrent execution.

## Selected work

- **Wasmtime — cleanup across concurrency, traps, and cancellation.** Starting from concurrent `ResourceAny` destruction, I audited fiber handoffs that could turn traps or internal errors into process aborts. After two design experiments, the merged repair preserves the scheduler representation while guarding ownership-transfer intervals, including cancellation before a future's first poll; fault-injection tests reproduce the abort paths on unpatched builds. A follow-on analysis of reader cancellation separated ownership-return and API-semantics questions and was deferred upstream until a concrete use case constrains the design. [#14362](https://github.com/bytecodealliance/wasmtime/pull/14362) → [#14620](https://github.com/bytecodealliance/wasmtime/pull/14620) · [#12090](https://github.com/bytecodealliance/wasmtime/issues/12090) · [Delivery record](https://github.com/Byte-Naut/systems-work/blob/main/cases/wasmtime-traps-cancellation.md).
- **Wasmtime — resource ownership, borrowing, and embedding.** A concurrent guest-resource drop API establishes the execution path; synthetic-borrow conversion refines which resources carry cleanup state; the official embedding example then documents borrowing, explicit destruction, and ownership transfer while reusing the earlier resource tests. [#14362](https://github.com/bytecodealliance/wasmtime/pull/14362) → [#14384](https://github.com/bytecodealliance/wasmtime/pull/14384) → [#14434](https://github.com/bytecodealliance/wasmtime/pull/14434), merged September 22–29, 2026. [Delivery record](https://github.com/Byte-Naut/systems-work/blob/main/cases/wasmtime-resource-lifecycle.md).
- **WasmEdge — SIMD memory lowering.** Changed the LLVM representation behind a `v128.store` performance cliff, with trap checks and endian-path validation. [PR #5329](https://github.com/WasmEdge/WasmEdge/pull/5329), merged September 14, 2026.
- **workerd — socket lifetime and garbage collection.** Traced a pending-close retention cycle across native captures, streams, and AsyncLocalStorage; proposed a fix with direct-socket and RPC regression tests. [PR #7258](https://github.com/cloudflare/workerd/pull/7258), open.
- **DuckDB — SQL correctness.** Fixed `BETWEEN` NULL handling in expression execution and statistics rewrites, with regression coverage for representation-dependent results. [PR #25394](https://github.com/duckdb/duckdb/pull/25394), merged September 10, 2026.
- **CUDA — Q/K per-head RMSNorm.** Recorded B200 result: SOL Score **0.577614**, Fast₁ **16/16**. [Public B200 leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/38/B200) · [Results](https://github.com/Byte-Naut/systems-work/blob/main/cases/sol-execbench-rmsnorm.md).

[Case studies and evidence](https://github.com/Byte-Naut/systems-work) include contribution boundaries, test records, and performance tradeoffs.

## Collaboration

I work through written specifications, reproducible tests, and asynchronous review. For a scoped systems task, send the repository, observed behavior, and acceptance criteria.

[Working together](https://github.com/Byte-Naut/systems-work/blob/main/WORKING_TOGETHER.md) · [Byte-Naut@proton.me](mailto:Byte-Naut@proton.me) · [2025llxe@gmail.com](mailto:2025llxe@gmail.com)

*Wasmtime statuses checked October 12, 2026; other upstream statuses recorded September 18, 2026. Benchmark values describe a recorded result, not a live ranking.*
