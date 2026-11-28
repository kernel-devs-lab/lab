# 🧠 Prompt de Planificación — Frontend Next.js + Solana

> **Uso:** Copiá este prompt y pegalo en tu agente de IA (Antigravity, Cursor, Claude, etc.) al inicio del hackathon para que te planifique y scaffoldee todo el frontend de tu dApp.  
> **Instrucción:** Reemplazá los `[PLACEHOLDER]` con los datos de tu proyecto antes de usar.

---

## El Prompt

```
Actúa como un senior fullstack developer especializado en Web3 y Solana.

Necesito que planifiques e implementes el frontend de mi dApp para un hackathon
que dura 1 día. El proyecto debe estar desplegado y funcional al final del evento.

## CONTEXTO DEL PROYECTO

- Nombre del proyecto: [NOMBRE_DEL_PROYECTO]
- Descripción breve: [QUÉ HACE TU DAPP EN 1-2 ORACIONES]
- Track/sponsor del hackathon: [TRACK O SPONSOR ELEGIDO, si aplica]
- ¿Tenés programa Solana ya deployado? [SÍ/NO — si SÍ, pegá el Program ID]
- ¿Tenés IDL de Anchor? [SÍ/NO — si SÍ, pegá el path o el JSON]

## STACK OBLIGATORIO

- Next.js 15 (App Router, TypeScript, Tailwind CSS)
- React Hook Form + Zod (@hookform/resolvers) para formularios
- @solana/wallet-adapter-react + @solana/wallet-adapter-react-ui para wallet
- @solana/web3.js para interacción con la blockchain
- @coral-xyz/anchor (si el programa usa Anchor)
- lucide-react para iconos SVG (tree-shakeable, compatible con shadcn)
- sonner para notificaciones/toasts
- @tanstack/react-query para data fetching y cache
- Deploy en Vercel

## LO QUE NECESITO QUE HAGAS

### Fase 1 — Scaffolding (prioridad máxima, hacer primero)

1. Crear el proyecto con `create-next-app` (TypeScript, Tailwind, App Router, src/).
2. Instalar TODAS las dependencias de una sola vez.
3. Configurar una paleta de colores con CSS custom properties en globals.css
   para que sea fácil de cambiar en un solo lugar. Definir variables para
   light y dark mode. Ejemplo:

   ```css
   /* src/app/globals.css */
   @tailwind base;
   @tailwind components;
   @tailwind utilities;

   @layer base {
     :root {
       --color-background: 0 0% 100%;
       --color-foreground: 240 10% 3.9%;
       --color-primary: 262 83% 58%;       /* violeta/púrpura */
       --color-primary-foreground: 0 0% 100%;
       --color-secondary: 240 4.8% 95.9%;
       --color-accent: 173 80% 40%;        /* verde/turquesa */
       --color-muted: 240 4.8% 95.9%;
       --color-muted-foreground: 240 3.8% 46.1%;
       --color-border: 240 5.9% 90%;
       --color-destructive: 0 84% 60%;
       --color-success: 142 71% 45%;
     }
     .dark {
       --color-background: 240 10% 3.9%;
       --color-foreground: 0 0% 98%;
       --color-primary: 262 83% 68%;
       --color-primary-foreground: 0 0% 100%;
       --color-secondary: 240 3.7% 15.9%;
       --color-accent: 173 80% 50%;
       --color-muted: 240 3.7% 15.9%;
       --color-muted-foreground: 240 5% 64.9%;
       --color-border: 240 3.7% 15.9%;
       --color-destructive: 0 62% 50%;
       --color-success: 142 71% 55%;
     }
   }
   ```

   Luego mapear esas variables en tailwind.config.ts:

   ```ts
   // tailwind.config.ts
   theme: {
     extend: {
       colors: {
         background: "hsl(var(--color-background))",
         foreground: "hsl(var(--color-foreground))",
         primary: {
           DEFAULT: "hsl(var(--color-primary))",
           foreground: "hsl(var(--color-primary-foreground))",
         },
         secondary: "hsl(var(--color-secondary))",
         accent: "hsl(var(--color-accent))",
         muted: {
           DEFAULT: "hsl(var(--color-muted))",
           foreground: "hsl(var(--color-muted-foreground))",
         },
         border: "hsl(var(--color-border))",
         destructive: "hsl(var(--color-destructive))",
         success: "hsl(var(--color-success))",
       },
     },
   },
   ```

   Así en todo el código se usa `bg-primary`, `text-foreground`,
   `border-border`, etc., y para cambiar toda la paleta solo se
   modifican las variables CSS en un solo archivo.

4. Crear el WalletProvider como Client Component ("use client") con:
   - ConnectionProvider apuntando a Devnet
   - WalletProvider con array vacío (auto-detect Phantom/Solflare)
   - WalletModalProvider
   - Import de "@solana/wallet-adapter-react-ui/styles.css"
5. Crear un archivo `.env.example` en la raíz del proyecto con todas las
   variables de entorno necesarias, documentadas con comentarios.
   También crear el `.env.local` (que va en .gitignore) con los mismos
   valores para desarrollo. Las variables deben ser:

   ```env
   # ===== Solana =====
   # Red: mainnet-beta | devnet | testnet
   NEXT_PUBLIC_SOLANA_NETWORK=devnet

   # RPC endpoint (usar Devnet por defecto; en producción usar un RPC privado)
   # Opciones gratuitas: https://api.devnet.solana.com
   # Opciones premium: Helius, Alchemy, QuickNode
   NEXT_PUBLIC_SOLANA_RPC_URL=https://api.devnet.solana.com

   # Program ID de tu programa Solana deployado
   NEXT_PUBLIC_PROGRAM_ID=

   # ===== App =====
   # URL base de la app (para metadatos, OG images, etc.)
   NEXT_PUBLIC_APP_URL=http://localhost:3000

   # Nombre del proyecto (se usa en metadata y UI)
   NEXT_PUBLIC_APP_NAME=Mi dApp

   # ===== APIs externas (si aplica) =====
   # Clave de API para servicios de terceros (NO exponer al cliente)
   # API_SECRET_KEY=
   ```

   Importante:
   - Las variables con prefijo NEXT_PUBLIC_ se exponen al navegador.
   - Las variables SIN ese prefijo solo están disponibles en el servidor.
   - Usar NEXT_PUBLIC_SOLANA_RPC_URL en el WalletProvider en lugar de
     hardcodear el endpoint.
   - Agregar `.env.local` al `.gitignore` (Next.js ya lo hace por defecto).

6. Envolver el root layout (src/app/layout.tsx) con el WalletProvider.
7. Crear un WalletButton con dynamic import (ssr: false) para evitar
   errores de hydration.
8. Verificar que `npm run dev` levanta sin errores y el botón conecta.

### Fase 2 — Funcionalidad core

1. Crear la estructura de carpetas **basada en features** (no por tipo):
   - src/features/[feature]/components/ → componentes propios de esa feature
   - src/features/[feature]/hooks/ → hooks propios de esa feature
   - src/features/[feature]/validators/ → schemas zod de esa feature
   - src/features/[feature]/types.ts → tipos de esa feature
   - src/features/[feature]/index.ts → barrel export
   - src/shared/components/ui/ → componentes genéricos reutilizables (Button, Card, Modal)
   - src/shared/hooks/ → hooks compartidos (useProgram, useSolanaBalance)
   - src/shared/lib/ → constants.ts, idl.json, utils
   - src/shared/providers/ → WalletProvider
   - src/types/ → tipos globales

   Regla: si algo es de UNA sola feature → va en features/[nombre]/.
   Si lo usan 2+ features → va en shared/.

   Ejemplo para una dApp con auth y listings:
   ```
   src/
   ├── app/
   │   ├── layout.tsx
   │   ├── page.tsx
   │   └── dashboard/page.tsx
   ├── features/
   │   ├── auth/
   │   │   ├── components/WalletButton.tsx
   │   │   ├── hooks/useAuth.ts
   │   │   └── index.ts
   │   └── listings/
   │       ├── components/CreateListingForm.tsx
   │       ├── components/ListingCard.tsx
   │       ├── hooks/useListings.ts
   │       ├── validators/listing.schema.ts
   │       ├── types.ts
   │       └── index.ts
   ├── shared/
   │   ├── components/ui/
   │   ├── hooks/useProgram.ts
   │   ├── lib/constants.ts
   │   └── providers/WalletProvider.tsx
   └── types/
   ```

2. Definir schemas de Zod en src/lib/validators.ts para cada formulario.
   Los campos que necesita mi dApp son: [DESCRIBÍ LOS CAMPOS DE TU FORMULARIO]

3. Crear formularios con React Hook Form + zodResolver que:
   - Validen en tiempo real con mensajes en español
   - Muestren estados de loading mientras se envía la TX
   - Bloqueen el submit si la wallet no está conectada
   - Llamen al programa Solana on-chain al hacer submit

4. Crear el hook useProgram.ts que:
   - Use useConnection y useWallet del wallet adapter
   - Instancie AnchorProvider y Program con el IDL
   - Exponga el program listo para llamar methods

5. Implementar las páginas principales:
   [LISTÁ LAS PÁGINAS QUE NECESITÁS — ejemplo:]
   - / → Landing con hero, descripción del proyecto y botón de wallet
   - /dashboard → Panel principal post-conexión con formulario y datos
   - /history → Historial de transacciones del usuario

### Fase 3 — Polish y deploy

1. Agregar feedback visual:
   - Toast de éxito/error en cada transacción (sonner)
   - Loading spinners mientras se confirma la TX
   - Estado vacío cuando no hay datos
2. Responsive: que funcione bien en mobile.
3. Deploy a Vercel con `npx vercel --prod`.
4. Verificar que la URL desplegada conecta wallet y envía TX en Devnet.

## RESTRICCIONES IMPORTANTES

- TODO componente que use hooks de wallet o del navegador DEBE tener "use client".
- El WalletMultiButton DEBE importarse con dynamic(..., { ssr: false }).
- El repo de GitHub DEBE ser PÚBLICO (si está privado = descalificación).
- Usar wallet de desarrollo (burner wallet), NUNCA wallet personal.
- El programa Solana DEBE estar integrado realmente (no mockups).
- Apuntar siempre a Devnet, nunca a Mainnet durante desarrollo.

## ENTREGABLES DEL HACKATHON (no olvidar)

- [ ] Repo GitHub público con README.md que incluya diagrama Mermaid
- [ ] App desplegada en Vercel, funcional y conectando wallet
- [ ] Programa Solana deployado en Devnet e integrado con el frontend
- [ ] Video demo ≤ 3 minutos
- [ ] Logo + banner + screenshots para el formulario de entrega

## OUTPUT ESPERADO

Dame primero un plan paso a paso con estimación de tiempo para cada fase.
Después empezá a implementar fase por fase, mostrándome el código completo
de cada archivo. No saltes archivos — necesito todo el código listo para
copiar y que funcione.
```

---

## 🔧 Variantes Rápidas

### Si ya tenés el programa Anchor listo, agregá esto al prompt:

```
Mi programa Anchor ya está deployado en Devnet.
- Program ID: [TU_PROGRAM_ID]
- IDL está en: ./target/idl/[nombre].json
- Las instrucciones disponibles son:
  - initialize(name: string, amount: u64)
  - update(new_name: string)
  - delete()
- Las cuentas PDA se derivan con seeds: [user_pubkey, "item"]

Creá los hooks y formularios que llamen a estas instrucciones específicas.
```

### Si querés integrar un sponsor específico:

```
Además, necesito integrar el SDK de [NOMBRE_SPONSOR] para calificar en su track.
El paquete npm es [PAQUETE] y necesito usarlo para [QUÉ FUNCIONALIDAD].
Indicá en el código con un comentario "// INTEGRACIÓN [SPONSOR]" la línea
exacta donde está implementado (es requisito del hackathon).
```

### Si querés que también genere el programa Solana:

```
No tengo programa Solana todavía. Necesito que también generes un programa
Anchor básico que haga [DESCRIBÍ QUÉ DEBE HACER ON-CHAIN].
Incluí:
- El código Rust del programa (lib.rs)
- Los comandos para compilar y deployar (anchor build && anchor deploy)
- El IDL generado integrado en el frontend
```

---

> [!TIP]
> **Tip para el hackathon:** Usá el comando `/plan` en Antigravity antes de pegar este prompt — te va a generar un plan detallado paso a paso que podés aprobar antes de que empiece a codear.
