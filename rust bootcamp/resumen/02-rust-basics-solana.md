# Guía de Estudio: Rust Basics para Solana (Sesión 2)

Basado en la clase oficial: **Session 2 - Rust Basics #2 (Bootcamp de Solana en Español)**  
Transcripción completa guardada en: [`../transcripciones/transcripcion_rust_session_2.txt`](../transcripciones/transcripcion_rust_session_2.txt)

> **Nota:** esta sesión continúa la [Sesión 1](./01-rust-basics-solana.md).

---

## 📌 Índice de la Sesión
1. [Contexto y repaso de la clase 1](#1-contexto-y-repaso-de-la-clase-1)
2. [Structs e `impl`: estructuras de datos propias (Ejercicio 5)](#2-structs-e-impl-estructuras-de-datos-propias)
3. [Enums y `match` (Ejercicio 6)](#3-enums-y-match)
4. [`Option<T>`: valores que pueden no existir](#4-optiont-valores-que-pueden-no-existir)
5. [`Result<T, E>` y el operador `?` (Ejercicio 7)](#5-resultt-e-y-el-operador-)
6. [Mini proyecto, puente a Anchor y errores comunes (Ejercicio 8)](#6-mini-proyecto-puente-a-anchor-y-errores-comunes)
7. [Tarea y entrega](#7-tarea-y-entrega)
8. [Resumen y Conclusiones para el Hackathon](#8-resumen-y-conclusiones-para-el-hackathon)

---

## 1. Contexto y repaso de la clase 1 `[0:06:07]`

El objetivo de hoy es ver la segunda parte de los básicos de Rust **para poder usar Anchor más adelante**: Anchor es el framework con el que se escriben los programas de Solana, y se apoya en muchas de las cosas que se ven en estas dos clases.

* **¿Qué es un programa de Solana?** `[0:07:24]` Es lo que le agrega *programabilidad* a la blockchain. Una blockchain sola sirve para transferir (enviar 1 SOL a A o a B); con programas se pueden construir protocolos (conjuntos de programas), por ejemplo uno donde una persona pida un préstamo respaldado por los activos que ya tiene.
* **Repaso de la sesión anterior** `[0:10:22]`:
  * **Ownership:** cada valor tiene un dueño; se puede *mover* o *prestar*.
  * **Borrowing:** se puede prestar para solo leer (`&`) o para escribir (`&mut`), pero no ambas cosas a la vez.
  * **`cargo test`:** el comando para probar los ejercicios. La clase pasada se vio el comando, pero no cómo es un test por dentro; hoy se ve un poco.
* **Avance de ejercicios** `[0:11:32]`: la clase 1 cubrió los ejercicios **1 al 4**; hoy se ven del **5 al 7**, y el **8 es un mini proyecto** (una compilación de lo anterior: un mini banco).
* **Importante:** todavía **no se trabaja con Solana como tal**, solo con Rust.

**Plan de la clase** `[0:11:57]`: structs → enums y `match` → `Option` → `Result` y `?` → mini proyecto → puente a Anchor → errores comunes.

**Recurso recomendado** `[0:12:26]`: el libro oficial de Rust (*The Rust Programming Language*) para ampliar cualquier tema técnico. Cubre variables, funciones, tipos, ownership, borrowing, enums y `match`. Aun así, la clase no sigue el libro al pie de la letra porque se prioriza lo que Anchor usa.

---

## 2. Structs e `impl`: estructuras de datos propias `[0:13:50]`

Un **struct** es una estructura de datos *propia*: agrupa varios datos bajo un mismo nombre. Ejemplo pensado en una cuenta (de banco o de Solana): en lugar de guardar por separado nombre, ID y saldo, se define "una cuenta" que los contiene a todos.

### Ejercicio 5: una cuenta de Solana simplificada `[0:19:25]`

```rust
pub struct Account {
    pub address: String,
    pub lamports: u64,
    pub owner: String,
}

impl Account {
    // Constructor: una cuenta nueva SIEMPRE empieza con 0 lamports
    pub fn new(address: String) -> Self {
        Account {
            address,                     // atajo: el campo y el parámetro se llaman igual
            lamports: 0,
            owner: "system".to_string(), // en el ejercicio el owner es el sistema
        }
    }

    // Depositar: no devuelve nada
    pub fn deposit(&mut self, amount: u64) {
        self.lamports += amount;         // equivale a self.lamports = self.lamports + amount
    }

    // Retirar: devuelve true si pudo, false si no hay fondos (y deja el saldo igual)
    pub fn withdraw(&mut self, amount: u64) -> bool {
        if self.lamports < amount {
            return false;
        }
        self.lamports -= amount;
        true
    }

    // Balance en SOL: lamports / constante (1 SOL = 1.000 millones de lamports)
    pub fn balance_in_sol(&self) -> u64 {
        self.lamports / LAMPORTS_PER_SOL
    }
}
```

Puntos clave de la explicación:

* **Por qué `new` empieza en 0:** una cuenta no puede nacer con dinero ("¿de dónde saldría esa plata?"). Además, los tests verifican justamente eso.
* **Atajo de inicialización:** si en el struct se escribe solo el nombre del campo (`address`), Rust usa el parámetro de la función que se llama igual (`address: address`).
* **`.to_string()`:** convierte `"system"` (texto literal) en un `String` de Rust, que es lo que espera el campo.
* **`&mut self`:** `self` es la propia cuenta sobre la que se llama la función; con `mut` se indica que se le pueden modificar los datos (conecta con el borrowing de la clase 1). `balance` solo lee, por eso usa `&self`.
* **`+=` y `-=`** son equivalentes a escribir `self.lamports = self.lamports + amount`. Cualquiera de las dos formas es válida.
* **`withdraw` con `<` (estricto):** si tengo 999 lamports y pido retirar 1.000.000, devuelve `false`. Sin `return` explícito en la última línea, `true` funciona como retorno (retorno implícito, visto en la clase 1).
* **Firma de una función:** `pub fn nombre(parámetros) -> TipoDeRetorno`. En `withdraw` el tipo es `bool`; en `deposit` no hay flecha porque no devuelve nada; en el balance en SOL devuelve `u64`.

### `#[derive(...)]` `[0:17:11]`
Sobre un struct se pueden poner atributos como `#[derive(Debug, Clone, PartialEq)]`. `derive` **genera código por debajo** que no hay que escribir (imprimir para depurar, clonar, comparar). En este ejercicio no es relevante, pero en **Anchor se usa muchísimo** (por ejemplo `#[derive(Accounts)]`, que genera todo el código de manejo de cuentas).

### Los tests por dentro `[0:32:13]`
* Se corre un ejercicio puntual con `cargo test` más el flag con el nombre del ejercicio (así no se ejecutan todos).
* Los **warnings** del compilador (cosas "sin usar" de los ejercicios no resueltos) se pueden ignorar; para ocultarlos se puede anteponer `RUSTFLAGS="-A warnings"` al comando `cargo test ...` `[1:08:05]`.
* Un test es una función marcada con **`#[test]`** (eso es una *macro*). Adentro usa `assert_eq!(izquierda, derecha)`, que verifica que ambas expresiones sean iguales `[0:33:34]`.
* **Ejemplo de fallo** `[0:34:17]`: si `new` crea la cuenta con 1 lamport en lugar de 0, los demás tests fallan (esperaba 600 y dio 601), porque cada aserción compara contra el valor correcto.

### Para tener en cuenta (comentarios del profesor)
* **Auditorías** `[0:41:04]`: un programa de Solana no se tira directo a mainnet; debe pasar por una auditoría que revise errores y vulnerabilidades. Recomendación: escribir **código y comentarios en inglés**, porque los auditores suelen trabajar en ese idioma.
* **Hackathon vs. producción** `[0:41:48]`: en el hackathon se trabaja probablemente en **devnet** (fondos falsos); si luego pasan al acelerador y manejan dinero real, la auditoría es clave.
* **Anchor vs. Pinocchio** `[0:35:51]`: Pinocchio es otra forma de hacer programas de Solana. El profesor solo ha usado Anchor y lo recomienda; si alguien quiere usar Pinocchio en su proyecto del curso, no hay problema.

---

## 3. Enums y `match` `[0:37:57]`

Un **enum** permite que un dato sea *una de varias variantes*, cada una con sus propios parámetros. Es similar a los enums de C, pero cada variante puede cargar datos.

```rust
pub enum Instruction {
    Transfer { from: String, to: String, lamports: u64 },
    CreateAccount { address: String },
    Close { address: String },
}
```

**`match`** recibe un valor del enum y devuelve un resultado distinto según la variante:

* **Es exhaustivo:** si falta una variante, el código **no compila** (el compilador avisa que falta un caso).
* Se pueden usar los parámetros de la variante dentro de la rama.

> **Conexión con Anchor** `[0:39:14]`: el enum modela los *datos de la instrucción* (instruction data). Las **cuentas llegan por separado** en un `Context`, tema que se verá más adelante.

### Ejercicio 6: tres funciones sobre `Instruction` `[0:41:04]`

```rust
// 1) kind: qué tipo de instrucción es
pub fn kind(ix: &Instruction) -> &'static str {
    match ix {
        Instruction::Transfer { .. }      => "transfer",
        Instruction::CreateAccount { .. } => "create",
        Instruction::Close { .. }         => "close",
    }
}

// 2) lamports_moved: cuántos lamports mueve (solo Transfer mueve algo)
pub fn lamports_moved(ix: &Instruction) -> u64 {
    match ix {
        Instruction::Transfer { lamports, .. } => *lamports,
        Instruction::CreateAccount { .. }      => 0,
        Instruction::Close { .. }              => 0,
    }
}

// 3) primary_account: la cuenta "sujeto principal" de la instrucción
pub fn primary_account(ix: &Instruction) -> &str {
    match ix {
        Instruction::Transfer { from, .. }       => from,     // la que envía
        Instruction::CreateAccount { address }   => address,  // la nueva cuenta
        Instruction::Close { address }           => address,  // la que se cierra
    }
}
```

* **`kind`:** `&'static str` es un texto fijo; devuelve `"transfer"`, `"create"` o `"close"`. El nombre viene de *kind* = "tipo" en inglés. Los tests esperan esos textos exactos: devolver `"transferir"` en vez de `"transfer"` hace fallar el test `[0:50:54]`.
* **`lamports_moved`:** solo `Transfer` mueve lamports; crear y cerrar una cuenta devuelven `0`. Escribir el nombre del campo (`lamports`) dentro de la rama lo "extrae" del enum para usarlo.
* **`primary_account`:** en `Transfer` la cuenta principal es `from`; en `CreateAccount` y `Close`, `address`.
* Se recibe la instrucción por **referencia inmutable** (`&Instruction`) porque solo se lee; no se quiere editar.

---

## 4. `Option<T>`: valores que pueden no existir `[0:51:30]`

`Option` expresa "quizás hay un valor". No existe `null`: en su lugar hay dos variantes.

* `Some(valor)`: sí hay valor.
* `None`: no hay nada (no se encontró).

```rust
fn find(id: u8) -> Option<u64> {
    if id == 1 {
        Some(5000)   // lo encontró: devuelve 5000
    } else {
        None         // no lo encontró: no devuelve nada
    }
}

let maybe = find(1);                 // Some(5000)
let amount = maybe.unwrap_or(0);     // si fuera None, usa 0 por defecto
```

* **`unwrap_or(0)`** funciona como un **valor por defecto**: si `maybe` es `None`, se usa `0`; si trae un valor, se usa ese valor. Por eso `amount` siempre queda con un número válido.
* Aquí `u8` es un entero sin signo de 8 bits (el `id`) y el valor devuelto es un `u64`.

---

## 5. `Result<T, E>` y el operador `?` `[0:54:07]`

### Enum de errores propio
Es habitual juntar todos los errores posibles de una operación en un enum, y algunas variantes pueden llevar **datos extra** para informar mejor al usuario:

```rust
pub enum TransferError {
    InsufficientFunds { available: u64, required: u64 }, // cuánto tenía vs. cuánto hacía falta
    ZeroAmount,                                          // monto cero
    SameAccount,                                         // transferencia a la misma cuenta
}
```

### `Result`
Una función que puede fallar devuelve `Result<T, E>`:

* `Ok(valor)`: salió bien. Si no hay valor que devolver se usa `Ok(())` (los paréntesis vacíos); es la **convención**.
* `Err(error)`: falló, con el motivo.

### Operador `?` `[1:01:30]`
Al llamar a otra función que devuelve `Result`, el signo **`?` propaga el error**: si la función interna falló, ese mismo error se devuelve de inmediato desde la función actual; si salió bien, el código sigue. Sin el `?`, el error de la función interna no se transmite.

### Ejercicio 7: validar y transferir `[0:57:53]`

```rust
// Paso 1: reglas que no dependen del saldo (en este orden)
fn validate(from: &str, to: &str, amount: u64) -> Result<(), TransferError> {
    if amount == 0 {
        return Err(TransferError::ZeroAmount);
    }
    if from == to {
        return Err(TransferError::SameAccount);
    }
    Ok(())
}

// Paso 2: transferir; devuelve el saldo restante de quien envía
pub fn transfer(from: &str, to: &str, amount: u64, balance: u64) -> Result<u64, TransferError> {
    validate(from, to, amount)?;                    // propaga el error si lo hay
    if balance < amount {
        return Err(TransferError::InsufficientFunds {
            available: balance,
            required: amount,
        });
    }
    Ok(balance - amount)
}
```

* **Solo se devuelve el primer error** `[1:15:19]` (pregunta de un estudiante): si el monto es cero *y además* se envía a la misma cuenta, solo se retorna el primero que se evalúa; la función termina ahí y nunca llega a revisar lo demás.
* El error `InsufficientFunds` entrega `available` y `required`, para que el usuario sepa por cuánto no alcanzó (ej.: tiene 1.000 y necesita 1.001).
* **Errores típicos al resolverlo** `[1:04:45]`: olvidar el `;` después del `?` o no terminar con `Ok(...)` produce el error de tipos "expected `u64`/`Result`, found `()`".

### ⚠️ Errores en Solana cuestan plata `[0:56:36]`
En Solana **un error revierte el estado, pero el *fee* se cobra igual**. Cada transacción cobra una comisión (los validadores no trabajan gratis), así que un programa mal hecho en mainnet hace que el usuario pierda plata en cada intento fallido. Por eso es tan importante validar bien y auditar.

---

## 6. Mini proyecto, puente a Anchor y errores comunes `[1:05:57]`

### Ejercicio 8: mini banco (se hace en casa)
* Un struct de cuenta de banco con: `owner` (la persona), `lamports` y `history` (un **`Vec<String>`** con el historial de transacciones).
* Un `Vec` es, de forma aproximada, como una **lista de Python** (no es el vector de álgebra lineal). El historial **no es un HashMap**: es una lista ordenada de textos.
* Hay que implementar crear cuenta, `deposit`, `withdraw` y `balance`, **registrando cada transacción en el historial**.
* Se entrega un enum `BankError`: hay que usar **`Result` con errores definidos y no `panic!`** (el *panic* es el "modo pánico" de Rust, que detiene todo).
* Se prueba con `cargo test` sobre el ejercicio 8.

### Puente a Anchor (versión simplificada) `[1:08:48]`
Lo visto hoy aparece directamente en Anchor:

* **Instrucciones con contexto** (`Context`) y un `amount` de tipo **`u64`** (lamports), por ejemplo en un `deposit`.
* **`Result`** como retorno (Ejercicio 7).
* **`require!`**: "verificá que esto se cumpla y si no, lanzá error".
* **`?`** para propagar errores.
* **`#[derive(Accounts)]`**: genera código extra de manejo de cuentas.
* **`#[account(mut)]`**: marca que una cuenta puede mutarse (misma idea que `mut`).
* **Un enum de códigos de error propio** (`#[error_code]`), igual que `TransferError`.

### Errores comunes del compilador `[1:10:00]`
* **Usar un valor que ya fue movido** → hay que *prestarlo* con `&` (ownership/borrowing de la clase 1).
* **Usar `&` y `&mut` a la vez** sobre el mismo dato → leer antes de escribir genera conflicto.
* **Tipos que no coinciden** → revisar que todos los tipos involucrados sean compatibles.
* **`todo!()`** en los ejercicios: no es un error, solo indica que esa función **aún no está implementada**.

---

## 7. Tarea y entrega `[1:10:38]`

* Completar los ejercicios **del 5 al 8** (la mayoría se resolvieron en clase, pero hay que entenderlos y resolver todos los `todo!()`).
* Pasos: hacer **fork** y clonar el repo de la semana → correr los tests → crear una **rama nueva** → hacer *push* y abrir un **Pull Request** hacia el repo.
* **No modificar los tests**: están hechos para verificar la solución.
* **Puntuación:** hay **18 tests** para esta parte y la nota es proporcional a los aprobados.
* Dentro de la plataforma, la pestaña **Homework** → repo en español contiene las instrucciones y el detalle.

---

## 8. Resumen y Conclusiones para el Hackathon

1. **Para modelar datos (Anchor/Rust):**
   * Agrupa los datos de una cuenta en un `struct` con su `impl` (constructor `new`, `deposit`, `withdraw`...).
   * Una cuenta nueva siempre empieza con `0` lamports.
   * Usa `&self` para solo leer y `&mut self` para modificar.
2. **Para modelar instrucciones y errores:**
   * Usa `enum` para las variantes (`Transfer`, `CreateAccount`, `Close`) y `match` exhaustivo para tratarlas: si falta un caso, no compila.
   * Define un enum de errores propio y devuelve `Result<T, E>`, con datos extra cuando ayuden (`available`/`required`).
   * Propaga con `?` y usa `Ok(())` cuando no hay valor que devolver. No uses `panic!`.
3. **Para pensar en seguridad:**
   * Un error revierte el estado, pero **el fee se cobra igual**: valida antes de mover fondos.
   * Antes de mainnet con dinero real, pasa por una **auditoría**; en el hackathon, trabaja en **devnet**.
   * Escribe código y comentarios en inglés.
