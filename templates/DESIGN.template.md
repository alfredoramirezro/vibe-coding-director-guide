# [NOMBRE_DEL_PROYECTO] — DESIGN.md (FUENTE DE LA VERDAD VISUAL)
> **Contrato Visual Inmutable y Sistema de Tokens de Diseño**  
> *REGLA DE ORO: Ningún agente puede alucinar estilos, bordes arbitrarios ni paletas improvisadas. Toda interfaz debe obedecer estrictamente este documento.*

---

## 1. Principios Rectores de Interfaz (Anti-Slop Mandate)
1. **Mandato Zero-Popup [P1]:** Prohibido el uso de modales flotantes (`<Dialog>`, `<Modal>`) para flujos educativos, glosarios o formularios densos. Toda vista de lectura profunda es una subpágina dedicada con URL compartible, scroll nativo y botón `Volver`.
2. **Gráficos 100% SVG Inline [P2]:** Cero hotlinking a Unsplash, Pexels o librerías de stock. Todos los diagramas, iconos e ilustraciones son `<svg>` inline con variables CSS (`currentColor`).
3. **WCAG 2.1/2.2 AA/AAA [P1]:** Contraste de texto mínimo 4.5:1 (AA) y 7:1 en estados críticos (AAA). Indicador de foco visible (`:focus-visible`) en todos los controles interactivos.

---

## 2. Paleta Semántica de Colores (Tokens)
Definición de tokens CSS semánticos:

| Token | Valor Hex / HSL | Uso Obligatorio |
|---|---|---|
| `--background` | `#08090C` | Fondo raíz oscuro profundo |
| `--surface` | `#0E1117` | Fondo de tarjetas, paneles y contenedores |
| `--surface-elevated` | `#161B22` | Tarjetas con interacción o estados hover |
| `--border` | `#1F242D` | Bordes sutiles y divisores estructurales |
| `--foreground` | `#F3F4F6` | Texto principal de alto contraste (>7:1) |
| `--foreground-muted` | `#9CA3AF` | Texto secundario y etiquetas |
| `--accent-emerald` | `#10B981` | Estados de éxito, pruebas en verde, confirmación |
| `--accent-amber` | `#F59E0B` | Advertencias, límites, atención requerida |
| `--accent-crimson` | `#EF4444` | Errores, bloqueos P0, acciones destructivas |
| `--accent-sky` | `#0EA5E9` | Enlaces informativos y badges de contexto |

---

## 3. Tipografía y Escala
* **Fuente Monospaciada:** `JetBrains Mono`, `Fira Code`, `ui-monospace` (códigos, números, logs de terminal, badges de versión).
* **Fuente de Lectura / UI:** `Inter`, `system-ui`, `sans-serif` (legibilidad limpia, antialiased).
* **Jerarquía Estricta:**
  - `h1`: 1 único por página (título principal).
  - `h2`: Secciones principales (`border-b border-border pb-2`).
  - `h3`: Módulos o tarjetas individuales.
  - `p` / `span`: Texto de cuerpo con `line-height: 1.6` para facilitar lectura.

---

## 4. Componentes y Patrones UI Permitidos
* **Botones:**
  - Primario: Fondo contrastante (`bg-foreground text-background font-semibold hover:opacity-90 transition`).
  - Secundario: Borde sutil (`border border-border text-foreground hover:bg-surface-elevated`).
  - Peligro: Acento carmesí (`bg-accent-crimson/10 text-accent-crimson border border-accent-crimson/20`).
* **Estados Vacíos (*Empty-State First*):**
  - Todo panel o tabla debe programar primero el estado de 0 elementos: ilustración SVG sobria + texto explicativo + botón de acción primario.
* **Badges y Etiquetas:**
  - Tipografía monospace compacta (`text-xs font-mono px-2 py-0.5 rounded`).
