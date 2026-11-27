# 🏆 Mejores Consejos para tu Primer Hackathon (Checklist Ganador)

Basado en la sesión 13 del **Rust Bootcamp (Dev3pack)**: **Best tips for your first hackathon** (con Solène, ganadora de +35 premios en hackathones).  
🎥 Video original: [Best tips for your first hackathon](https://www.youtube.com/watch?v=S9LyP7V82UQ)  
Transcripción completa en inglés guardada en: [`../transcripciones/transcripcion_rust_session_13.txt`](../transcripciones/transcripcion_rust_session_13.txt)

---

## 🚨 1. Errores Eliminatorios (Lo que NO debes hacer)

Solène advirtió sobre fallos simples que dejan fuera a muchísimos equipos automáticamente:

1. **Dejar el repositorio de GitHub en PRIVADO:**  
   Si el repo no es público al momento de la evaluación, ni los jueces ni el sistema de revisión pueden acceder y quedás eliminado automáticamente.
2. **Construir solo una *Landing Page*:**  
   No entregues una web estática bonita explicando qué haría el proyecto. **Debés entregar una aplicación funcional** donde el usuario pueda interactuar con el producto real.
3. **No respetar los requisitos de los Tracks / Sponsors:**  
   Cada sponsor publica requisitos de calificación (*Qualification Requirements*) y una lista explícita de *"What gets rejected"*. Si no cumplís lo que piden, descartan tu envío sin revisarlo.
4. **Integración vacía con Solana:**  
   No basta con poner un botón simbólico de "pagar con cripto" sin sentido; la arquitectura debe aprovechar la blockchain de forma genuina.

---

## ⚡ 2. Preparación Técnica Antes de Empezar (Hazlo HOY)

* **Reclama SOL de Devnet con anticipación:**  
  Al final del hackathon todos intentan desplegar al mismo tiempo y los *faucets* de Devnet se saturan o bloquean. Conseguí tokens de prueba antes de arrancar.
* **Usa una Billetera exclusiva para Desarrollo:**  
  Creá una wallet nueva en Phantom o Solflare solo para programar y testear. **Nunca** uses tu billetera personal con fondos reales (evita riesgos de hacks o drenajes por error).
* **Enfócate en una narrativa clara:**  
  Podés aplicar a más de un track, pero mantené un hilo conductor sólido para no dispersar el producto.
* **¿Solo o en equipo?**  
  Se puede participar en solitario (*solo*) o armar equipo desde la pestaña *Team* del dashboard o el grupo de Telegram.

---

## 🧠 3. Cómo Piensan los Jueces y la IA Evaluadora

* **Revisión técnica profunda con IA + Jueces locales:**  
  En Dev3pack, una IA analiza técnicamente tu repositorio para verificar que las integraciones que declarás sean **reales y no simuladas**. Al finalizar el hackathon recibirás un *Project Report* con fortalezas y puntos a mejorar.
* **Un `README.md` impecable marca la diferencia:**  
  Incluí un **diagrama de flujo** (ej. hecho con Excalidraw o Mermaid) explicando cómo funciona la arquitectura de tu app, cómo navegar el repo y qué hace cada parte. Ayuda tanto a los jueces humanos como a la IA (especialmente si alguna feature quedó a medias).
* **Sé específico al entregar:**  
  En el formulario de *Submit Project*, indicá exactamente **en qué archivo y línea** está integrada la tecnología de cada track/sponsor al que aplicás.

---

## 💡 4. Estrategia de Producto

* **Toda app viable necesita Usuarios o Liquidez.**
* **Diferenciación por contexto:** Aprovechá tu experiencia personal, tu profesión o tu país/región para resolver un problema concreto que otros no ven.
* **Benchmarking entre blockchains:** Mirá qué aplicaciones o protocolos están funcionando muy bien en otras redes (Base, Monad, Stellar) o en **DeFiLlama** que **todavía no existen en Solana**, y construí esa solución en Solana.

---

## ✅ 5. Checklist Obligatorio de Entrega (*Submission*)

Antes de la hora límite (revisar el reloj exacto en tu dashboard según tu zona horaria; mencionado como *7:00 a.m. UTC del domingo* en la charla):

- [ ] **Repositorio de GitHub en modo PÚBLICO** con un `README.md` claro y diagrama de flujo.
- [ ] **Aplicación desplegada en vivo** (Vercel, Netlify, etc.) y funcionando.
- [ ] **Video Demo de máximo 3 minutos:**
  * Qué problema resuelve y descripción breve.
  * Demostración en vivo de la app funcionando.
  * *Tip extra:* Mencionar brevemente el **background del equipo** (los organizadores lo miran para seleccionar candidatos a la **Aceleradora de Dev3pack**).
- [ ] **Material visual:** Logo, banner y capturas de pantalla (*screenshots*) de la app.
- [ ] **Build in Public:** Publicar avances o la entrega final en redes etiquetando a **Dev3pack** y **Solana** para ganar visibilidad y credibilidad.
