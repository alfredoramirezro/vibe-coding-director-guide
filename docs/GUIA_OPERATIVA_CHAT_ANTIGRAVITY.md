# 🧭 GUÍA DE CAMPO RÁPIDA: CÓMO USAR E INVOCAR IVC-OS EN EL CHAT DE ANTIGRAVITY
> **Cheat Sheet de Bolsillo para Directores de Vibe Coding**  
> *Versión 2.0 — Ecosistema Antigravity & IVC-OS*  
> *Ruta en el repositorio:* `docs/GUIA_OPERATIVA_CHAT_ANTIGRAVITY.md`

---

## ⚡ Resumen Ejecutivo: Las 4 Formas de Llamar al Sistema

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               MODOS DE INVOCACIÓN                                      │
├────────────────────────────────┬───────────────────────────────────────────────────────┤
│ 1. INHERENTE (AUTOMÁTICO)      │ Ya opera de fondo en cada chat gracias a `GEMINI.md`. │
│ 2. INICIALIZAR PLANTILLAS      │ Pide copiar y adaptar las plantillas canónicas.       │
│ 3. SKILL GLOBAL                │ Invoca `ivc-os-field-guide` para auditorías o triaje. │
│ 4. SUBAGENTE AUDITOR           │ Delega la revisión adversarial a `code-reviewer`.     │
└────────────────────────────────┴───────────────────────────────────────────────────────┘
```

---

## 📋 Catálogo de Prompts Copiables para el Chat de Cada App

### 1. Para Arrancar un Proyecto Nuevo o Módulo
Copia y pega este prompt al abrir el chat en la carpeta de tu aplicación:

```text
Inicializa la estructura IVC-OS en este proyecto.
Copia y adapta las plantillas de `templates/` aquí (NORTH_STAR, MVP_BOUNDARY y FEATURE_PARKING_LOT).
Pregúntame únicamente por la Hipótesis Central de Valor y la Frontera Negativa (lo que NO haremos en esta versión).
```

---

### 2. Para Inyectar el Paquete de Inicio Limpio (Session Primer)
Al iniciar una nueva sesión de programación en una tarea o componente específico:

```text
Usa el skill `ivc-os-field-guide` y arranca con un SESSION_PRIMER para esta tarea.
Recuerda las restricciones mandatorias:
- Archivos modulares estrictamente < 250 líneas.
- Spec-Driven First: muéstrame los schemas antes de codificar.
- Bozal a la IA: no sugieras librerías ni features extras; envíalas a FEATURE_PARKING_LOT.md.
```

---

### 3. Para Triaje de Funcionalidades (Evitar Quema de Tokens)
Cuando tengas una lista de ideas o solicitudes y no sepas qué entra en el MVP:

```text
Aplica la Matriz de Triaje de Características de IVC-OS a estas ideas:
[Pega aquí tu lista de ideas]

Clasifícalas con la pregunta ácida en:
1. Essential-to-Have (Entra al MVP actual).
2. Good-to-Have (Fase 2 Crecimiento / Workaround manual).
3. Nice-to-Have (Fase 3 Deleite).
4. Wish-to-Have (A FEATURE_PARKING_LOT.md con 0 código generado).
```

---

### 4. Para Auditoría de Calidad ("Bug-Sweep" en 5 Capas)
Antes de aceptar un cambio o dar por cerrado un componente:

```text
Ejecuta el Bug-Sweep en 5 capas de IVC-OS sobre este archivo/módulo:
- Capa 1: Invariantes y tipos (cero 'any', manejo exhaustivo de null/undefined).
- Capa 2: Concurrencia y debounce en envíos.
- Capa 3: Fuzzing y valores límite (vacíos, caracteres raros, números negativos).
- Capa 4: Regresión y pruebas en verde.
- Capa 5: Seguridad (cero secretos, sanitización contra XSS e inyecciones).
```

---

### 5. Para Auditoría de UI, Accesibilidad y Mandato Zero-Popup
Cuando construyas o revises pantallas de usuario:

```text
Audita esta pantalla bajo las directivas sensoriales y de interfaz de IVC-OS:
1. Mandato Zero-Popup: verifica que no existan modales flotantes (<Dialog>) y que todo flujo denso sea una subpágina dedicada con URL limpia y scroll vertical.
2. Accesibilidad WCAG 2.1 AA/AAA: contraste > 7:1, outline de foco visible, áreas táctiles de al menos 44x44px y navegación 100% por teclado.
3. Anti-Slop: empty-states first, cero testimonios inventados y cero contadores simulados.
4. Gráficos: ilustraciones vectoriales inline SVG nativas (cero imágenes de stock externas).
```

---

### 6. Para Revisión Adversarial (Regla de No Self-Approval)
Antes de integrar código a la rama principal:

```text
Aplica la regla de No Self-Approval de IVC-OS.
Delega una revisión adversarial al subagente `code-reviewer` en contexto limpio para verificar arquitectura, seguridad, modularidad (<250 líneas) y evidencia de pruebas antes del commit.
```

---

### 7. Checklist Pre-Lanzamiento de 10 Dimensiones (Go-Live Gate)
Cuando la aplicación esté lista para desplegarse a producción:

```text
Aplica el Checklist Pre-Lanzamiento de 10 Dimensiones de la Fase 4 de IVC-OS.
Evalúa 1 a 1:
1. Build (cero errores TS/Linter).
2. Tests (suite en verde con evidencia literal).
3. Security (auditoría de paquetes).
4. Secrets (cero API keys en código).
5. Performance (Core Web Vitals LCP < 2.0s).
6. Accessibility (auditoría axe/Lighthouse sin violaciones AA).
7. Legal (Aviso de Privacidad y Términos enlazados en footer).
8. Error Monitoring (capturador de excepciones configurado).
9. Database Backup (estrategia de respaldo verificada).
10. SEO/GEO (robots.txt, sitemap.xml, llms.txt y metadatos OpenGraph).

¿Tenemos el 10/10 PASS para autorizar el GO?
```

---

## 🤖 Comportamientos Automáticos (Lo que Antigravity ya hace solo)

Al configurar [`GEMINI.md`](../GEMINI.md) en la raíz de tu proyecto o workspace, el agente aplica automáticamente:

| Directiva | Qué hace el agente automáticamente |
| :--- | :--- |
| **Anti-God-Files** | Si un componente supera las **250-300 líneas**, lo descompone en subcomponentes, hooks o utilitarios sin que se lo pidas. |
| **Bozal a la IA** | No improvisa funcionalidades accesorias. Cualquier sugerencia no pedida la envía a `FEATURE_PARKING_LOT.md`. |
| **Verification Before Completion** | No afirma que el código funciona sin ejecutar pruebas y reportar la salida de terminal. |
| **Zero-Popup** | Construye subpáginas dedicadas en lugar de modales flotantes que desbordan pantallas móviles o laptops. |
| **Soberanía y Permisos** | Respeta la lista blanca de licencias permisivas (MIT, Apache 2.0) y el Zero-Training Shield. |
