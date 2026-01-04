# CHANGELOG - Zyb Multi-Repo
**Período:** 2025-12-29 → 2026-01-04
**Generado:** 2026-01-04

---

## RESUMEN EJECUTIVO

### Estadísticas Generales
- **9 repositorios** configurados y funcionales
- **~50+ commits** entre todos los repos
- **~8,000+ líneas de código** nuevas/modificadas
- **~2,000+ líneas de documentación** generadas
- **5 sesiones principales** de desarrollo documentadas

### Repos Afectados
| Repo | Estado | Cambios Principales |
|------|--------|---------------------|
| zyb-apps | FUNCIONAL | Migración Bun, App Shell, auto-refresh |
| zyb-sdks | FUNCIONAL | identity-sdk completo, fhe-client integrado |
| zyb-platform | FUNCIONAL | GitBook, docker-compose ZK |
| zyb-cli | FUNCIONAL | ZK proofs E2E, demo mejorado, config TOML |
| zyb-kernel | FUNCIONAL | CircuitType::Groth16 |
| zyb-chain | FUNCIONAL | Workspace reestructurado, Unified SDK |
| zyb-compute | FUNCIONAL | SnarkjsProver, Groth16 support |
| zyb-services | FUNCIONAL | Prover auth fix |
| zyb-circuits | FUNCIONAL | Test E2E scripts |

---

## CHANGELOG POR REPOSITORIO

### zyb-apps

#### v0.4.0 (2026-01-04)
**Breaking Changes:**
- Migración de npm a Bun como package manager

**Features:**
- `83437b2` - refactor(webapp): remove Buffer polyfills and upgrade to @solana/kit v5
- `75da0ea` - feat(webapp): implement App Shell architecture with layouts
- `1ad1e02` - chore: migrate package manager from npm to Bun
- `245f4ff` - feat(webapp): add auto-refresh capability to futarchy markets list (30s)

**Refactoring:**
- `8159550` - refactor: consolidar estructura aplanada del repositorio
- `5c81401` - refactor: consolidar estructura tras migracion Phase 5
- `8b9b316` - refactor: Phase 5 - Infrastructure migration and modularization
- `1d9c147` - refactor: normalizar nombre de directorio sdks/ a sdk/
- `9f5e3bd` - refactor: migrate verticals to domain-driven structure

**Documentation:**
- `3e9a801` - docs: README profesional con arquitectura y ejemplos

**TypeScript SDK:**
- Stripe-like APIs implementadas
- `compliance.ts`: screen(), screenBatch()
- `webhooks.ts`: WebhookClient con HMAC verification
- `react/hooks.ts`: useZyber, useCompliance, useFheOperation, useZkProof

---

### zyb-sdks

#### v0.3.0 (2026-01-04)
**Features:**
- `5677ea0` - feat(identity-sdk): complete prove_innocence and verify implementations
- `a2f9a28` - refactor: integrar fhe-client en workspace principal
- `7a85d99` - client added (FHE client SDK)

**New SDKs:**
- **identity-sdk (Rust):** ComplianceClient, BlacklistManager, Merkle trees, 16 tests
- **defi-sdk (Rust):** DeFiClient, prove_portfolio, prove_liquidity, 8 tests
- **governance-sdk:** Renombrado y funcional

**Refactoring:**
- `f74477d` - refactor: consolidar estructura aplanada del repositorio
- `3d44890` - fix: corregir paths rotos en sdk/ y preservar directorios vacios
- `647dcb2` - refactor: migrate verticals to domain-driven structure

**Documentation:**
- `306fba4` - docs: README profesional con arquitectura y ejemplos

---

### zyb-platform

#### v0.5.0 (2026-01-04)
**Features:**
- `87c79db` - docs: integración GitBook y actualización URLs repositorios
- `e3475b5` - Add minimal docker-compose for ZK backend testing
- `201e5a3` - feat(cli): add visual demo command for presentations
- `f1c0822` - feat(cli): add job status and history tracking to dev-job

**Fixes:**
- `eeb2b16` - fix(blink-server): correct prover authentication query (authority_pubkey)

**Refactoring:**
- `053adaf` - refactor: consolidar estructura aplanada del repositorio

**Documentation:**
- `2ed5f46` - docs: README profesional con arquitectura y ejemplos

**Cleanup:**
- `d9ac13d` - workflows don't make sense anymore
- `1e04881` - Delete .github/workflows/release-fhe-cli.yml

---

### zyb-cli

#### v0.6.0 (2026-01-04)
**Features:**
- `0eb0f3b` - feat(cli): integración completa CLI-Backend para ZK proofs
- `28f3980` - feat(cli): improve DX with examples, error hints, and compliance wizard
- `d0472a0` - feat(cli): enhance demo mode with recording and narration options
- `bda6bd5` - feat(cli): add visual demo command for presentations
- `363a923` - feat(cli): add job status and history tracking to dev-job
- `6ed4202` - feat(cli): add unified TOML config system with profiles

**New Commands:**
- `zyb compliance prove --local --verify` - Genera proofs con rapidsnark/snarkjs
- `zyb compliance verify-onchain` - Verificación on-chain (planned)
- `zyb dev-job status --job-id X` - Ver estado de job
- `zyb dev-job history` - Historial de jobs
- `zyb demo poi-zk` - Demo ZK completo

**New Modules:**
- `src/snarkjs.rs` - Wrapper rapidsnark/snarkjs
- Sistema de configuración TOML con `--profile local`

**Fixes:**
- `2bf2000` - fix: corregir paths de dependencias para estructura multi-repo
- `35dacdd` - fix: corregir paths y referencias tras migracion programs/ a chain/solana/programs/

**Refactoring:**
- `bf81cd3` - refactor: consolidar estructura aplanada del repositorio

**Documentation:**
- `7186a96` - docs: README profesional con arquitectura y ejemplos

---

### zyb-kernel

#### v0.2.0 (2026-01-03)
**Features:**
- Nuevo `CircuitType::Groth16(u8)` para soporte ZK proofs

**Files Changed:**
- `types/src/circuit.rs` - Nuevo variant Groth16

---

### zyb-chain

#### v0.4.0 (2026-01-03)
**Features:**
- Workspace reestructurado
- Unified SDK Phases 2-5 completadas (~3,500 LOC)

**Unified SDK Components:**
- Phase 2: bedrock, zk, fhe, futarchy wrappers
- Phase 3: ZyberUnified client
- Phase 4: JobListener, JobClaimer, ProverRegistry
- Phase 5: crypto, retry, config utils

**Program Changes:**
- `solana/programs/zyberlink/src/processor/create_job.rs` - Groth16 match
- `solana/programs/zyberlink/src/processor/create_job_with_token.rs` - Groth16 match

---

### zyb-compute

#### v0.3.0 (2026-01-03)
**Features:**
- Soporte Groth16 en job_processor
- `src/core/snarkjs.rs` - SnarkjsProver nuevo

**New Functions:**
- `generate_groth16_proof()` - Genera proofs con rapidsnark
- `submit_groth16_proof_to_backend()` - POST a /internal/zk/{job_id}/submit-proof
- `with_circuits_base()`, `with_backend_url()` - Builder pattern

---

### zyb-services

#### v0.2.0 (2025-12-31)
**Fixes:**
- Fix prover auth: query por `authority_pubkey` en lugar de `pubkey`

**Features:**
- Endpoint `/api/futarchy/stats` en blink-server + public-api

---

### zyb-circuits

#### v0.2.0 (2026-01-03)
**Features:**
- `poi/test_e2e_cli.sh` - Script de test E2E

---

## CHANGELOG POR SESIÓN

### Sesión 2025-12-29
**Rama:** obsidian
**Objetivos cumplidos:**
- Witness Download implementado (Estrategia 1)
- Verificación de arquitectura FHE
- Programas Solana compilados (fhe_generator.so, bedrock.so)
- docker-compose.yml actualizado con Program IDs
- Fixes: `circuit_type_from_u8`, histogram bins uniformes

**Archivos clave:**
- services/public-api/src/clients/blink_client.rs
- services/public-api/src/handlers/gateway.rs
- prover/core/src/witness_fetcher.rs
- nginx.conf

---

### Sesión 2025-12-30
**Rama:** obsidian
**Objetivos cumplidos:**
- Sistema TOML config implementado (`zyb.toml`)
- Comandos migrados: dev-job, vote, market usan `--profile local`
- Endpoint /api/futarchy/stats
- Auto-refresh 30s en FutarchyMarketList.svelte
- 9 commits realizados

---

### Sesión 2025-12-31
**Rama:** obsidian
**Objetivos cumplidos:**
- Migración multi-repo completa (9 repos extraídos)
- Fix prover auth (authority_pubkey)
- Comandos status/history en CLI
- Tracking automático en .zyb-jobs.json
- SDK completion: identity-sdk, defi-sdk, Unified SDK phases 2-5
- Housekeeping: .gitignore y LICENSE en 8 repos
- TS SDK high-level APIs (compliance.ts, webhooks.ts, hooks)

**Métricas:**
- ~6,000+ líneas Rust nuevas
- ~1,500+ líneas TypeScript nuevas
- 56 tests nuevos
- 25+ commits

---

### Sesión 2026-01-02
**Rama:** (extracted3)
**Objetivos cumplidos:**
- Extracción limpia de 9 repos desde base2
- Análisis de gaps con strategic-planner
- Documentación en extracted3/private/

---

### Sesión 2026-01-03
**Rama:** (extracted3)
**Objetivos cumplidos:**
- CLI genera proofs reales con rapidsnark/snarkjs
- Prover → Backend verification
- CircuitType::Groth16 en kernel
- SnarkjsProver en zyb-compute
- Test E2E scripts

**Cambio técnico importante:**
- Rapidsnark como prover preferido (~10x más rápido que snarkjs)


---

## FEATURES PRINCIPALES IMPLEMENTADAS

### 1. Sistema de Configuración TOML
```toml
# zyb.toml
[profiles.local]
rpc_url = "http://localhost:8899"
backend_url = "http://localhost:9000"
program_id = "..."
```
**Uso:** `zyb dev-job run --profile local`

### 2. ZK Proofs End-to-End
- Generación local con rapidsnark/snarkjs
- Verificación local
- Submit al backend
- Flags: `--local`, `--verify`, `--circuits-dir`

### 3. Identity SDK (Rust)
```rust
let client = ComplianceClient::new(blacklist_merkle_root);
let proof = client.prove_innocence(&portfolio)?;
let valid = client.verify_innocence(&proof)?;
```

### 4. TypeScript SDK Stripe-like
```typescript
const result = await compliance.screen({
  addresses: ["0x..."],
  proofTypes: ["poi"]
});

const hook = useCompliance({ address });
```

### 5. Auto-refresh UI
- FutarchyMarketList con refresh cada 30s
- Tracking de jobs en `.zyb-jobs.json`

### 6. Demo Mode Mejorado
```bash
zyb demo poi-zk --quick
zyb demo poi-zk --record
zyb demo poi-zk --narrate
```

---

## ARQUITECTURA FINAL

```
extracted3/
├── zyb-kernel/      # Types, FHE primitives (base)
├── zyb-chain/       # Solana programs, SDK, chain-client
├── zyb-circuits/    # Circom circuits (poi, vote, market)
├── zyb-sdks/        # Vertical SDKs (identity, defi, governance)
├── zyb-services/    # Backend services (blink, public-api)
├── zyb-compute/     # Prover node
├── zyb-cli/         # CLI tool
├── zyb-apps/        # Web apps (webapp, wallet-extension)
├── zyb-platform/    # Docs, config, infra
└── private/         # Documentación interna (no trackeada)
```

---

## PRÓXIMOS PASOS (Phase 3)

1. **On-Chain Verification** (Days 1-4)
   - Smart contract Groth16 verifier
   - Deploy a Solana devnet
   - CLI integration

2. **Demo Video** (Days 5-6)
   - 60s video para Twitter
   - Screen recording E2E
   - Post-production

3. **Public Launch** (Day 7)
   - README profesional
   - Twitter thread
   - Launch assets

---

## NOTAS TÉCNICAS

### Dependencias Entre Repos
```
zyb-kernel ← zyb-chain ← zyb-compute
                      ← zyb-cli
                      ← zyb-services
zyb-sdks ← zyb-services
         ← zyb-compute
zyb-apps (independiente - frontend)
zyb-circuits (independiente - circom)
```

### Comandos de Compilación
```bash
# Kernel
cd zyb-kernel && cargo check

# Chain
cd zyb-chain && cargo check

# CLI
cd zyb-cli && cargo build --release

# Services
cd zyb-services && SQLX_OFFLINE=true cargo check

# Apps
cd zyb-apps && bun install && bun run build
```

### Program IDs (Devnet)
- FHE_GENERATOR: `GkYw9vNT6EZFZTwoEM2UBuwsAD6nwzArLGghBZqpsF5L`
- BEDROCK: `8oSWVqrU78YW3FH6BqrqJqRyqK4p6k5ikzbT7UyekJrH`
- ZK_GENERATOR: `3MBUZ4Gy5g8FJSKjBJVKixr5vFZZXgFqd9tqhwmMWNPv`

---
