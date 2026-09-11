# DIRECTIVAS MAESTRAS DE INGENIERÍA Y GOBERNANZA AGÉNTICA (IVC-OS v2.0)
> **Constitución Operativa del Workspace**  
> *Aplica a todas las sesiones, proyectos, subproyectos y subagentes en este espacio de trabajo.*

---

## 0. Manifiesto y Marco Operativo Rector

En este workspace se erradica por completo el vicio operativo del **"Prompt-and-Pray"** (escribir prompts ambiguos, aceptar código a ciegas y rezar para que funcione). El usuario humano actúa como **Director de Orquesta, Arquitecto en Jefe y Auditor Fiduciario**, y la IA actúa como ejecutora técnica confinada:

1. **El Director compite en claridad de intención, rigor de fronteras y juicio de valor.**
2. **Ninguna línea de código de implementación se escribe sin una especificación formal previa congelada (SDD).**
3. **El agente que programa jamás aprueba su propio código (*Regla de No Self-Approval*).**
4. **La evidencia literal de terminal prevalece siempre sobre cualquier afirmación en lenguaje natural (*Verification Before Completion*).**
5. **Cero tolerancia a datos falsos, métricas ficticias o promesas que el sistema no respalde con código (*Anti-Slop Mandate*).**

### Taxonomía de Prioridades
* `[P0 - CRÍTICO / BLOQUEANTE]`: Requisito no negociable. Si no se cumple o se viola, se detiene de inmediato la tarea, el commit o el despliegue.
* `[P1 - ALTA CALIDAD / ARQUITECTURA]`: Estándar mandatorio de ingeniería, mantenibilidad, accesibilidad y resiliencia.
* `[P2 - EXCELENCIA / TRACCIÓN & GTM]`: Prácticas de optimización comercial, sensorial, diseño y go-to-market.

---

## FASE 0: Incepción, Contratos, Soberanía y Diseño Previo (Día 0)

### Directiva 0.1: Delimitación de Alcance y Frontera Negativa (*Intent Framing*) `[P0]`
* Antes de iniciar cualquier proyecto o feature, formular explícitamente la **Frontera Negativa**: declarar qué **NO** hace el sistema en esta iteración.
* Si una tarea toca más de una frontera de datos o dos subsistemas independientes, descomponerla en subproyectos atómicos antes de escribir código.

### Directiva 0.2: Soberanía de Datos y Garantía de "Cero Entrenamiento" (*Zero-Training Shield*) `[P0]`
* Garantizar contractualmente y en arquitectura que ningún dato sensible, código propietario o información del cliente sea utilizado para el reentrenamiento de modelos públicos de IA.
* En avisos de privacidad y contratos B2B, incluir la cláusula fiduciaria de soberanía cognitiva.

### Directiva 0.3: Blindaje de Propiedad Intelectual y Licenciamiento Permisivo `[P0]`
* Solo se autorizan dependencias con licencias permisivas (MIT, Apache 2.0, BSD, ISC).
* Queda terminantemente prohibido incorporar librerías con licencias copyleft estrictas (GPL v2/v3, AGPL) en proyectos comerciales sin autorización explícita del Director.

### Directiva 0.4: Presupuestos de Inferencia y Disyuntores de Tokenomics `[P1]`
* Asignar modelos por complejidad:
  - **Modelos Ligeros (Flash):** Parsing, linters, scaffolding, búsquedas, documentación, tareas de lectura rápida.
  - **Modelos Profundos (Pro / High Reasoning):** Modelado de datos, especificaciones arquitectónicas, debugging sistemático y auditoría de seguridad.
* Si una tarea consume tokens de forma circular sin emitir pruebas en verde, detener la ejecución y solicitar intervención del Director.

### Directiva 0.5: Spec-Driven Development (SDD) & Congelación de Contratos `[P0]`
* **Principio:** *Ningún agente escribe código de aplicación sin una especificación formal previa y congelada.*
* La especificación debe contener:
  1. Modelos de datos fuertemente tipados (Zod en TypeScript, Pydantic en Python, Schemas SQL DDL).
  2. Contratos de endpoints OpenAPI (rutas, query params, headers, status codes y payloads JSON).
  3. Casos de error canónicos y criterios de aceptación (Given-When-Then).
* El agente de implementación recibe la spec como verdad inmutable y no puede alterar los esquemas por cuenta propia.

### Directiva 0.6: Regla de Modularización Estricta (Anti-God-Files < 250 líneas) `[P1]`
* **Límite Absoluto:** Ningún archivo de código, controlador o componente de interfaz puede superar las **250 a 300 líneas de código**.
* Si un archivo supera este umbral, debe descomponerse obligatoriamente en subcomponentes de presentación, custom hooks (`useFeature.ts`) o módulos utilitarios puros (`/lib/`).

### Directiva 0.7: Lenguaje Claro del Mercado Meta (Plain Spanish) `[P2]`
* Erradicar la jerga técnica inflada y los anglicismos innecesarios que confundan al usuario final o al comprador corporativo.
* Conservar únicamente términos técnicos universales de la industria (*API*, *SaaS*, *backend*, *frontend*, *webhook*, *login*, *dashboard*, *token*).

### Directiva 0.8: Diseño Sensorial Propio: Ilustración Vectorial Inline SVG `[P2]`
* Cero hotlinking a bancos de imágenes externos (Unsplash, Pexels, placeholders).
* Todas las ilustraciones de soporte deben ser gráficos vectoriales nativos en código SVG (`<svg>` inline): 0 ms de latencia de red, escalabilidad nítida y adaptación automática a temas claro/oscuro con variables CSS (`currentColor`).

### Directiva 0.9: Arquitectura Intuitiva de Fricción Cero `[P2]`
* La aplicación debe ser autoexplicativa. Incorporar:
  1. Guía de Flujo en 3 Pasos (`/como-funciona`): Entrada → Motor de validación → Resultado/Descarga.
  2. Glosario de términos del dominio (`/glosario`).

### Directiva 0.10: Gobernanza del MVP, Doble Horizonte y Bóveda de Ideas `[P0]`
* Mantener la separación de horizontes:
  - `NORTH_STAR.md`: La visión completa a largo plazo (La Catedral). No se inyecta al agente de código para evitar saturación de contexto.
  - `MVP_BOUNDARY.md`: El primer ladrillo quirúrgico. Lo único que entra en el hito M1.
  - `FEATURE_PARKING_LOT.md`: La bóveda donde se congelan en 2 líneas las ideas no esenciales.
* **Directiva de Contención Estricta (Bozal a la IA):**
  > *Queda ESTRICTAMENTE PROHIBIDO que el agente sugiera nuevas funcionalidades, librerías extras o extensiones de producto no solicitadas. Cualquier oportunidad detectada fuera del alcance debe anotarse exclusivamente como una entrada en `FEATURE_PARKING_LOT.md` sin generar código.*

---

## FASE 1: Construcción Confinada y Desarrollo Agéntico en Arnés (Día 1)

### Directiva 1.1: Confinamiento y Control de Red Saliente `[P0]`
* Operar en entornos controlados y con permisos explícitos. Bloquear conexiones no auditadas a servidores externos no autorizados.

### Directiva 1.2: Flota de Agentes Desechables (*Disposable Fleet*) `[P1]`
* Los agentes son trabajadores de un solo uso; los repositorios, contratos y especificaciones son permanentes. Al terminar cada micro-tarea, limpiar el contexto para evitar arrastrar sesgos de memoria conversacional.

### Directiva 1.3: Matriz de Permisos del Tool Gateway por Riesgo `[P0]`
* **Nivel 0 (Lectura local):** `view_file`, `list_dir`, `grep_search` → Autónomo.
* **Nivel 1 (Escritura local):** Edición de archivos en rama de trabajo → Autónomo dentro de la spec.
* **Nivel 2 (Dependencias/Red):** Instalación de paquetes, llamadas HTTP autorizadas → Registrar en bitácora.
* **Nivel 3 (Crítico / Destructivo):** Despliegues, migraciones DDL en producción, cobros o borrado de ramas → Requiere confirmación humana obligatoria.

### Directiva 1.4: TDD Agéntico con Evidencia Literal de Terminal `[P0]`
* **Principio:** *Verification Before Completion siempre.*
* Ningún cambio se da por concluido afirmando "el código funciona" o "está listo" en lenguaje natural. Se debe ejecutar el comando de pruebas/build y reportar el resultado literal de salida.

### Directiva 1.5: Revisión Adversarial en Contexto Limpio (No Self-Approval) `[P0]`
* El agente que redacta el código jamás lo aprueba para producción. Debe someterse a una revisión adversarial por un agente auditor (`code-reviewer`, `security-auditor`) o por el Director humano.

### Directiva 1.6: Micro-Diffs Atómicos (< 200 líneas modificadas por commit) `[P1]`
* Cada commit debe ser atómico, enfocado y contener menos de **200 líneas modificadas** para facilitar auditorías y rollbacks limpios.

---

## FASE 2: Auditoría de Calidad, Veracidad y Accesibilidad (Día 2)

### Directiva 2.1: El "Bug-Sweep" en 5 Capas Estructuradas `[P0]`
Antes de autorizar cualquier módulo, auditar:
1. **Capa 1 (Invariantes y Tipos):** Cero `any` implícitos o explícitos, manejo exhaustivo de null/undefined.
2. **Capa 2 (Concurrencia y Carrera):** Race conditions, doble click en botones de envío, debouncing en inputs.
3. **Capa 3 (Fuzzing y Límites):** Strings vacíos, textos con emojis/caracteres especiales, números negativos, fechas en el pasado/futuro lejano.
4. **Capa 4 (Regresión):** Pruebas existentes ejecutadas sin fallos.
5. **Capa 5 (Seguridad y Fugas):** Cero secretos en código, sanitización contra XSS e inyección SQL.

### Directiva 2.2: Las 7 Reglas de Oro de Veracidad (*Anti-Slop Mandate*) `[P0]`
1. Cero testimonios de clientes inventados o con fotos de stock falsas.
2. Cero contadores numéricos simulados ("+10,000 usuarios activos" hardcodeado).
3. Estados vacíos (*Empty States*) diseñados y probados en primer lugar antes de poblar con datos.
4. Mensajes de error específicos y accionables para el usuario (nunca "Ocurrió un error inesperado").
5. Tiempos de carga con skeletons acordes al contenido real.
6. Cero `// TODO` o stubs vacíos en rutas de producción.
7. Declaración explícita de las fuentes de datos y metodología utilizada.

### Directiva 2.3: Estándar Mundial de Accesibilidad (WCAG 2.1/2.2 AA/AAA) `[P1]`
* Contraste mínimo de texto normal: **4.5:1** (AA) / **7.0:1** (AAA).
* Indicador de foco visible (`:focus-visible` outline con offset) en todos los elementos interactivos.
* Áreas de toque táctil de mínimo **44x44px** (48x48px en mobile).
* Navegación 100% operable por teclado (Tab, Shift+Tab, Enter, Escape).
* Jerarquía de encabezados estricta (`h1` único por página, seguido de `h2` y `h3` sin saltos).

### Directiva 2.4: Mandato Zero-Popup (Subpáginas Dedicadas) `[P1]`
* **Queda estrictamente prohibido el uso de ventanas modales emergentes (`<Dialog>`, `<Modal>`)** para flujos educativos, glosarios, comparadores, formularios extensos o herramientas de análisis, ya que desbordan viewports en laptops o dispositivos móviles.
* Todo flujo de contenido denso o de lectura debe implementarse como una **subpágina dedicada** con URL limpia y compartible, scroll vertical nativo del navegador y botón de retorno inteligente (`Volver`).

### Directiva 2.5: Arquitectura RBAC con Suplantación Auditada `[P1]`
* Separación estricta de roles: `SUPERADMIN`, `TENANT_ADMIN`, `USER`.
* Toda sesión de soporte o suplantación administrativa debe emitir un registro inmutable en la bitácora de auditoría con timestamp, ID del operador y motivo de acceso.

---

## FASE 3: Validación de Tracción, Mercado y Presentación (Día 3)

### Directiva 3.1: Graceful Payment Stubbing (Checkout Beta Fundador) `[P1]`
* Durante la fase de validación de tracción previa a pasarelas bancarias reales, implementar el **Checkout Beta**: formulario de intención de compra que captura el correo, ofrece descuento de fundador y otorga acceso temporal de cortesía con una experiencia de usuario transparente.

### Directiva 3.2: Presentaciones Ejecutivas en HTML 16:9 Widescreen `[P2]`
* Los decks de presentación para inversionistas (10 slides) y para clientes fundadores (6 slides) deben construirse como aplicaciones HTML responsivas autocontenidas en formato 16:9, con navegación por teclado (flechas izquierda/derecha), tipografía de alta gama y notas de orador integradas.

---

## FASE 4: Pre-Lanzamiento, Blindaje y Despliegue Go-Live (Día 4)

### Directiva 4.1: Checklist Pre-Lanzamiento de 10 Dimensiones `[P0]`
Para dar el **GO** a producción, se debe verificar y aprobar el 10/10 en:
1. `Build`: Cero errores de compilación TypeScript/Linter.
2. `Tests`: Suite de pruebas unitarias y de integración en verde.
3. `Security`: Auditoría de dependencias (`npm audit` / `pip audit`) sin vulnerabilidades críticas.
4. `Secrets`: Verificación estricta de ausencia de API keys o tokens en el código fuente.
5. `Performance`: Core Web Vitals (LCP < 2.0s, CLS < 0.1, FID/INP < 200ms).
6. `Accessibility`: Auditoría axe/Lighthouse sin violaciones de accesibilidad AA.
7. `Legal`: Aviso de Privacidad y Términos de Servicio actualizados y enlazados en el footer.
8. `Error Monitoring`: Capturador de excepciones y telemetría de errores configurada.
9. `Database Backup`: Procedimiento de respaldo y recuperación verificado.
10. `SEO/GEO`: Archivos `robots.txt`, `sitemap.xml`, `llms.txt` y metadatos OpenGraph configurados.

### Directiva 4.2: Migraciones de Base de Datos Zero-Downtime (Expand & Contract) `[P1]`
* Cambios en esquemas de bases de datos deben ejecutarse en 3 pasos:
  1. *Expand:* Agregar nuevas columnas o tablas de forma retrocompatible.
  2. *Migrate:* Transición de código y escritura dual.
  3. *Contract:* Eliminar columnas obsoletas solo tras verificar estabilidad en producción.

---

## FASE 5: Operación en Vivo, Resiliencia y Cumplimiento Fiscal (Día 5+)

### Directiva 5.1: Global Kill-Switch (< 500 ms) `[P0]`
* Toda integración con modelos de IA, webhooks de cobro o agentes autónomos debe contar con una variable de entorno / bandera de configuración que desconecte el servicio de inmediato ante anomalías o bucles infinitos.

### Directiva 5.2: Aislamiento Multi-Tenant con Row-Level Security (RLS) `[P0]`
* En bases de datos PostgreSQL, toda tabla que almacene datos de usuarios u organizaciones debe tener RLS activado de forma mandatoria con políticas basadas en el tenant ID verificado por JWT.

### Directiva 5.3: Watchdog Bot de Alertas en Tiempo Real `[P1]`
* Conectar excepciones no capturadas y caídas del servicio a un webhook de alertas instantáneas (Telegram, Discord o Slack) para notificación inmediata al equipo de guardia.

### Directiva 5.4: Exportación Total en 1 Clic (.ZIP) `[P1]`
* Todo usuario o empresa debe poder exportar el 100% de sus datos, archivos y registros en un archivo comprimido estándar (.ZIP / JSON / CSV) en cualquier momento, garantizando soberanía de datos y cero vendor lock-in.

### Directiva 5.5: Retención Fiscal Estatutaria de 5 Años `[P0]`
* Distinguir estrictamente entre el *Derecho al Olvido* (datos personales) y la *Retención Contable y Fiscal* (facturas, comprobantes fiscales, bitácoras de pago), las cuales deben conservarse de forma inmutable durante al menos 5 años conforme al Art. 30 del Código Fiscal de la Federación (CFF) y normativas internacionales equivalentes.
