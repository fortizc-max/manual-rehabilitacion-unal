# REVIEW PASS 1 — Ortografía y gramática

**Fecha:** 2026-05-11
**Alcance:** 16 archivos HTML de `web/manual-rehabilitacion-unal/` (12 capítulos + 3 anexos + index principal)
**Modo:** Auto-corrección conservadora + reporte
**Snapshot de seguridad:** tag `pre-review-2026-05-11` → commit `23460f92`

---

## Resumen ejecutivo

| Categoría | Conteo |
|---|---|
| Auto-correcciones aplicadas | **1** |
| Hallazgos para revisión manual (alta confianza) | 1 |
| Falsos positivos descartados manualmente | 22 |
| Líneas HTML totales | 20 061 |
| Caracteres de texto visible analizado | ~620 000 |

**Conclusión:** los HTMLs están **excepcionalmente limpios** desde el punto de vista ortotipográfico. No se encontraron errores frecuentes de español académico (espacios múltiples internos, espacios antes de signos de puntuación, tildes faltantes en adverbios, palabras duplicadas reales, comillas mezcladas). El único hallazgo accionable fue una palabra sin tilde según RAE.

---

## Auto-corrección aplicada

### 1. `item` → `ítem` (RAE)

- **Archivo:** `10-inmovilizacion/index.html`
- **Línea:** 620
- **Antes:**
  > Cada **item** marcado contraindica la *movilización activa*.
- **Después:**
  > Cada **ítem** marcado contraindica la *movilización activa*.
- **Justificación:** la RAE recoge "ítem" con tilde como adaptación al español. En otras ubicaciones del libro el término aparece como atributo CSS (`align-items`) y queda intacto. Esta corrección no afecta CSS/JS.

---

## Hallazgos analizados y descartados

Por transparencia, se documentan los falsos positivos del corrector automático para que puedan ser ignorados en futuras pasadas.

### Palabras duplicadas (regex `\b(palabra)\s+\1\b`)

Tres coincidencias, todas en el apellido **De Quervain** ("Tenosinovitis de De Quervain"). El primer "de" es la preposición española, el segundo es la "De" francesa del apellido. **No son duplicaciones.** Aparecen en:
- `05-msk-cuadros/index.html` (×2)
- `08-tratamientos/index.html` (×1)

### "Punto + minúscula" (regex `\.\s+[a-z]`)

14 coincidencias. **Todas son abreviaturas válidas seguidas de minúscula:**
- `Cord. lateral/posterior/medial` (Cordón en 01-anatomia)
- `vs.` comparativo (en 02-funciones-estructuras, 06-electrodiagnostico, anexo-c)
- `supl.` (suplemento, en 06-electrodiagnostico)
- `Barthel 65/100. mRS 3.` (escala/sigla, en 02-funciones-estructuras)

### Spell-check de pyspellchecker(es)

1 851 palabras únicas no reconocidas por el diccionario español de `pyspellchecker`. Después de filtrar por frecuencia entre capítulos (palabras que solo aparecen en 1 archivo) y de filtrar candidatos donde la sugerencia es la misma palabra con tilde, quedaron 6 candidatos de alta confianza:

| Palabra | Sugerencia | Archivo | Veredicto |
|---|---|---|---|
| `anatomica` | anatómica | 01-anatomia | **Falso positivo** · es Latín (*Terminologia Anatomica* es el nombre oficial latino) |
| `diagnostica` | diagnóstica | 05-msk-cuadros | **Falso positivo** · es el verbo "(él/ella) diagnostica" |
| `cortes` | cortés | 09-prescripcion | **Falso positivo** · es plural de "corte" (punto de corte) |
| `item` | ítem | 10-inmovilizacion | **✓ TYPO REAL** — corregido |
| `fabrica` | fábrica | 11-ayudas-y-ortesis | **Falso positivo** · es el verbo "el ortesista fabrica" |
| `inter` | ínter | anexo-c-fuerza-muscular | **Falso positivo** · es prefijo "inter-examinador" |

---

## Limitaciones de esta pasada

1. **Diccionario:** `pyspellchecker` Spanish no maneja morfología (plurales, conjugaciones) ni terminología médica/anatómica. Un análisis con `hunspell + es_ES + médico` daría más sensibilidad, pero requiere `apt-get install` (sin permisos en este entorno).
2. **No se revisaron:** concordancia de género/número, régimen preposicional, estilo, redundancias. Eso requiere herramientas como LanguageTool o revisión humana.
3. **Mayúsculas iniciales tras `:`** no se revisaron como categoría (uso es discutible en español).

---

## Recomendaciones para una segunda pasada manual

Si quieres hacer una revisión humana adicional, los archivos con más texto y por ende más riesgo son (por densidad):

1. `09-prescripcion/index.html` (2 397 líneas)
2. `05-msk-cuadros/index.html` (2 003 líneas)
3. `01-anatomia/index.html` (1 792 líneas)
4. `02-funciones-estructuras/index.html` (1 705 líneas)
5. `06-electrodiagnostico/index.html` (1 694 líneas)

Sugerencias para esa revisión:
- Pegar el texto visible (sin tags) en LanguageTool web (https://languagetool.org/) capítulo por capítulo.
- O instalar localmente `brew install hunspell` + diccionario `es_ES` y correr `hunspell -d es_ES`.

---

## Cómo revertir esta pasada

```bash
cd web/manual-rehabilitacion-unal
git reset --hard pre-review-2026-05-11
```

Esto descarta el commit de la Pasada 1 y vuelve al estado exacto previo. El tag de seguridad se conserva.
