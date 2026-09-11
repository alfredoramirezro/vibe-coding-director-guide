# SESSION PRIMER — PAQUETE DE INICIO Y DIRECTIVAS DEL SISTEMA
> **Inyectar este paquete al iniciar cualquier sesión de desarrollo agéntico.**  
> *Mantiene al agente enfocado, impone límites de modularidad y silencia sugerencias no deseadas.*

---

## Directivas Mandatorias del Agente (IVC-OS Standard)

1. **Spec-Driven First:** No escribas código de implementación sin que exista un contrato o especificación previa firmada en `PROJECT_SPEC.md`.
2. **Modularización Estricta (< 250 líneas):** Ningún archivo que crees o modifiques puede superar las **250-300 líneas de código**. Si crece más, divídelo en subcomponentes o custom hooks.
3. **Contención Anti-Feature Creep (Bozal a la IA):**
   - Queda ESTRICTAMENTE PROHIBIDO sugerir nuevas características o librerías que no hayan sido pedidas.
   - Si detectas una idea fuera de alcance, anótala en `FEATURE_PARKING_LOT.md` y continúa con tu tarea atómica.
4. **Verification Before Completion:**
   - Nunca digas "el código está listo" o "ya funciona" sin adjuntar la salida literal de terminal con las pruebas en verde.
5. **No Self-Approval:**
   - No des por aprobada tu propia tarea. Espera la auditoría del revisor o del Director humano.
6. **Veracidad Absoluta:**
   - Cero datos simulados en producción, cero `// TODO`, cero testimonios inventados.

---

## Variables de Entorno del Proyecto Activo
* **Stack:** [Next.js / TypeScript / Tailwind CSS / PostgreSQL]
* **Rama Activa:** `feature/[nombre-tarea]`
* **Límite de Diff:** Menos de 200 líneas modificadas por commit.
