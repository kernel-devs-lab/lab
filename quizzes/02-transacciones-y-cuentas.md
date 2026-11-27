# 📝 Quiz 02: Transacciones y Cuentas

Cuestionario de evaluación del **Rust Bootcamp (Dev3pack x Solana)** con la justificación de cada opción y su referencia directa a los resúmenes del laboratorio.

---

## 1. Una transacción tiene 3 instrucciones. Las dos primeras se ejecutan bien, pero la tercera falla. ¿Qué pasa?

* **Toda la transacción falla, se revierten todos los cambios y aun así se cobra la comisión** ✅ *(Correcta)*  
  Las transacciones en Solana son **atómicas (todo o nada)**: si falla una sola instrucción, se revierten por completo los cambios de las instrucciones anteriores, pero los validadores igual cobran el *fee* por el trabajo computacional realizado.  
  🔗 **Referencia:** [Sesión 5 — Atomicidad, Límites, Comisiones y Ciclo de Vida (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)
* **Toda la transacción falla y no se cobra ninguna comisión** ❌  
  Solo no se cobra comisión si la transacción es rechazada antes en la simulación (*preflight*); una vez enviada y ejecutada por el validador, el *fee* se cobra aunque falle.  
  🔗 **Referencia:** [Sesión 6 — Simulación, Confirmación y Manejo de Errores (`[1:05:30]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-5-simulación-confirmación-y-manejo-de-errores-10530-11643)
* **Se guardan los cambios de las dos primeras y solo se revierte la tercera** ❌  
  Violaría el principio de **atomicidad**: nunca quedan estados ejecutados a medias dentro de una misma transacción.  
  🔗 **Referencia:** [Sesión 5 — Atomicidad (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)

---

## 2. ¿Cuánto cuesta en comisión base una transferencia simple de SOL con una sola firma?

* **200,000 lamports** ❌  
  `200,000` corresponde al límite por defecto de **Compute Units (CU)** por instrucción, no al costo de la comisión en lamports.  
  🔗 **Referencia:** [Sesión 5 — Límites (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)
* **5,000 lamports (0.000005 SOL)** ✅ *(Correcta)*  
  En Solana la comisión base fija es de **5,000 lamports por cada firma** incluida en la transacción (`0.000005 SOL`), más cualquier *priority fee* opcional.  
  🔗 **Referencia:** [Sesión 3 — Diferenciadores de Solana (`[0:30:47]`)](../rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md#-4-pow-vs-pos-y-el-trilema-de-la-blockchain-02157-02442) · [Sesión 5 — Comisiones (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)
* **890,880 lamports (0.00089 SOL)** ❌  
  Ese valor corresponde a la **renta mínima (*rent-exempt*)** necesaria para mantener una cuenta de 0 bytes viva en la red, no al costo de transferir SOL.  
  🔗 **Referencia:** [Sesión 5 — Propiedad, System Program y Renta (`[0:21:50]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-2-propiedad-system-program-y-renta-rent-02150)

---

## 3. ¿Para qué sirve el blockhash reciente dentro del mensaje de una transacción?

* **Indica cuántas compute units se solicitan** ❌  
  El límite y precio de *compute units* se configura mediante instrucciones del programa `ComputeBudget`, no mediante el *blockhash*.  
  🔗 **Referencia:** [Sesión 5 — Anatomía de una Transacción (`[0:32:47]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-4-anatomía-de-una-transacción-e-instrucciones-03247-04057)
* **Es la firma del remitente** ❌  
  Las firmas criptográficas (64 bytes cada una) van en el arreglo de firmas fuera del mensaje de la transacción.  
  🔗 **Referencia:** [Sesión 5 — Anatomía de una Transacción (`[0:32:47]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-4-anatomía-de-una-transacción-e-instrucciones-03247-04057)
* **Prueba que la transacción es reciente y evita que se repita** ✅ *(Correcta)*  
  Actúa como marca de tiempo criptográfica y protección contra ataques de repetición (*replay attacks*). El *recent blockhash* expira tras **150 bloques** (~1 minuto), impidiendo que una misma transacción firmada vuelva a ejecutarse más tarde.  
  🔗 **Referencia:** [Sesión 5 — Anatomía y Expiración (`[0:32:47]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-4-anatomía-de-una-transacción-e-instrucciones-03247-04057) · [Sesión 3 — Expiración del blockhash (`[1:00:29]`)](../rust%20bootcamp/resumen/03-infraestructura-solana-y-cli.md#-5-clusters-y-práctica-con-solana-cli-03529-03700)

---

## 4. ¿Qué nivel de commitment indica que una transacción es prácticamente irreversible?

* **Confirmed** ❌  
  Indica que una supermayoría de validadores ya votó a favor del bloque (suficiente para la mayoría de las DApps rápidas), pero aún no alcanzó finalidad definitiva.  
  🔗 **Referencia:** [Sesión 6 — Simulación, Confirmación y Manejo de Errores (`[1:05:30]`)](../rust%20bootcamp/resumen/06-solana-kit-typescript.md#-5-simulación-confirmación-y-manejo-de-errores-10530-11643)
* **Finalized** ✅ *(Correcta)*  
  Es el nivel máximo de confirmación (`processed` $\rightarrow$ `confirmed` $\rightarrow$ `finalized`): indica que el bloque quedó consolidado tras múltiples confirmaciones posteriores y la transacción es prácticamente irreversible.  
  🔗 **Referencia:** [Sesión 5 — Confirmación y Ciclo de Vida (`[0:46:15]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-5-atomicidad-límites-comisiones-y-ciclo-de-vida-04615-05141)
* **Submitted** ❌  
  No es un nivel de *commitment* de confirmación en Solana (los tres niveles son `processed`, `confirmed` y `finalized`).

---

## 5. ¿Cuáles son las tres partes de una instrucción?

* **Program ID, cuentas (marcadas como firmante y/o escribible) y datos** ✅ *(Correcta)*  
  Cada instrucción dentro de una transacción especifica: a qué programa llamar (`Program ID`), qué cuentas va a leer o modificar (indicando cuáles deben firmar y cuáles son mutables) y los bytes de argumentos (`data`).  
  🔗 **Referencia:** [Sesión 5 — Anatomía de una Transacción e Instrucciones (`[0:40:57]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-4-anatomía-de-una-transacción-e-instrucciones-03247-04057)
* **Remitente, destinatario y comisión** ❌  
  Eso describe únicamente una transferencia simple de alto nivel, no la estructura general de una instrucción ejecutada por cualquier programa en Solana.
* **Encabezado, claves de cuentas e instrucciones** ❌  
  Esos son los componentes del **Mensaje** completo de la transacción (junto con el *recent blockhash*), no las partes internas de una instrucción individual.  
  🔗 **Referencia:** [Sesión 5 — Anatomía de una Transacción (`[0:32:47]`)](../rust%20bootcamp/resumen/05-arquitectura-cuentas-pdas-transacciones.md#-4-anatomía-de-una-transacción-e-instrucciones-03247-04057)
