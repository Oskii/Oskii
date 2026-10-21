<p align="center">
  <a href="https://hackerbane.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="./assets/banner-dark.svg">
      <source media="(prefers-color-scheme: light)" srcset="./assets/banner-light.svg">
      <img alt="Oscar Chambers (Oskii) — AI, Protocol & Software Security" src="./assets/banner-dark.svg" width="100%">
    </picture>
  </a>
</p>

<p align="center">
  <a href="https://hackerbane.com"><img src="https://img.shields.io/badge/Hackerbane-hackerbane.com-0f172a?style=flat-square&logo=securityscorecard&logoColor=38bdf8" alt="Hackerbane" /></a>
  <a href="https://hackerbane.com/reports"><img src="https://img.shields.io/badge/Public_Audit_Reports-12+_Published-059669?style=flat-square" alt="Public Audit Reports" /></a>
  <a href="https://www.linkedin.com/in/oscarchambers"><img src="https://img.shields.io/badge/LinkedIn-Oscar_Chambers-0a66c2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:oscar@hackerbane.com"><img src="https://img.shields.io/badge/Contact-oscar%40hackerbane.com-334155?style=flat-square&logo=protonmail&logoColor=white" alt="Email" /></a>
</p>

---

### Upstream Security Fixes & Advisories

Public security patches, vulnerability remediations, and advisories shipped to leading AI, cloud, and open-source codebases:

| Organization / Project | Vulnerability / Hardening Scope | Proof / Upstream Link |
| :--- | :--- | :--- |
| **AWS** (`awslabs/cli-agent-orchestrator`) | Enforce `cao:write` scope on PTY WebSocket, apply native deny flags on empty allowlists, and fail closed on unknown agent roles | [PR #748](https://github.com/awslabs/cli-agent-orchestrator/pull/748) · [PR #747](https://github.com/awslabs/cli-agent-orchestrator/pull/747) · [PR #746](https://github.com/awslabs/cli-agent-orchestrator/pull/746) |
| **Anthropic** (`buffa`, `claude-agent-sdk`, `anthropic-cli`) | Supply-chain SHA pinning for GitHub Actions & conformance images; S3/Redis session key aliasing & CLI path-confinement fixes | [buffa #479](https://github.com/anthropics/buffa/pull/479) · [sdk #478](https://github.com/anthropics/claude-agent-sdk-typescript/pull/478) · [cli #104](https://github.com/anthropics/anthropic-cli/pull/104) |
| **Google** (`google/adk-python`) | Sanitize `test_name` parameter across `GET`, `DELETE`, and `rebuild` routes to prevent path traversal | [PR #7034](https://github.com/google/adk-python/pull/7034) |
| **NVIDIA** (`NVIDIA/garak`) | Fix detection bypass in `PythonPypi` package-hallucination scanner for dotted and indented imports | [PR #2108](https://github.com/NVIDIA/garak/pull/2108) · [Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-nvidia-garak.html) |
| **Mistral AI** (`mistralai/mistral-common`) | Prevent unbounded worker hang on attacker-controlled image URLs by enforcing HTTP timeouts in `download_image` | [PR #308](https://github.com/mistralai/mistral-common/pull/308) · [Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-mistral-common-image-url.html) |
| **Baseten** (`basetenlabs/truss`) | Remediate `docker build` shell injection in `external_data` URL handling and enforce POSIX destination path confinement | [PR #2616](https://github.com/basetenlabs/truss/pull/2616) · [PR #2627](https://github.com/basetenlabs/truss/pull/2627) · [Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-baseten-truss.html) |
| **vLLM** (`vllm-project/vllm`) | Close validation bypass on the audio translation endpoint where string `file` fields skipped transcription checks | [PR #55618](https://github.com/vllm-project/vllm/pull/55618) · [Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-vllm-translation-file.html) |
| **Twenty CRM** (`twentyhq/twenty`) | Privilege escalation allowing workspace members with invite permissions to grant `Admin` roles | [GHSA-8w82-h3w4-62r5](https://github.com/twentyhq/twenty/security/advisories/GHSA-8w82-h3w4-62r5) |
| **Unicity AOS** (`unicity-aos/aos-ce`) | Prevent chained/multi-line shell check bypasses and swapped-path TOCTOU on channel transaction writes | [PR #256](https://github.com/unicity-aos/aos-ce/pull/256) · [PR #255](https://github.com/unicity-aos/aos-ce/pull/255) |
| **Karotte** (`preferencemodel/karotte`) | Bind container transcript WebSocket to `127.0.0.1` instead of all interfaces (`0.0.0.0`) | [PR #96](https://github.com/preferencemodel/karotte/pull/96) |
| **Boston Dynamics** (`boston-dynamics/spot-sdk`) | Confine exported robot link model paths to `outdir`, verify TLS certificates on BDDF downloads, and default NTRIP to TLS | [PR #169](https://github.com/boston-dynamics/spot-sdk/pull/169) · [PR #168](https://github.com/boston-dynamics/spot-sdk/pull/168) · [PR #167](https://github.com/boston-dynamics/spot-sdk/pull/167) |

---

### Selected Blockchain, Compiler & Protocol Audits

Full technical publications are available on **[hackerbane.com/reports](https://hackerbane.com/reports)**:

- **go-ethereum (`geth`) — EIP-7928 Block-Level Access Lists** — Identified state-transition ordering discrepancies where system calls execute prior to withdrawals at `n+1` and `Merge` retains stale writes across boundaries. [[Read Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-geth-eip-7928.html)]
- **reth — EIP-7928 Block-Level Access Lists** — Found consensus divergence accepting empty `7002`, `7251`, and `8282` predeploys rejected by EELS and `geth`. [[Read Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-reth-eip-7928.html)]
- **Bitcoin Core — BIP460 CISA (Cross-Input Signature Aggregation)** — Analyzed Witness v2 keypath aggregation (`PR #36122`), uncovering dummy half-agg member verification bypasses and PSBT merge collisions. [[Read Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-bip460-cisa.html)]
- **ZeroDev Bastion — EIP-7702 Session Wallet** — Uncovered factory budget refill bypass and cross-chain session replay via caller-supplied chain IDs. [[Read Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-zerodev-bastion.html)]
- **OKcontract (`oksolc`) — Solidity Compiler** — End-to-end compiler security assessment against `solc 0.8.36` across 25 findings (23 remediated). [[Read Report](https://hackerbane.com/reports/hackerbane-HACK-AR-2026-oksolc.html)]
- **Bitcoin Quantum (`btq-core`) — Post-Quantum Dilithium Consensus & PSBT** — Designed and implemented the `BTQ-PSBT` specification for CRYSTALS-Dilithium `P2MR` script paths, control-block validation, and cross-wallet signing. [[PR #99](https://github.com/btq-ag/btq-core/pull/99) · [PR #163](https://github.com/btq-ag/btq-core/pull/163) · [PR #169](https://github.com/btq-ag/btq-core/pull/169)]

---

### Focus Areas

```text
AI & Agent Security      LLM serving stacks, MCP/agent tool execution boundaries, container & sandbox escapes
Protocol & L1 Security   EVM execution clients (Go/Rust), Bitcoin consensus & PSBT, post-quantum cryptography
Smart Contracts & DeFi   Solidity, Rust (Solana/Anchor), compilers, cross-chain bridges, account abstraction (EIP-7702)
```
