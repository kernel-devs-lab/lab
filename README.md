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
├── hackaton/                               # Charlas y recursos estratégicos del Hackathon
│   ├── resumen/
│   │   ├── 01-product-ideation.md          # Cómo encontrar ideas reales y validarlas (Dev3pack)
│   │   └── 02-best-tips-hackathon.md       # Checklist ganador, errores eliminatorios y entrega
│   └── transcripciones/
│       ├── transcripcion_product_ideation.txt # Transcripción completa con marcas de tiempo
│       └── transcripcion_best_tips_hackathon.txt # Transcripción completa con marcas de tiempo
│
├── rust bootcamp/                          # Bootcamp oficial de Solana en Español
│   ├── resumen/
│   │   └── 01-rust-basics-solana.md        # Guía técnica, código y sintaxis de Rust para Solana
│   └── transcripciones/
│       └── transcripcion_rust_session_1.txt # Transcripción completa con marcas de tiempo
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

### 2. Preparación para el Hackathon (Dev3pack)
* 💡 **[Ideación de Producto: Cómo encontrar ideas reales](./hackaton/resumen/01-product-ideation.md):** Consejos de los organizadores, validación con proyectos de Colosseum y oportunidades para LATAM/Argentina.
* 🏆 **[Mejores Consejos para tu Primer Hackathon](./hackaton/resumen/02-best-tips-hackathon.md):** Errores eliminatorios, preparación previa (Devnet/wallets) y checklist de entrega.
* 📄 **[Transcripción - Product Ideation](./hackaton/transcripciones/transcripcion_product_ideation.txt):** Transcripción íntegra en inglés con timestamps.
* 📄 **[Transcripción - Best Tips for your First Hackathon](./hackaton/transcripciones/transcripcion_best_tips_hackathon.txt):** Transcripción íntegra en inglés con timestamps.

### 3. Bootcamp de Rust para Solana
* 📘 **[Resumen Técnico - Sesión 1](./rust%20bootcamp/resumen/01-rust-basics-solana.md):** Variables, mutabilidad, ownership, borrowing, `Option` y `Result`.
* 📄 **[Transcripción Completa - Sesión 1](./rust%20bootcamp/transcripciones/transcripcion_rust_session_1.txt):** Registro textual íntegro con timestamps de la clase.
