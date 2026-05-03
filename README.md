# Manual de Rehabilitación · Prescripción del ejercicio

Guía clínica interactiva sobre prescripción del ejercicio para el **Manual de Rehabilitación para estudiantes de medicina** del Departamento de Medicina Física y Rehabilitación, Universidad Nacional de Colombia.

## Contenido

La guía está organizada en 11 pestañas:

1. **Introducción** — definiciones, recomendaciones generales, FITT-VP.
2. **Evaluación clínica** — anamnesis, examen funcional, escala UCLA interactiva.
3. **Riesgo cardiovascular** — estratificador interactivo con factores ACSM.
4. **Condición física** — calculadoras de IMC, cintura y cintura/cadera.
5. **Capacidad aeróbica** — VO₂máx desde 6MWT (ecuaciones ACSM y Mänttäri).
6. **FC máxima y reserva** — comparación de 5 ecuaciones + Karvonen.
7. **Intensidad** — escala de Borg 6–20 y CR-10 con equivalencias.
8. **Sesión y fortalecimiento** — calculadora bidireccional %1RM ↔ repeticiones.
9. **Por patología** — protocolos para 16 condiciones (HTA, IAM con PIpELINe, ACV, fibromialgia, artrosis, adulto mayor, diabetes, Parkinson, ataxias, cáncer, ELA, Pompe, post-COVID, obesidad, depresión, dolor músculo-esquelético común).
10. **Casos clínicos** — dos casos guiados con preguntas progresivas y programa de prescripción completo.
11. **Autoevaluación** — 10 preguntas de selección múltiple con retroalimentación inmediata.

## Características

- **HTML autocontenido** — todo el código (CSS y JavaScript) está embebido en un único archivo. No requiere conexión a internet, servidor, ni dependencias externas.
- **Compatible con dispositivos móviles** — el diseño se adapta a pantallas pequeñas.
- **Sin almacenamiento externo** — los cálculos se realizan localmente en el navegador; ningún dato se envía a servidores externos.
- **Acceso libre y gratuito** para uso docente.

## Despliegue en GitHub Pages

### Opción 1 — Repositorio público con GitHub Pages

1. Crear un repositorio nuevo en GitHub (por ejemplo `manual-rehabilitacion-unal`).
2. Subir el archivo `index.html` y este `README.md` al repositorio.
3. Ir a **Settings → Pages**.
4. En **Source**, seleccionar la rama `main` (o `master`) y la carpeta `/ (root)`.
5. Guardar. GitHub generará la URL pública en el formato:
   `https://<usuario>.github.io/<nombre-repositorio>/`
6. La página estará disponible en pocos minutos.

### Opción 2 — Repositorio con múltiples capítulos del manual

Si el manual va a tener varios capítulos, se sugiere la siguiente estructura:

```
manual-rehabilitacion-unal/
├── index.html                          # Portada del manual
├── prescripcion-ejercicio/
│   └── index.html                      # Este capítulo
├── analisis-marcha/
│   └── index.html                      # Otro capítulo
├── electrodiagnostico/
│   └── index.html                      # Otro capítulo
└── README.md
```

Cada capítulo será accesible en su propia URL:
`https://<usuario>.github.io/manual-rehabilitacion-unal/prescripcion-ejercicio/`

## Uso local

Para usar el manual sin publicarlo en internet:

1. Descargar `index.html`.
2. Abrirlo directamente en cualquier navegador moderno (doble clic).

Funciona completamente offline.

## Cómo citar

> Departamento de Medicina Física y Rehabilitación, Universidad Nacional de Colombia. *Manual de Rehabilitación para estudiantes de medicina: Prescripción del ejercicio*. [Año]. Disponible en: [URL del despliegue]

## Referencias principales

- Pescatello LS, American College of Sports Medicine. *ACSM's guidelines for exercise testing and prescription*. 9.ª ed. Wolters Kluwer; 2014.
- Whelton PK, et al. 2017 ACC/AHA Guideline for the Prevention, Detection, Evaluation, and Management of High Blood Pressure in Adults. *Hypertension*. 2017.
- Bannuru RR, et al. OARSI guidelines for the non-surgical management of knee, hip, and polyarticular osteoarthritis. *Osteoarthritis Cartilage*. 2019;27(11):1578-1589.
- Ensayo PIpELINe — *N Engl J Med*. 2025.
- Lista completa de referencias incluida en el documento original del capítulo.

## Licencia

Material docente de uso académico. Las imágenes, fórmulas y tablas referenciadas conservan los derechos de autor de sus fuentes originales, citadas en el texto.

---

**Versión actual:** 1.0 · Mayo 2026
**Contacto:** Departamento de Medicina Física y Rehabilitación · Universidad Nacional de Colombia
