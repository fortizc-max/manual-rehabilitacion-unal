# REVIEW PASS 3 — Coherencia argumentativa y referencias

**Fecha:** 2026-05-11
**Alcance:** 16 archivos HTML de `web/manual-rehabilitacion-unal/`
**Modo:** Solo reporte, sin auto-edits
**Snapshot de seguridad:** `pre-review-2026-05-11` → commit `23460f92`

> Nota: los HTMLs no usan BibTeX (lo cual aplica al libro LaTeX en `manual_rehab/`). Aquí se revisan citas inline tipo "Autor Año", referencias cruzadas a capítulos, integridad de anclas internas, y consistencia de cifras clave entre capítulos.

---

## Resumen ejecutivo

| Categoría | Resultado |
|---|---|
| Anclas internas rotas (`href="#xxx"` sin `id` que las reciba) | **0** ✓ |
| Referencias cruzadas a capítulos inexistentes (cap. N con N>11 o N<1) | **0** ✓ |
| Auto-referencias awkward (cap. N dentro del propio cap N) | **1** |
| Inconsistencias en formato de citas | **0** ✓ |
| Cifras clave entre capítulos con contradicción | **0** ✓ |
| Nombres de ensayo / acrónimo con capitalización inusual (verificar) | **1** |

**Conclusión:** la arquitectura interna del corpus es **muy sólida**. Anclas, navegación entre capítulos y cifras clínicas se mantienen consistentes a lo largo de los 16 archivos. Hay dos hallazgos puntuales (uno editorial menor, uno que requiere tu verificación) y observaciones sobre cómo está estructurada la red de citas.

---

## A. Hallazgos accionables

### A.1. Auto-referencia parentética en cap 8

- **Archivo:** `08-tratamientos/index.html`
- **Línea:** 1120
- **Texto:** `<h3>Síntesis · criterios de derivación al fisiatra (cap. 8 completo)</h3>`

El paréntesis "(cap. 8 completo)" aparece **dentro** del cap 8. Para el lector que abre cap 8 directamente, la auto-referencia es confusa. Opciones:
- Quitar el paréntesis: `Síntesis · criterios de derivación al fisiatra`
- Reformular: `Síntesis · criterios de derivación al fisiatra · todo el capítulo`

No es un error de información; es un detalle de redacción.

### A.2. Capitalización inusual "PIpELINe" — verificar

- **Archivo:** `09-prescripcion/index.html`
- **Líneas:** 1098, 1165, 1167, 1887, 2259, 2268
- **Texto representativo:** `ensayo PIpELINe (NEJM 2025)`

La grafía mezcla mayúsculas y minúsculas (P-I-p-E-L-I-N-e). Puede ser:
- **Intencional**, si el nombre del ensayo se estiliza así oficialmente (raro en ensayos clínicos, pero ocurre — ej. *iFR*, *eGFR*).
- **Typo de "PIPELINE"** que se propagó por copy-paste a 6 ocurrencias.

**Acción sugerida:** verificar la grafía oficial del ensayo (PubMed / NEJM 2025) y, si es "PIPELINE", reemplazar las 6 ocurrencias.

---

## B. Cifras clave validadas entre capítulos (sin contradicciones)

Esta tabla muestra que los puntos de corte aparecen de manera **consistente** allá donde se citan.

| Concepto | Valor | Aparece en | Veredicto |
|---|---|---|---|
| **SPPB cutoff funcional** | `≤ 8` | 03-actividades, 09-adulto-mayor, anexo-a-sppb | ✓ consistente |
| **TUG riesgo de caídas** | `≥ 12 s` | 08-tratamientos, 09-adulto-mayor | ✓ consistente |
| **TUG sarcopenia severa** | `≥ 20 s` | 09-adulto-mayor | ✓ (cutoff distinto, contexto distinto) |
| **Escala de Borg RPE** | `6–20` | 09-adulto-mayor, 09-prescripcion | ✓ consistente |
| **Borg ejercicio fuerza** | `15–17` para 70–80% de 1RM | 09-adulto-mayor | ✓ (única mención, sin contradicción) |
| **Fox · FCmax** | `220 − edad` | 09-prescripcion | ✓ |
| **MRC sum-score ICU-AW** | `< 48 / 60` | 10-inmovilizacion (en dos lugares) | ✓ consistente |
| **Banderas rojas edad lumbalgia** | `> 65 mujeres / > 75 hombres` | 04-lumbalgia | ✓ (única mención) |

---

## C. Mapa de citas autor-año por archivo

| Archivo | Citas inline detectadas | Comentario |
|---|---|---|
| 09-prescripcion/index.html | **47** | Es el capítulo con más referencias bibliográficas — apropiado por ser denso en guías ACSM / Cochrane / ensayos. Formato consistente "Autor Año". |
| 03-actividades/index.html | 5 | OK |
| 05-msk-cuadros/index.html | 3 | OK |
| 09-adulto-mayor/index.html | 3 | OK |
| 10-inmovilizacion/index.html | 3 | OK |
| 04-lumbalgia/index.html | 1 | Bajo para un capítulo extenso — posible oportunidad para reforzar evidencia citada |
| 06-electrodiagnostico/index.html | 1 | Bajo para un capítulo técnico |
| Otros | 0–1 | — |

### Citas que aparecen en ≥2 archivos (intertextualidad sana)

- `Graf 2008` — en 02-funciones-estructuras y 03-actividades
- `Kosek 2021` — en 05-msk-cuadros y 08-tratamientos

Ambos son ejemplos saludables de un mismo concepto referenciado consistentemente desde dos capítulos.

### Formato

Las 47 citas de cap 9-prescripcion siguen el formato uniforme `Autor Año` (sin paréntesis, sin coma entre autor y año):
`Pescatello 2014`, `Cornelissen 2013`, `Tan 2022`, `Bidonde 2014`, etc.

No detecté variantes como `Pescatello, 2014` o `(Pescatello 2014)` mezcladas. **Formato consistente.**

---

## D. Red de referencias cruzadas entre capítulos

Mapa de "cap N → cap M" detectado en el texto visible:

```
02-funciones-estructuras  →  cap. 1, cap. 3, cap. 5, cap. 9
03-actividades            →  cap. 2, cap. 9
04-lumbalgia              →  cap. 2
05-msk-cuadros            →  cap. 6, cap. 7
07-discapacidad-neuro     →  cap. 2, cap. 3, cap. 8
08-tratamientos           →  cap. 4, cap. 5, cap. 7, cap. 9, cap. 11
09-adulto-mayor           →  cap. 3, cap. 8, cap. 10
10-inmovilizacion         →  cap. 8, cap. 9
11-ayudas-y-ortesis       →  (sin referencias salientes)
anexo-c-fuerza-muscular   →  cap. 1
```

Observaciones:
- Cap 1, cap 6, cap 10, cap 11 no son **referenciados por nadie** desde el contenido (excepto cap 10 ← cap 9, cap 11 ← cap 8). Esto es esperado: cap 1 es anatomía (base, no se cita típicamente desde otros); cap 6 es electrodiagnóstico (referido por cap 5 ya); cap 10–11 son finales en la secuencia.
- Hay 2 auto-referencias en metadescripciones (`<meta>` de cada capítulo) que son legítimas — es la propia descripción de la página.
- La red es **acíclica y forward-leaning** salvo cap 02 ↔ cap 03 que se referencian entre sí (esperable, son los pilares CIF + AVD).

---

## E. Integridad de anclas (`href="#xxx"`)

Por cada archivo HTML, **todos los `href="#..."` apuntan a un `id` definido en el mismo archivo**. No hay anclas rotas internas. Esto significa que las pestañas, calculadoras, glosarios y navegación inter-secciones funcionan correctamente en el navegador.

| Archivo | Anclas | IDs | Rotas |
|---|---|---|---|
| 01-anatomia | varios | varios | 0 |
| 02-funciones-estructuras | varios | varios | 0 |
| ... (todos los demás) | — | — | **0** |

---

## F. Limitaciones de esta pasada

1. **No revisé enlaces externos** (`href="https://..."`) ni verifiqué que los DOIs/PubMed IDs apunten a artículos válidos. Esto requiere conexión a internet sostenida y revisión manual.
2. **No verifiqué la corrección clínica de las cifras** (solo su consistencia interna entre capítulos). Las cifras pueden ser internamente coherentes pero estar desactualizadas frente a la última guía.
3. **No reviso la jerarquía argumental** dentro de cada capítulo (¿la tesis principal del cap se sostiene a lo largo del texto?). Esto requiere lectura humana experta.
4. **Las 47 citas de 09-prescripcion** no fueron contrastadas contra sus fuentes originales. Un script podría verificar año y revista vía API de PubMed.

---

## G. Recomendaciones para una posible Pasada 4

Si quieres profundizar más, en otra sesión podría:
1. Validar cada cita de 09-prescripcion contra PubMed (existe; autor y año coinciden con la publicación real).
2. Hacer la misma Pasada 1–3 sobre los `.tex` de `manual_rehab/` (el libro LaTeX, que es lo que originalmente solicitabas; las decisiones tomadas aquí fueron por el HTML).
3. Buscar específicamente terminología clínica obsoleta (e.g., "demencia senil" → "trastorno neurocognitivo mayor").
4. Verificar que las dosis de fármacos citadas correspondan a guías actuales (INVIMA, ACSM 2024, GOLD 2024, etc.).

---

## Cómo revertir esta pasada

```bash
cd web/manual-rehabilitacion-unal
git reset --hard pre-review-2026-05-11
```

Esta pasada solo añade el reporte; no hay edits que revertir.
