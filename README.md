# 🔬 Kernel Devs Lab

Laboratorio personal de investigación y experimentación sobre **Rust, Solana, Web3, blockchain y sistemas distribuidos** para el **Build Station Jujuy (Dev3pack Global Hackathon)** en la Facultad de Ingeniería (UNJu).

---

## 📁 Estructura del Repositorio

```text
lab/
├── conceptos/                              # Fundamentos teóricos y arquitectura Web3
│   ├── 01-evolucion-web-1-2-3.md           # Evolución Web 1.0, 2.0 y 3.0 (Comparativa REST/Cloud)
│   ├── 02-que-es-blockchain.md             # Arquitectura distribuida, hashes, consenso y ledger
│   ├── 03-solana-y-arquitectura.md         # Red, validadores, PoH, Sealevel y modelo de cuentas
│   └── 04-por-que-rust.md                  # Rol de Rust, SBF, ausencia de GC y Framework Anchor
│
├── rust bootcamp/                          # Rust Bootcamp (Dev3pack x Solana)
│   ├── resumen/
│   │   ├── 01-rust-basics-solana.md        # Sesión 1: Variables, ownership, Option/Result
│   │   ├── 02-rust-basics-solana.md        # Sesión 2: Rust Basics #2
│   │   ├── 03-infraestructura-solana-y-cli.md # Sesión 3: Blockchain, RPCs, CLI y cuentas
│   │   ├── 04-wallets-seguridad-y-multisig.md # Sesión 4: Wallets, custodia, firmas y Squads
│   │   ├── 05-arquitectura-cuentas-pdas-transacciones.md # Sesión 5: Cuentas, Renta, PDAs y Tx
│   │   ├── 06-solana-kit-typescript.md     # Sesión 6: Solana Kit (TS), RPC, WS y pipe
│   │   ├── 07-anchor-intro-y-testing.md    # Sesión 7: Anchor, proyecto counter, tests y Devnet
│   │   ├── 08-deploy-maquinas-estado-y-seguridad.md # Sesión 8: Máquinas de estado, aritmética y seguridad
│   │   ├── 09-deploy-playground-cli-e-idl.md # Sesión 9: Deploy (Playground/CLI), IDL y upgrades
│   │   ├── 10-product-ideation.md          # Sesión 10: Product Ideation: how to find real ideas
│   │   ├── 11-vibecode-solana.md           # Sesión 11: Vibecode your first app on Solana
│   │   ├── 12-x402-micropagos-solana.md    # Sesión 12: Enable micro-payments with x402 on Solana
│   │   └── 13-best-tips-hackathon.md       # Sesión 13: Best tips for your first hackathon
│   └── transcripciones/
│       └── transcripcion_rust_session_1..13.txt
│
├── .gitignore
└── README.md
```

---

## 📚 Módulos de Investigación

### 1. Conceptos Fundamentales de Web 3.0 y Solana
* 🌐 **[Evolución de la Web (Web 1.0, 2.0 y 3.0)](./conceptos/01-evolucion-web-1-2-3.md):** Diferencias arquitectónicas entre clientes/servidores tradicionales (APIs REST, PostgreSQL, AWS) y el paradigma descentralizado.
* ⛓️ **[¿Qué es una Blockchain?](./conceptos/02-que-es-blockchain.md):** El ledger inmutable, criptografía de clave pública/privada y mecanismos de consenso.
* ⚡ **[¿Qué es Solana y cómo funciona su arquitectura?](./conceptos/03-solana-y-arquitectura.md):** Proof of History (PoH), procesamiento paralelo Sealevel, y el modelo de cuentas (Accounts Model).
* 🦀 **[¿Por qué Rust en Solana?](./conceptos/04-por-que-rust.md):** Ausencia de Garbage Collector, seguridad de memoria a costo cero y el framework Anchor.

### 2. Bootcamp de Rust y Solana (Dev3pack — Sesiones 1 a 13)
* 📘 **[Sesión 1 - Rust Basics #1](./rust%20bootcamp/resumen/01-rust-basics-solana.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_1.txt))
* 📘 **[Sesión 2 - Rust Basics #2](./rust%20bootcamp/resumen/02-rust-basics-solana.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_2.txt))
* 🌐 **[Sesión 3 - Blockchain, Infraestructura y Solana CLI](./rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_3.txt))
* 🔐 **[Sesión 4 - Wallets, Custodia, Seguridad y Multisig](./rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_4.txt))
* 🧱 **[Sesión 5 - Arquitectura de Cuentas, PDAs y Transacciones](./rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_5.txt))
* 💻 **[Sesión 6 - Solana Kit en TypeScript](./rust%20bootcamp/resumen/06-solana-kit-typescript.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_6.txt))
* ⚓ **[Sesión 7 - Introducción a Anchor y Testing](./rust%20bootcamp/resumen/07-anchor-intro-y-testing.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_7.txt))
* 🛡️ **[Sesión 8 - Máquinas de Estado, Aritmética Segura y Seguridad](./rust%20bootcamp/resumen/08-deploy-maquinas-estado-y-seguridad.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_8.txt))
* 🚀 **[Sesión 9 - Deploy (Playground/CLI), IDL y Upgrades](./rust%20bootcamp/resumen/09-deploy-playground-cli-e-idl.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_9.txt))
* 💡 **[Sesión 10 - Product Ideation](./rust%20bootcamp/resumen/10-product-ideation.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_10.txt))
* 🤖 **[Sesión 11 - Vibecode your first app on Solana](./rust%20bootcamp/resumen/11-vibecode-solana.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_11.txt))
* ⚡ **[Sesión 12 - Micro-payments with x402 on Solana](./rust%20bootcamp/resumen/12-x402-micropagos-solana.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_12.txt))
* 🏆 **[Sesión 13 - Best tips for your first hackathon](./rust%20bootcamp/resumen/13-best-tips-hackathon.md)** ([Transcripción](./rust%20bootcamp/transcripciones/transcripcion_rust_session_13.txt))
