# Guía de Estudio: Rust Basics para Solana (Sesión 1)

Basado en la clase oficial: **Session 1 - Rust Basics #1 (Bootcamp de Solana en Español)**  
Transcripción completa guardada en: [`../transcripciones/transcripcion_rust_session_1.txt`](../transcripciones/transcripcion_rust_session_1.txt)

---

## 📌 Índice de la Sesión
1. [¿Por qué Solana eligió Rust?](#1-por-qué-solana-eligió-rust)
2. [Modelo de Cuentas y Estado en Solana](#2-modelo-de-cuentas-y-estado-en-solana)
3. [Variables, Inmutabilidad y Tipos de Datos](#3-variables-inmutabilidad-y-tipos-de-datos)
4. [Funciones y Control de Flujo](#4-funciones-y-control-de-flujo)
5. [Ownership (Propiedad) y Borrowing (Préstamo)](#5-ownership-y-borrowing-el-corazón-de-rust)
6. [Manejo de Errores y Seguridad (Option y Result)](#6-manejo-de-errores-y-seguridad)
7. [Resumen y Conclusiones para el Hackathon](#7-resumen-y-conclusiones-para-el-hackathon)

---

## 1. ¿Por qué Solana eligió Rust? `[0:18:55]`

Solana busca procesar miles de transacciones por segundo con bloques de ~400 milisegundos. Para lograrlo, los fundadores eligieron Rust por tres razones técnicas fundamentales:

1. **Sin Garbage Collector (Recolector de basura):**
   * Lenguajes como Java, Go o JavaScript pausan la ejecución o consumen ciclos de CPU en segundo plano para limpiar memoria.
   * En Solana, una pausa para recolectar memoria rompería el determinismo del tiempo de bloque. Rust libera la memoria en tiempo de compilación.
2. **Seguridad de Memoria (Memory Safety):**
   * Previene errores críticos como *null pointer dereference*, desbordamientos de búfer (*buffer overflow*) y condiciones de carrera (*race conditions*) sin penalización de rendimiento.
3. **Compilación a eBPF/SBF (Solana Bytecode Format):**
   * El código Rust se compila a instrucciones de bajo nivel hiperoptimizadas que la máquina virtual de Solana (SVM) ejecuta casi a velocidad de hardware nativo.

---

## 2. Modelo de Cuentas y Estado en Solana `[0:17:30]`

En Solana:
* **Los programas (Smart Contracts) son apátridas (stateless):** No guardan variables dentro del código ejecutable.
* **Todo se guarda en Cuentas (Accounts):**
  * Hay cuentas que guardan código (programas marcados como ejecutables).
  * Hay cuentas que guardan datos (balances, estados de juegos, NFTs, votos).
* **El ciclo de una transacción:**
  1. El usuario envía una instrucción al programa.
  2. Le pasa las cuentas que se van a leer o modificar.
  3. El programa se ejecuta:
     * Si la lógica es correcta: **Modifica el Ledger** (actualiza saldos o datos).
     * Si falla alguna comprobación: **Revierte la transacción y devuelve un error**.

---

## 3. Variables, Inmutabilidad y Tipos de Datos `[0:22:20]`

### Inmutabilidad por Defecto
En Rust, **toda variable es inmutable por defecto**. Para poder cambiar su valor, hay que declararla explícitamente con `mut`:

```rust
// Inmutable (no se puede reasignar)
let sol_balance: u64 = 100; 

// Mutable (se puede reasignar)
let mut contador: u32 = 0;
contador += 1;
```

### Tipos Numéricos en Solana
En Solana las cantidades de SOL se manejan internamente en **Lamports** (1 SOL = $10^9$ Lamports, equivalente a los Satoshis en Bitcoin):
* `u64`: Entero sin signo de 64 bits. **Es el tipo estándar en Solana para balances y tokens**, porque los saldos nunca pueden ser negativos y requieren rangos altos.
* `bool`: Boleanos (`true` / `false`) para estados y banderas de permisos.
* `Pubkey`: Arreglo de 32 bytes (`[u8; 32]`) que representa la dirección pública de una cuenta o billetera.

---

## 4. Funciones y Control de Flujo `[0:40:50]`

### Retorno Implícito
En Rust no siempre hace falta la palabra clave `return`. La última expresión de un bloque sin punto y coma (`;`) se evalúa y se retorna automáticamente:

```rust
fn calcular_comision(monto: u64) -> u64 {
    // Sin punto y coma al final = retorno implícito
    monto * 5 / 100 
}
```

### Iteradores y Filtrado Funcional
En lugar de bucles `for` tradicionales propensos a errores de índice, Rust favorece los iteradores declarativos:

```rust
let pagos = vec![10, 50, 150, 20];
let umbral = 30;

// Filtra y cuenta pagos que superen el umbral
let pagos_grandes = pagos.iter().filter(|&&m| m > umbral).count();
```

---

## 5. Ownership y Borrowing: El Corazón de Rust `[0:46:00]`

Es la característica más importante de Rust y la que más dudas genera al empezar:

### Las 3 Reglas del Ownership
1. Cada valor en Rust tiene un único dueño (variable).
2. Solo puede haber un dueño a la vez.
3. Cuando el dueño sale del alcance (*scope* o `{}`), el valor se elimina automáticamente de la memoria (`drop`).

### Move vs Borrow (Préstamo)
* **Move (Transferencia de propiedad):**
  ```rust
  let s1 = String::from("solana");
  let s2 = s1; // s1 se "mueve" a s2. s1 ya no es válida.
  ```
* **Borrowing (Referencias con `&`):**
  Para permitir que una función lea datos sin quitarle la propiedad al llamador:
  ```rust
  fn validar_cuenta(cuenta: &AccountInfo) {
      // Leemos prestado sin destruir la cuenta
  }
  ```
* **Regla de referencias:** Puedes tener muchas referencias inmutables (`&T`) simultáneas, O BIEN una sola referencia mutable (`&mut T`), pero **nunca ambas al mismo tiempo**. Esto evita condiciones de carrera.

---

## 6. Manejo de Errores y Seguridad `[0:38:00]`

Rust **no tiene `null` ni excepciones tradicionales (`try / catch`)**.

### El Enum `Option<T>`
Para valores que pueden existir o no:
* `Some(valor)`: Contiene un valor.
* `None`: No hay valor.

```rust
let balance: Option<u64> = obtener_balance_cuenta(&pubkey);

match balance {
    Some(monto) => println!("El saldo es: {}", monto),
    None => println!("La cuenta no existe"),
}
```

### El Enum `Result<T, E>`
Para operaciones que pueden fallar (como enviar una transacción o descontar fondos):
* `Ok(T)`: Operación exitosa con su resultado.
* `Err(E)`: Ocurrió un error con su motivo.

```rust
fn transferir(origen_balance: u64, monto: u64) -> Result<u64, &'static str> {
    if origen_balance < monto {
        Err("Fondos insuficientes: no se puede transferir más del saldo disponible")
    } else {
        Ok(origen_balance - monto)
    }
}
```

---

## 7. Resumen y Conclusiones para el Hackathon

1. **Para contratos (Anchor/Rust):**
   * Usa `u64` para balances.
   * Diseña funciones que validen con `Result<T, E>` antes de modificar saldos.
   * Todo lo que no necesite mutar, pásalo por referencia inmutable `&`.
2. **Para prototipar rápido:**
   * Apóyate en los tipos y el compilador: si Rust compila, el 90% de los bugs de memoria y estado ya están resueltos.
   * Utiliza la Devnet de Solana para desplegar y probar sin costo real.
