# IVC-OS Web App Implementation Plan
> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Construir la aplicación web completa de IVC-OS (Intelligent Vibe Coding Operating System), una plataforma SaaS de cabina de control y gobernanza que materializa las directivas del Director de Vibe Coding (Fases 0 a 5, Spec-Driven Development, Arnés de verificación, Anti-Slop, Decks 16:9 en HTML, y RBAC con retención fiscal).

**Architecture:** Aplicación web fullstack en Next.js (App Router) + TypeScript + Tailwind CSS, desarrollada bajo el patrón "Zero-Popup" (subpáginas dedicadas en lugar de modales), "Local-First" con persistencia de borradores, ilustraciones SVG nativas en código (cero imágenes de stock) y diseño accesible WCAG AA/AAA. Diseñada para operar en una ruta y repositorio independiente (`ivc-os-platform`).

**Tech Stack:** Next.js 14+ (App Router), TypeScript, Tailwind CSS, Zod (validación de contratos), Lucide/Custom SVGs, PrismJS / Shiki (render de código y diffs), PostgreSQL con Row-Level Security (o SQLite local para modo offline inicial), Vitest / React Testing Library.

**Spec:** [`C:\.Proyectos\Vibecoder\IVC-OS\IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md`](file:///C:/.Proyectos/Vibecoder/IVC-OS/IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md) y [`C:\.Proyectos\Vibecoder\docs\superpowers\specs\2026-09-11-ivc-os-director-field-guide-design.md`](file:///C:/.Proyectos/Vibecoder/docs/superpowers/specs/2026-09-11-ivc-os-director-field-guide-design.md).

## Global Constraints
* **Ruta de Despliegue/Respaldo:** `C:\.Proyectos\Vibecoder\ivc-os-platform` (repositorio Git independiente al de la guía).
* **Idioma:** Español claro, profesional y cercano para el mercado hispano/mexicano (cero anglicismos innecesarios).
* **Tamaño Máximo de Archivo:** Máximo 250 líneas por componente o archivo de código (Anti-God-Files).
* **Diseño Sensorial:** 100% ilustraciones vectoriales SVG en código; prohibidas imágenes de stock o enlaces externos.
* **Mandato Zero-Popup:** Ninguna ventana modal superpuesta; navegación por subpáginas con URL limpia y scroll nativo.
* **Accesibilidad:** WCAG AA/AAA (contraste > 4.5:1 / 7:1, navegación completa por teclado con `:focus-visible` y skip-link).
* **Empty-State First:** Toda pantalla se diseña primero para el usuario con 0 proyectos, sin datos simulados falsos.

---

## File Structure & Module Map (`ivc-os-platform/`)

```
ivc-os-platform/
├── package.json
├── tsconfig.json
├── tailwind.config.ts
├── next.config.mjs
├── public/
│   ├── llms.txt                 # Manifiesto GEO para crawlers de IA
│   ├── ai.txt                   # Permisos de scraping
│   └── favicon.ico
├── src/
│   ├── app/
│   │   ├── layout.tsx           # Layout global con skip-link, fuentes Syne/JetBrains Mono y tema dark
│   │   ├── page.tsx             # Landing / Home con Proof of Mechanism interactivo
│   │   ├── como-funciona/       # Subpágina didáctica del flujo en 3 pasos
│   │   │   └── page.tsx
│   │   ├── glosario/            # Diccionario accesible de términos
│   │   │   └── page.tsx
│   │   ├── proyectos/           # Workspace central
│   │   │   ├── page.tsx         # Listado de proyectos (Empty-state first)
│   │   │   ├── nuevo/           # Incepción guiada con frontera negativa
│   │   │   │   └── page.tsx
│   │   │   └── [id]/
│   │   │       ├── layout.tsx   # Subnavegador del proyecto
│   │   │       ├── page.tsx     # Resumen del proyecto y estado de fases
│   │   │       ├── spec/        # Gestor SDD: North Star, Boundary, Parking Lot
│   │   │       │   └── page.tsx
│   │   │       ├── arnes/       # Cabina de ejecución, TDD y micro-diffs
│   │   │       │   └── page.tsx
│   │   │       ├── auditoria/   # Bug-Sweep y Checklist Pre-Lanzamiento
│   │   │       │   └── page.tsx
│   │   │       └── decks/       # Generador de Decks 16:9 HTML (Investor / Clientes)
│   │   │           └── page.tsx
│   │   ├── checkout-beta/       # Checkout frictionless con descuento fundador
│   │   │   └── page.tsx
│   │   ├── admin-platform/      # Panel Superadmin aislado
│   │   │   ├── page.tsx         # Métricas globales y kill-switch
│   │   │   ├── suplantacion/    # Modo soporte auditado con banner
│   │   │   │   └── page.tsx
│   │   │   └── compliance-tax/  # Retención fiscal por 5 años (Art. 30 CFF)
│   │   │       └── page.tsx
│   │   └── api/
│   │       ├── proyectos/
│   │       ├── spec/
│   │       ├── decks/export/
│   │       └── backup/export/   # Exportación total en .ZIP
│   ├── components/
│   │   ├── ui/                  # Componentes base atómicos (< 150 líneas cada uno)
│   │   │   ├── Button.tsx
│   │   │   ├── Input.tsx
│   │   │   ├── Card.tsx
│   │   │   ├── Badge.tsx
│   │   │   └── SvgIcon.tsx      # Generador de SVG en código
│   │   ├── layout/
│   │   │   ├── Navbar.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── ImpersonationBanner.tsx
│   │   └── project/
│   │       ├── IntentForm.tsx   # Formulario con frontera negativa y auto-draft
│   │       ├── SpecViewer.tsx   # Visualizador de contratos Zod/OpenAPI
│   │       ├── DiffViewer.tsx   # Inspector de micro-diffs (< 200 líneas)
│   │       └── GoLiveChecklist.tsx # Auditoría interactiva de 10 dimensiones
│   ├── lib/
│   │   ├── contracts/           # Esquemas Zod inmutables
│   │   │   ├── project.ts
│   │   │   ├── spec.ts
│   │   │   └── audit.ts
│   │   ├── storage/
│   │   │   └── localDraft.ts    # Persistencia local-first (auto-draft)
│   │   └── decks/
│   │       └── htmlDeckGenerator.ts # Compilador de presentaciones 16:9 en 1 archivo HTML
│   └── tests/
│       ├── contracts.test.ts
│       ├── deckGenerator.test.ts
│       └── goLiveAudit.test.ts
```

---

## Tasks

### Task 1: Scaffolding del Proyecto Independiente (`ivc-os-platform`) y Configuración Base
**Files:**
- Create: `ivc-os-platform/package.json`
- Create: `ivc-os-platform/tsconfig.json`
- Create: `ivc-os-platform/tailwind.config.ts`
- Create: `ivc-os-platform/next.config.mjs`
- Create: `ivc-os-platform/src/app/layout.tsx`
- Create: `ivc-os-platform/src/app/globals.css`

**Interfaces:**
- Produces: Base Next.js 14 App Router con Tailwind CSS, tipografía dark-tech (Syne + JetBrains Mono), `:focus-visible` para accesibilidad y skip-link principal.

- [ ] **Step 1: Crear estructura de directorios e inicializar git en `ivc-os-platform`**
- [ ] **Step 2: Configurar `package.json` con dependencias mínimas requeridas (Next.js, React, Tailwind, Zod, Vitest)**
- [ ] **Step 3: Configurar variables CSS de contraste matemático (> 4.5:1 / 7:1) y estilos globales con accesibilidad**
- [ ] **Step 4: Verificar arranque y compilación con `npm run build`**
- [ ] **Step 5: Commit inicial del proyecto de la plataforma**

---

### Task 2: Contratos de Dominio Zod y Utilidades Local-First
**Files:**
- Create: `ivc-os-platform/src/lib/contracts/project.ts`
- Create: `ivc-os-platform/src/lib/contracts/spec.ts`
- Create: `ivc-os-platform/src/lib/storage/localDraft.ts`
- Test: `ivc-os-platform/src/tests/contracts.test.ts`

**Interfaces:**
- Produces: Esquemas fuertemente tipados para `Project`, `NorthStar`, `MVPBoundary`, `ParkingLotItem`, y funciones de guardado automático en `localStorage`.

- [ ] **Step 1: Escribir pruebas unitarias para esquemas Zod y validación de frontera negativa**
- [ ] **Step 2: Ejecutar pruebas y verificar fallo inicial**
- [ ] **Step 3: Implementar esquemas Zod (`project.ts`, `spec.ts`) con tipado estricto**
- [ ] **Step 4: Implementar utilería `localDraft.ts` para recuperación offline y auto-draft**
- [ ] **Step 5: Ejecutar pruebas con Vitest y confirmar paso en verde con log literal**
- [ ] **Step 6: Commit atómico**

---

### Task 3: Home & Subpáginas Didácticas ("Cero Fricción de Ventas")
**Files:**
- Create: `ivc-os-platform/src/app/page.tsx`
- Create: `ivc-os-platform/src/app/como-funciona/page.tsx`
- Create: `ivc-os-platform/src/app/glosario/page.tsx`
- Create: `ivc-os-platform/src/components/ui/SvgIcon.tsx`

**Interfaces:**
- Produces: Landing page con Proof of Mechanism interactivo (demostración en vivo, cero testimonios falsos), subpágina `/como-funciona` en 3 pasos, y subpágina `/glosario` con términos en español claro.

- [ ] **Step 1: Implementar componente de ilustraciones SVG nativas (`SvgIcon.tsx`) sin enlaces de stock**
- [ ] **Step 2: Construir la landing page con demostración interactiva de mecanismo (Proof of Mechanism)**
- [ ] **Step 3: Construir `/como-funciona` con el flujo en 3 pasos (Objetivo → Arnés → Software)**
- [ ] **Step 4: Construir `/glosario` con términos técnicos explicados en lenguaje sencillo**
- [ ] **Step 5: Verificar navegación por teclado y contraste visual WCAG AA**
- [ ] **Step 6: Commit atómico**

---

### Task 4: Módulo de Incepción de Proyectos & Frontera Negativa (Fase 0)
**Files:**
- Create: `ivc-os-platform/src/app/proyectos/page.tsx`
- Create: `ivc-os-platform/src/app/proyectos/nuevo/page.tsx`
- Create: `ivc-os-platform/src/components/project/IntentForm.tsx`

**Interfaces:**
- Consumes: `localDraft.ts`, `project.ts` (Zod).
- Produces: Pantalla de proyectos (Empty-State First) y formulario de incepción guiada que obliga al usuario a definir: Problema, Solución y **Lista Explícita de lo que NO hace el sistema (Frontera Negativa)**.

- [ ] **Step 1: Diseñar pantalla de Proyectos con Empty-State prioritario (cero tablas falsas)**
- [ ] **Step 2: Implementar `IntentForm.tsx` con autoguardado en tiempo real en `localStorage`**
- [ ] **Step 3: Añadir validación Zod que impida crear proyectos sin frontera negativa explícita**
- [ ] **Step 4: Probar flujo de creación y restauración ante recarga de pestaña**
- [ ] **Step 5: Commit atómico**

---

### Task 5: Gestor SDD: La Catedral, El Ladrillo y la Bóveda Parking Lot
**Files:**
- Create: `ivc-os-platform/src/app/proyectos/[id]/spec/page.tsx`
- Create: `ivc-os-platform/src/components/project/SpecViewer.tsx`

**Interfaces:**
- Produces: Interfaz de gestión del Doble Horizonte: pestaña `NORTH_STAR.md` (La Catedral), pestaña `MVP_BOUNDARY.md` (El Primer Ladrillo) y pestaña `FEATURE_PARKING_LOT.md` (Bóveda de Ideas con botón rápido para congelar sugerencias sin gastar tokens).

- [ ] **Step 1: Implementar vistas tabulares sin modales (Zero-Popup) para los 3 archivos de horizonte**
- [ ] **Step 2: Añadir botón "Enviar a Parking Lot" que registra ideas en 2 líneas**
- [ ] **Step 3: Añadir selector de triaje de características (Essential / Good / Nice / Wish)**
- [ ] **Step 4: Probar interactividad y renderizado markdown**
- [ ] **Step 5: Commit atómico**

---

### Task 6: Cabina de Arnés, TDD y Auditoría de Micro-Diffs (Fases 1 y 2)
**Files:**
- Create: `ivc-os-platform/src/app/proyectos/[id]/arnes/page.tsx`
- Create: `ivc-os-platform/src/components/project/DiffViewer.tsx`

**Interfaces:**
- Produces: Monitor de tareas agénticas con salida de consola literal (TDD), visor de diffs atómicos con alerta roja si supera 200 líneas, y botón de revisión adversarial independiente.

- [ ] **Step 1: Implementar visor de salida de terminal (emulando log de CLI con pruebas en verde)**
- [ ] **Step 2: Implementar `DiffViewer.tsx` con contador de líneas modificadas y bloqueo si > 200 líneas**
- [ ] **Step 3: Añadir compuerta de aprobación de dos pasos (No Self-Approval)**
- [ ] **Step 4: Commit atómico**

---

### Task 7: Checklist Pre-Lanzamiento (10 Dimensiones) y Pasarela Beta
**Files:**
- Create: `ivc-os-platform/src/app/proyectos/[id]/auditoria/page.tsx`
- Create: `ivc-os-platform/src/app/checkout-beta/page.tsx`
- Create: `ivc-os-platform/src/components/project/GoLiveChecklist.tsx`
- Test: `ivc-os-platform/src/tests/goLiveAudit.test.ts`

**Interfaces:**
- Produces: Auditoría interactiva con las 10 dimensiones críticas de Go-Live (10/10 para obtener veredicto GO), y pantalla de Checkout Beta con descuento fundador congelado en base de datos sin solicitar tarjeta bancaria.

- [ ] **Step 1: Escribir pruebas unitarias del evaluador de Go-Live (10/10 PASS = GO)**
- [ ] **Step 2: Implementar componente interactivo `GoLiveChecklist.tsx`**
- [ ] **Step 3: Implementar flujo de `checkout-beta` con captura de intención y activación de trial por 30 días**
- [ ] **Step 4: Ejecutar pruebas y confirmar paso en verde**
- [ ] **Step 5: Commit atómico**

---

### Task 8: Generador de Decks 16:9 en HTML Autocontenido
**Files:**
- Create: `ivc-os-platform/src/lib/decks/htmlDeckGenerator.ts`
- Create: `ivc-os-platform/src/app/proyectos/[id]/decks/page.tsx`
- Test: `ivc-os-platform/src/tests/deckGenerator.test.ts`

**Interfaces:**
- Produces: Generador que compila y descarga en 1 clic archivos HTML autónomos (`deck-investor.html` de 10 slides y `deck-founders.html` de 6 slides) con navegación por teclado y diseño widescreen 16:9.

- [ ] **Step 1: Escribir prueba unitaria que valida que el HTML generado sea 100% autocontenido (CSS inline, scripts de teclado embebidos)**
- [ ] **Step 2: Implementar plantillas dinámicas de 10 slides para inversionistas y 6 slides para clientes fundadores**
- [ ] **Step 3: Añadir interfaz de previsualización y botón de descarga directa `.html`**
- [ ] **Step 4: Ejecutar pruebas y validar generación**
- [ ] **Step 5: Commit atómico**

---

### Task 9: Panel Superadmin RBAC, Kill-Switch y Retención Fiscal
**Files:**
- Create: `ivc-os-platform/src/app/admin-platform/page.tsx`
- Create: `ivc-os-platform/src/app/admin-platform/suplantacion/page.tsx`
- Create: `ivc-os-platform/src/app/admin-platform/compliance-tax/page.tsx`
- Create: `ivc-os-platform/src/components/layout/ImpersonationBanner.tsx`

**Interfaces:**
- Produces: Panel de Superadmin con botón Kill-Switch de emergencia (< 500 ms), modo de suplantación de identidad para soporte con banner amarillo visible permanente y vista de cumplimiento fiscal para registros retenidos por 5 años (Art. 30 CFF).

- [ ] **Step 1: Implementar vista de `/admin-platform` con métricas globales y botón rojo Kill-Switch con confirmación de dos pasos**
- [ ] **Step 2: Implementar módulo de suplantación de soporte con `ImpersonationBanner.tsx` activo**
- [ ] **Step 3: Implementar `/compliance-tax` para auditar comprobantes fiscales retenidos con estatus `statutory_tax_hold`**
- [ ] **Step 4: Commit atómico**

---

### Task 10: Exportación en .ZIP (Zero Vendor Lock-In) y Manifiestos GEO/SEO
**Files:**
- Create: `ivc-os-platform/src/app/api/backup/export/route.ts`
- Create: `ivc-os-platform/public/llms.txt`
- Create: `ivc-os-platform/public/ai.txt`

**Interfaces:**
- Produces: Endpoint API que empaqueta en 1 clic todos los datos del proyecto en un archivo `.zip` descargable, y archivos de manifiesto GEO (`llms.txt`, `ai.txt`) para crawlers de IA.

- [ ] **Step 1: Implementar endpoint de exportación total en .ZIP (código, specs, SQL DDL, SVGs)**
- [ ] **Step 2: Configurar `llms.txt` y `ai.txt` en `/public/`**
- [ ] **Step 3: Validar descarga completa y verificar integridad del archivo .zip**
- [ ] **Step 4: Commit atómico**

---

## Verification & Pre-Flight Review
- Ejecutar suite de pruebas completa: `npm test`
- Ejecutar build de producción: `npm run build`
- Verificar navegación completa por teclado y accesibilidad con Lighthouse / axe.
