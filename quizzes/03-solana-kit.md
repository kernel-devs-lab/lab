# 📝 Quiz 03: Solana Kit

Cuestionario de evaluación del **Rust Bootcamp (Dev3pack x Solana)** con la justificación de cada opción y su referencia directa a los resúmenes del laboratorio.

---

## 1. ¿Qué ventaja ofrece que `@solana/kit` sea *tree-shakable*?

* **Confirma transacciones sin conexión al RPC.** ❌  
  Toda confirmación de transacciones requiere comunicación con la red a través de un nodo RPC (HTTP y/o WebSockets).  
  🔗 **Referencia:** [Sesión 6 — Comunicación con la Red: HTTP RPC y WebSockets (`[0:21:00]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-3-comunicación-con-la-red-http-rpc-y-websockets-02100-02559)
* **Almacena las claves privadas en la blockchain.** ❌  
  Las claves privadas jamás se suben ni almacenan en la blockchain; siempre permanecen secretas en el cliente o *signer* local.  
  🔗 **Referencia:** [Sesión 4 — Wallets, Keypairs y Seed Phrases (`[0:11:04]`)](../rust%20bootcamp/resumen/04-wallets-seguridad-y-multisig.md#-1-wallets-keypairs-y-seed-phrases-01104)
* **Permite incluir solo las funciones utilizadas y reducir el tamaño del bundle.** ✅ *(Correcta)*  
  Al estar diseñado de forma modular y funcional (sin clases gigantes acopladas como `@solana/web3.js` legado), el empaquetador (Vite, Webpack, Next.js) descarta el código no utilizado (*tree-shaking*), reduciendo drásticamente el peso final en el frontend.  
  🔗 **Referencia:** [Sesión 6 — ¿Por qué Solana Kit en lugar de `@solana/web3.js` legado? (`[0:13:37]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-2-por-qué-solana-kit-en-lugar-de-solanaweb3js-legado-01337)

---

## 2. ¿Cuál es el orden de construcción con `pipe()`?

* **Crear mensaje -> establecer fee payer -> establecer tiempo de vida -> agregar instrucciones.** ✅ *(Correcta)*  
  Con el patrón **`pipe`**, la transacción se construye de manera declarativa e inmutable en ese orden exacto: `createTransactionMessage` $\rightarrow$ `setFeePayer` $\rightarrow$ `setLifetime` (con el *blockhash* reciente) $\rightarrow$ `appendInstruction` (y luego se firma).  
  🔗 **Referencia:** [Sesión 6 — Patrón `pipe`: Construcción, Firma y Envío (`[0:53:20]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-4-patrón-pipe-construcción-firma-y-envío-05320-10530)
* **Crear mensaje -> firmar -> establecer fee payer -> agregar instrucciones** ❌  
  No se puede firmar antes de definir el pagador y las instrucciones, ya que la firma criptográfica se calcula sobre el mensaje completo terminado.
* **Agregar instrucciones -> enviar -> establecer tiempo de vida -> firmar** ❌  
  No se puede enviar una transacción antes de definir su *lifetime* (*blockhash*) ni antes de firmarla.

---

## 3. Al simular una transacción, ¿qué indica `sim.unitsConsumed`?

* **La cantidad de lamports transferidos** ❌  
  Los lamports transferidos corresponden al monto de la operación o saldo, no al consumo computacional de la VM.
* **El número de validadores que confirmaron** ❌  
  Una simulación corre localmente en el nodo RPC antes de enviarse a la red (*preflight*), por lo que no hay votos de validadores.
* **Las unidades de cómputo utilizadas durante la simulación** ✅ *(Correcta)*  
  Indica exactamente cuántas **Compute Units (CU)** consumió la ejecución simulada en la Solana Virtual Machine (por ejemplo, `150` CU en una transferencia simple del `System Program`), útil para estimar límites y *priority fees*.  
  🔗 **Referencia:** [Sesión 6 — Simulación, Confirmación y Manejo de Errores (`[1:05:30]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-5-simulación-confirmación-y-manejo-de-errores-10530-11643) · [Sesión 5 — Límites (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)

---

## 4. Si el *blockhash* de una transacción expiró, ¿qué corresponde hacer?

* **Reenviar exactamente la misma transacción firmada** ❌  
  El *blockhash* antiguo sigue vencido (expira tras 150 bloques / ~1 min), por lo que la red seguirá rechazándola.
* **Reconstruirla con un blockhash nuevo, firmarla y enviarla nuevamente** ✅ *(Correcta)*  
  Como el *recent blockhash* forma parte del cuerpo del mensaje firmado, al expirar es obligatorio consultar un *blockhash* nuevo vía RPC, reconstruir el mensaje, volver a firmarlo y reenviarlo.  
  🔗 **Referencia:** [Sesión 6 — Simulación, Confirmación y Manejo de Errores (`[1:05:30]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-5-simulación-confirmación-y-manejo-de-errores-10530-11643) · [Sesión 3 — Expiración del blockhash (`[1:00:29]`)](../rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md#-5-clusters-y-práctica-con-solana-cli-03529-03700)
* **Aumentar únicamente el límite de cómputo** ❌  
  El límite de *compute units* no afecta la validez temporal de un *blockhash* expirado.
