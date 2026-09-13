# Guía de Campo para Directores de Plataformas de Vibe Coding (IVC-OS)
> **El estándar de ingeniería, gobernanza, calidad y tracción para liderar desarrollo de software asistido por IA sin caer en el *Prompt-and-Pray*.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Production Ready](https://img.shields.io/badge/Status-Production%20Ready-success.svg)](#)
[![Vibe Coding Standard](https://img.shields.io/badge/Standard-IVC--OS%20v2.0-blue.svg)](file:///IVC-OS/IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md)
[![Language: Spanish](https://img.shields.io/badge/Language-Spanish%20(Universal)-green.svg)](#)

> [!NOTE]
> **Aviso de Alcance y Desacoplamiento de Repositorios:**  
> Este repositorio está dedicado **exclusivamente al marco metodológico, directivas normativas, plantillas y guía de campo de dirección (`IVC-OS Field Guide`)**.  
> La implementación del software y la plataforma web oficial se encuentran en: **[OrkestradOS en GitHub](https://github.com/alfredoramirezro/OrkestradOS)**.

---

## 🌟 ¿Qué es este repositorio?

La mayoría de los desarrolladores y fundadores que usan herramientas como **Cursor, Claude Code, Copilot, Antigravity o Devin** caen en el vicio operativo del **"Prompt-and-Pray"**: escribir instrucciones en lenguaje natural ambiguo, aceptar el código resultante a ciegas y rezar para que funcione en producción.

El resultado suele ser catastrófico: **deuda técnica masiva, alucinaciones silenciosas, componentes que se rompen en móviles, quema indiscriminada de tokens y "amnesia del proyecto" por hiperfocarse en detalles del MVP**.

Este repositorio contiene la **Guía de Campo Oficial para Directores de Plataformas de Vibe Coding (`IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md`)**: un manual normativo, cronológico y táctico que enseña a los líderes técnicos y fundadores cómo dirigir a los agentes de IA con el mismo rigor que un Director de Orquesta y un Auditor Fiduciario de Software.

---

## 🧭 Estructura del Ciclo de Vida (Fases 0 a 5)

La guía está articulada cronológicamente cubriendo todo el ciclo de vida del software, clasificada por niveles de prioridad (`[P0]` Crítico/Bloqueante, `[P1]` Alta Calidad, `[P2]` Excelencia y Tracción):

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                CICLO DE VIDA IVC-OS                                    │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ FASE 0: Incepción, Contratos, Soberanía y Diseño Previo (Día 0)                        │
│         - Intent Framing, Offer Builder y Frontera Negativa (qué NO construir).        │
│         - Gatillo de 2 Personas: Detección del punto de quiebre de soluciones manuales.│
│         - Garantía de Cero-Entrenamiento (Zero-Training Shield en contratos).          │
│         - Spec-Driven Development (SDD): Congelar schemas Zod/OpenAPI antes de codificar│
│         - Anti-God-Files: Archivos modulares estrictamente < 250 líneas.               │
│         - Trinidad de Contratos: NORTH_STAR (Catedral), MVP_BOUNDARY y DESIGN.md.      │
│         - Bóveda FEATURE_PARKING_LOT: Desvío de sugerencias de la IA para ahorrar tokens.│
│                                                                                        │
│ FASE 1: Construcción Confinada y Desarrollo Agéntico en Arnés (Día 1)                 │
│         - Sandbox Docker efímero con bloqueo de red saliente (Egress Guardrails).      │
│         - Disposable Fleet: Agentes desechables de un solo uso para evitar memoria sucia│
│         - TDD Agéntico con Evidencia Literal de Terminal (Verification Before Complete)│
│         - Revisión Adversarial en Contexto Limpio (Regla de No Self-Approval).         │
│         - Micro-Diffs atómicos (< 200 líneas modificadas por commit).                  │
│                                                                                        │
│ FASE 2: Auditoría Avanzada de Calidad, Veracidad y Accesibilidad (Día 2)               │
│         - El "Bug-Sweep" en 5 capas estructuradas (Invariantes, Concurrencia, Fuzzing).│
│         - Las 7 Reglas de Oro de Veracidad (Cero testimonios falsos, Empty-State first)│
│         - Estándar Mundial de Accesibilidad (WCAG 2.1/2.2 AA/AAA, Contraste >4.5:1/7:1)│
│         - Mandato Zero-Popup: Subpáginas con URL limpia y scroll en vez de modales.    │
│         - Arquitectura RBAC: Superadmin con suplantación auditada, Tenant Admin, User. │
│                                                                                        │
│ FASE 3: Validación de Tracción, Mercado y Presentación Comercial (Día 3)               │
│         - Graceful Payment Stubbing: Checkout beta con descuento fundador sin tarjeta. │
│         - Decks en HTML 16:9 autocontenidos: Investor Deck (10 slides), Founding       │
│           Customers Deck (6 slides) y Solución B2B High-Ticket $10k-$25k (8 slides).   │
│         - Doble Motor Comercial: Micro-SaaS recurrente vs Soluciones a la medida.      │
│         - Modo Sombra (Shadow Mode): Evaluación ciega del 10% de tráfico para IA nueva.│
│                                                                                        │
│ FASE 4: Pre-Lanzamiento, Blindaje y Despliegue Go-Live (Día 4)                         │
│         - Checklist Pre-Lanzamiento: 10 Dimensiones de Despegue (10/10 PASS = GO).     │
│         - Migraciones Zero-Downtime: Patrón Expand & Contract en 3 fases.              │
│         - Dark Launching: Liberación escalonada detrás de Feature Flags booleanas.     │
│         - Optimización GEO, SEO y SEM: Manifiestos llms.txt, Schema.org y LCP < 2.0s.  │
│                                                                                        │
│ FASE 5: Operación en Vivo, Resiliencia y Cumplimiento Fiscal (Día 5+)                  │
│         - Global Kill-Switch: Botón de desconexión de emergencia de agentes (< 500 ms).│
│         - Aislamiento Multi-Tenant Estricto con Row-Level Security (RLS) en PostgreSQL.│
│         - Watchdog Bot a Telegram/Discord para alertas críticas en tiempo real.        │
│         - Exportación Total en 1 Clic (.ZIP) con cero dependencia cautiva.             │
│         - Statutory Tax Hold: Separación entre derecho al olvido y retención contable  │
│           por 5 años conforme al Art. 30 del CFF / normativas fiscales internacionales.│
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 📥 Descarga y Lectura Inmediata

Puedes leer o descargar la guía en los siguientes formatos:

1. **Lectura Directa en GitHub:** Abre el archivo [`IVC-OS/IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md`](IVC-OS/IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md).
2. **Cheat Sheet Rápido de Prompts (Markdown):** Abre [`docs/GUIA_OPERATIVA_CHAT_ANTIGRAVITY.md`](docs/GUIA_OPERATIVA_CHAT_ANTIGRAVITY.md) para copiar y pegar comandos directos en el chat.
3. **Cheat Sheet Interactivo e Imprimible (HTML / PDF):** Abre [`docs/cheatsheet.html`](docs/cheatsheet.html) con botones de 1 clic para copiar y soporte de exportación a PDF.
4. **Descarga en 1 Clic (Markdown Crudo):**  
   Haz clic derecho y selecciona *Guardar como...* en [Descargar Guía Completa (.md)](https://raw.githubusercontent.com/alfredoramirezro/vibe-coding-director-guide/main/IVC-OS/IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md).
5. **Clonar el Repositorio:**
   ```bash
   git clone https://github.com/alfredoramirezro/vibe-coding-director-guide.git
   cd vibe-coding-director-guide
   ```

---

## 🚀 Cómo Usar esta Guía con tus Herramientas de IA

### En Antigravity (`GEMINI.md`)
Coloca el archivo maestro [`GEMINI.md`](GEMINI.md) en la raíz de tu workspace (ej. `c:/.Proyectos/GEMINI.md`). Antigravity cargará jerárquicamente las reglas en todas las sesiones y subproyectos:
* **Anti-God-Files:** Veto automático a archivos mayores a 250 líneas.
* **Bozal a la IA:** Las sugerencias de features accesorias se desvían a `FEATURE_PARKING_LOT.md`.
* **Zero-Popup:** Obliga a crear subpáginas dedicadas con scroll en lugar de modales flotantes.
* **No Self-Approval:** Exige revisión adversarial con subagentes antes del commit.
* **Evidencia en Terminal:** No acepta respuestas que no incluyan la ejecución de pruebas.

Consulta el catálogo de comandos en [`docs/GUIA_OPERATIVA_CHAT_ANTIGRAVITY.md`](docs/GUIA_OPERATIVA_CHAT_ANTIGRAVITY.md).

### En Cursor (`.cursorrules`)
Copia el archivo `IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md` en la raíz de tu proyecto o referencia las directivas clave en tu archivo `.cursorrules`:
```markdown
# Directivas de Vibe Coding
Sigue estrictamente el estándar IVC-OS (IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md):
- Ninguna feature sin especificación previa en SPEC.md.
- Archivos estrictamente modulares de menos de 250 líneas.
- No sugieras features extras: anótalas en FEATURE_PARKING_LOT.md.
- Entrega siempre la salida literal de terminal con pruebas en verde antes de dar por terminada la tarea.
```

### En Claude Code / Copilot / Devin
Coloca la guía en tu carpeta de skills o referénciala directamente en tu sesión:
```bash
@IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md
Actúa como el Director Técnico bajo este estándar para planificar la siguiente épica.
```

---

## 📁 Plantillas Listas para Usar (Templates Incluidos)

En la carpeta [`templates/`](templates/) encontrarás las 5 plantillas oficiales para arrancar tus proyectos sin fricción bajo la Trinidad de Contratos:

| Archivo | Propósito |
|---|---|
| [`templates/NORTH_STAR.template.md`](templates/NORTH_STAR.template.md) | La Catedral: mapa de visión completa a 12-24 meses. |
| [`templates/MVP_BOUNDARY.template.md`](templates/MVP_BOUNDARY.template.md) | El Primer Ladrillo: delimitación del MVP con Gatillo de 2 Personas y Frontera Negativa [P0]. |
| [`templates/DESIGN.template.md`](templates/DESIGN.template.md) | Tokens UI & Anti-Slop: fuente de la verdad visual inmutable y mandato Zero-Popup. |
| [`templates/FEATURE_PARKING_LOT.template.md`](templates/FEATURE_PARKING_LOT.template.md) | La Bóveda de Ideas: desvío de sugerencias para ahorrar tokens. |
| [`templates/SESSION_PRIMER.template.md`](templates/SESSION_PRIMER.template.md) | Paquete de contexto limpio y bozal anti-feature creep para el agente. |

---

## 🤝 Cómo Compartir esto con tus Colegas

Si deseas compartir este estándar en tus grupos de WhatsApp, Telegram, LinkedIn o Slack con colegas fundadores y desarrolladores, puedes usar este mensaje de presentación:

```text
🚀 Colegas desarrolladores y fundadores:

Si están programando con IA (Cursor, Claude Code, Copilot, Antigravity), seguro han sufrido los problemas del "Prompt-and-Pray": código espagueti enredado, agentes que queman tokens sugiriendo cosas que nadie pidió, alucinaciones y la clásica "amnesia del proyecto" por hiperfocarse en el MVP.

Armamos una Guía de Campo completa y de acceso abierto para quienes dirigen plataformas y proyectos de Vibe Coding:

📘 IVC-OS: Guía de Campo para Directores de Vibe Coding
👉 https://github.com/alfredoramirezro/vibe-coding-director-guide

Incluye:
✅ Spec-Driven Development (congelar contratos antes de codificar).
✅ Bóveda Parking Lot (para que la IA no te queme presupuesto en tokens).
✅ Modularización estricta (veto a archivos mayores a 250 líneas).
✅ Checklist Go-Live de 10 dimensiones antes de abrir a usuarios.
✅ Procedimiento de cobro beta diferido y presentaciones 16:9 en HTML.
✅ Plantillas de inicio rápido (North Star, MVP Boundary, Parking Lot).

¡Espero les sirva para elevar el nivel de sus proyectos con IA!
```

---

## 📄 Licencia
Este proyecto está licenciado bajo la **Licencia MIT**, lo que permite su uso comercial, modificación y distribución libre sin restricciones.
