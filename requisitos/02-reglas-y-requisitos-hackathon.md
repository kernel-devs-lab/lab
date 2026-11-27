# 🏆 Reglas y Requisitos del Dev3pack Hackathon

Resumen detallado de las reglas de calificación, errores eliminatorios, criterios de evaluación y entregables obligatorios para el **Dev3pack Global Hackathon (Build Station Jujuy)**, según lo explicado por los organizadores en las sesiones del bootcamp.

> **Nota:** Para participar y ganar en el Hackathon **no** se exigen los quizzes ni el *Rust assignment* del bootcamp, pero sí el cumplimiento estricto de los puntos detallados abajo.

---

## 🚨 1. Errores Eliminatorios (Descalificación Directa)

* **No integrar un *Solana Program* (on-chain):**  
  En la [Sesión 11 (`[1:27:06]`)](../rust%20bootcamp/resumen/11-vibecode-solana.md#-1-dato-crítico-confirmado-para-calificar-12706), Solène confirmó: *"Every submission should integrate the Solana program to be qualified."* (Podés escribirlo en Rust/Anchor, con tu agente local o con Noah AI).
* **Entregar solo una *Landing Page*:**  
  En la [Sesión 13 (`[0:26:01]`)](../rust%20bootcamp/resumen/13-best-tips-hackathon.md#-1-errores-eliminatorios-lo-que-no-debes-hacer-02119), advirtieron que entregar solo una web informativa sin aplicación funcional es **eliminatorio**.
* **Dejar el repositorio de GitHub en PRIVADO:**  
  En la [Sesión 13 (`[0:21:19]`)](../rust%20bootcamp/resumen/13-best-tips-hackathon.md#-1-errores-eliminatorios-lo-que-no-debes-hacer-02119), si el repo está privado, los jueces y la IA evaluadora no pueden revisarlo y quedás eliminado automáticamente.
* **Incumplir requisitos de Sponsors / Tracks:**  
  Cada sponsor tiene *Qualification Requirements* y una lista explícita de *What gets rejected* ([Sesión 13 `[0:23:46]`](../rust%20bootcamp/resumen/13-best-tips-hackathon.md#-1-errores-eliminatorios-lo-que-no-debes-hacer-02119)).

---

## ✅ 2. Checklist de Entregables (*Submission*) `[0:28:54]`

Según la [Sesión 13](../rust%20bootcamp/resumen/13-best-tips-hackathon.md#-5-checklist-obligatorio-de-entrega-submission-02854):

- [ ] **Repositorio GitHub Público** con un **`README.md` completo** (que incluya diagrama de flujo hecho con Excalidraw o Mermaid explicando la arquitectura).
- [ ] **Aplicación desplegada en vivo** (Vercel, Netlify, etc.) y funcional.
- [ ] **Programa de Solana desplegado** (en Devnet o Mainnet) e integrado con la app.
- [ ] **Video Demo de máximo 3 minutos:** Explicando el problema, demostrando la app funcionando y contando brevemente el *background* del equipo.
- [ ] **Material visual:** Logo, banner y capturas de pantalla de la app para el formulario.
- [ ] **Detalle por Track:** Indicar en el formulario de entrega **el archivo y línea exacta** donde está implementada cada integración de sponsor/track ([Sesión 13 `[0:29:20]`](../rust%20bootcamp/transcripciones/transcripcion_rust_session_13.txt)).

---

## 📋 3. Reglas Generales y Evaluación

* **Participación solo o en equipo:** Confirmado en la [Sesión 13 (`[0:36:11]`)](../rust%20bootcamp/transcripciones/transcripcion_rust_session_13.txt), podés participar de forma individual o armar equipo.
* **¿Se pueden usar ideas o proyectos previos?** **Sí**, confirmado en la [Sesión 10 (`[0:44:07]`)](../rust%20bootcamp/resumen/10-product-ideation.md#-1-reglas-de-oro-para-elegir-tu-idea-02817), siempre que se construya sobre **Solana** y se agreguen nuevas funcionalidades durante el hackathon.
* **¿Cómo evalúan? (`[0:24:34]`):** Combinación de **jueces locales** + **IA técnica profunda** que revisa el código para verificar que las integraciones declaradas sean reales. Al cierre entregan un ***Project Report*** con fortalezas y puntos a mejorar.
* **Post-Hackathon (`[0:38:51]` / `[0:33:13]`):** Los mejores proyectos pueden acceder a la **Aceleradora de Dev3pack** (donde valoran mucho la alineación y *background* del equipo presentado en el video).

---

## 💡 4. Preparación Recomendada Antes de Llegar `[0:17:47]`

1. **Reclamar SOL de Devnet con anticipación** (en [`faucet.solana.com`](https://faucet.solana.com), máx. 2 pedidos cada 8 hs) para evitar saturación al final del evento.
2. **Usar una billetera exclusiva de desarrollo** (*burner wallet* en Phantom/Solflare), nunca tu wallet personal con fondos reales.
3. **Separar la planificación de la ejecución** (Regla 50/50 de *AI Engineering* vista en la [Sesión 11](../rust%20bootcamp/resumen/11-vibecode-solana.md#-2-de-vibecoding-a-ai-engineering-00946)).
