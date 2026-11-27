# 📝 Quiz 01: Arquitectura y Wallets

Cuestionario de evaluación del **Rust Bootcamp (Dev3pack x Solana)** con la justificación de cada opción y su referencia directa a los resúmenes del laboratorio.

---

## 1. ¿Qué guarda realmente una wallet?

* **Tus SOL y tokens** ❌  
  Los fondos nunca viven dentro de la app de tu celular o navegador; siempre residen en el *ledger* de la blockchain (dentro de las cuentas de Solana).
* **Tus llaves** ✅ *(Correcta)*  
  Una wallet únicamente almacena y gestiona tus pares de llaves criptográficas (clave pública y privada) para firmar operaciones.  
  🔗 **Referencia:** [Sesión 4 — Wallets, Keypairs y Seed Phrases (`[0:11:04]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-1-wallets-keypairs-y-seed-phrases-01104) · [Sesión 3 — Wallets, Claves y Criptografía (`[0:17:01]`)](../rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md#-2-wallets-claves-y-criptografía-01701)
* **Una copia de la blockchain** ❌  
  Quienes almacenan copias del historial y estado completo de la red son los **nodos RPC y validadores**, no las wallets de usuario.  
  🔗 **Referencia:** [Sesión 3 — Nodos, Validadores, RPC y Delegadores (`[0:18:41]`)](../rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md#-3-nodos-validadores-rpc-y-delegadores-01841)
* **Tu historial** ❌  
  El historial de transacciones vive registrado en la cadena de bloques y es consultado/indexado por exploradores (como Solscan) o nodos RPC.  
  🔗 **Referencia:** [Conceptos — ¿Qué es una Blockchain?](../conceptos/02-que-es-blockchain.md)

---

## 2. Borraste Phantom de tu celular. ¿Qué necesitas para recuperar tus fondos?

* **Tu contraseña de Phantom** ❌  
  La contraseña local solo sirve para desbloquear la interfaz en ese dispositivo específico; al desinstalar la app, no permite recuperar tus claves en otro lado.
* **Tu dirección pública** ❌  
  La dirección pública funciona como un CBU/CVU: es pública y sirve para recibir fondos o ver saldos, pero no autoriza a mover dinero.  
  🔗 **Referencia:** [Conceptos — Criptografía Asimétrica](../conceptos/02-que-es-blockchain.md#2-criptografía-asimétrica-llave-pública-y-llave-privada)
* **Tu seed phrase** ✅ *(Correcta)*  
  La frase semilla (*seed phrase* de 12 o 24 palabras) regenera de forma determinista tus llaves privadas en Phantom o en cualquier otra wallet compatible (portabilidad entre Solflare, Backpack, etc.).  
  🔗 **Referencia:** [Sesión 4 — Wallets, Keypairs y Seed Phrases (`[0:11:04]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-1-wallets-keypairs-y-seed-phrases-01104)
* **Escribirle a soporte** ❌  
  Phantom es una wallet **no custodial**: no existe ningún soporte ni servidor central que guarde tus llaves o pueda restablecer tu acceso (*"Not your keys, not your coins"*).  
  🔗 **Referencia:** [Sesión 4 — Custodiales vs. No Custodiales (`[0:16:47]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-2-custodiales-vs-no-custodiales-y-tipos-de-wallets-01647-02124)

---

## 3. ¿Qué diferencia hay entre firmar una transacción y firmar un mensaje?

* **Ninguna** ❌  
  Cumplen propósitos y niveles de riesgo totalmente distintos dentro del ecosistema.
* **La transacción cambia algo on-chain y paga fee; el mensaje solo prueba que la dirección es tuya** ✅ *(Correcta)*  
  Firmar una transacción envía instrucciones a los validadores para modificar el estado *on-chain* (y consume *fee* base en lamports). Firmar un mensaje (`signMessage`) ocurre *off-chain* (por ejemplo, para iniciar sesión en una DApp) y solo demuestra criptográficamente que controlás esa dirección sin costo ni cambios en la red.  
  🔗 **Referencia:** [Sesión 4 — Firmar Transacciones vs. Mensajes (`[0:29:18]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-3-firmar-transacciones-vs-mensajes-y-wallet-standard-02918)
* **El mensaje mueve fondos y la transacción no** ❌  
  Es al revés: únicamente una transacción validada en la red puede modificar balances o estados de cuentas.
* **Firmar un mensaje cuesta más fee** ❌  
  Firmar un mensaje de autenticación es gratuito (0 lamports), mientras que las transacciones abonan un *fee* base de 5,000 lamports por firma.  
  🔗 **Referencia:** [Sesión 5 — Atomicidad, Límites, Comisiones y Ciclo de Vida (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)

---

## 4. Una página te pide "conectar tu wallet". ¿Qué recibe la página al conectar?

* **Tu seed phrase** ❌  
  Jamás se entrega la *seed phrase* al conectar una wallet; si un sitio te la pide, es un intento de *phishing*.  
  🔗 **Referencia:** [Sesión 4 — Seguridad, Estafas Comunes y Buenos Hábitos (`[0:33:39]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-4-seguridad-estafas-comunes-y-buenos-hábitos-03339)
* **Permiso para mover tus fondos** ❌  
  Conectar la wallet no otorga permisos para gastar ni transferir nada; cada movimiento requiere que el usuario apruebe y firme explícitamente la transacción correspondiente.  
  🔗 **Referencia:** [Sesión 4 — Wallet Standard (`[0:29:18]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-3-firmar-transacciones-vs-mensajes-y-wallet-standard-02918)
* **Solo tu dirección pública** ✅ *(Correcta)*  
  Mediante el *Wallet Standard*, la acción `connect` únicamente comparte tu llave pública (`Pubkey`) para que la aplicación pueda leer tus saldos e identificarte.  
  🔗 **Referencia:** [Sesión 4 — Firmar Transacciones vs. Mensajes y Wallet Standard (`[0:29:18]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-3-firmar-transacciones-vs-mensajes-y-wallet-standard-02918)
* **Tu llave privada** ❌  
  La llave privada nunca sale de tu billetera ni se expone a las DApps.  
  🔗 **Referencia:** [Conceptos — Criptografía Asimétrica](../conceptos/02-que-es-blockchain.md#2-criptografía-asimétrica-llave-pública-y-llave-privada)

---

## 5. Creaste una wallet nueva y pegas la dirección en Solscan. Dice "cuenta no encontrada". ¿Por qué?

* **La wallet está mal creada** ❌  
  Las llaves Ed25519 se generan válidamente de manera local aunque todavía no tengan actividad registrada en la red.
* **Solscan está caído** ❌  
  Solscan consulta el estado actual de la blockchain; simplemente refleja que esa dirección aún no tiene una cuenta inicializada en el *ledger*.
* **Crear una wallet es matemática offline; la cuenta aparece cuando recibe su primer SOL** ✅ *(Correcta)*  
  Generar un *keypair* es pura matemática criptográfica en tu dispositivo (no toca la red). En Solana, mantener una cuenta en memoria cuesta **renta** (*rent-exempt*, ~0.00089 SOL mínimo para 0 bytes); por la regla de la primera transferencia, la cuenta recién se crea y aparece en la blockchain cuando recibe su primer depósito de lamports/SOL.  
  🔗 **Referencia:** [Sesión 5 — Propiedad, System Program y Renta (`[0:21:50]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-2-propiedad-system-program-y-renta-rent-02150) · [Conceptos — El Modelo de Cuentas en Solana](../conceptos/03-solana-y-arquitectura.md#-el-modelo-de-cuentas-accounts-model-la-clave-de-solana)
* **Hay que registrarla en la blockchain primero** ❌  
  No hace falta ningún registro manual previo: el `System Program` inicializa la cuenta automáticamente en cuanto recibe su primer SOL.  
  🔗 **Referencia:** [Sesión 5 — System Program (`[0:21:50]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-2-propiedad-system-program-y-renta-rent-02150)
