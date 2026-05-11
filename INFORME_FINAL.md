# Informe final · Revisión automatizada en 3 pasadas

**Para:** Fernando
**Fecha:** 2026-05-11
**Sesión:** Cowork (Claude) — ~2 h de trabajo desatendido
**Corpus revisado:** `web/manual-rehabilitacion-unal/` (16 HTML, ~23 000 líneas, ~620 000 caracteres de texto visible)

---

## 1. Cambios al código fuente · 1 línea modificada

El único auto-edit aplicado en toda la sesión:

| Archivo | Línea | Antes | Después | Pasada |
|---|---|---|---|---|
| `10-inmovilizacion/index.html` | 620 | `Cada item marcado…` | `Cada ítem marcado…` | 1 |

La RAE recoge "ítem" con tilde como adaptación al español. La aparición de `item` como atributo CSS (`align-items`, `justify-items`) **no fue tocada**.

---

## 2. Red de seguridad · cómo revertir

```bash
cd "~/Dropbox/1-LIBRO DE PREGRADO REHABILITACION/web/manual-rehabilitacion-unal"

# Para deshacer TODA la sesión (1 fix + 3 reportes):
git reset --hard pre-review-2026-05-11

# Para deshacer solo una pasada concreta:
git revert 8c62504    # quita Pasada 1
git revert 34d61f5    # quita Pasada 2  (solo reporte)
git revert 84fc228    # quita Pasada 3  (solo reporte)
```

| Item | Hash | Notas |
|---|---|---|
| **Tag de seguridad** | `pre-review-2026-05-11` → `23460f92` | Punto exacto antes de empezar |
| **Pasada 1** (ortografía) | `8c62504` | 1 edit + REVIEW_PASS1.md |
| **Pasada 2** (terminología) | `34d61f5` | Solo REVIEW_PASS2.md |
| **Pasada 3** (coherencia) | `84fc228` | Solo REVIEW_PASS3.md |

Validación HTML post-edit: el `html.parser` de Python confirma 0 tags abiertos sin cerrar y 0 errores estructurales en `10-inmovilizacion/index.html`.

**Nada se publicó.** No se hizo `git push`. El sitio en `fortizc-max.github.io` sigue mostrando la versión previa hasta que tú decidas hacer push.

---

## 3. Recomendaciones prioritarias para revisión humana

Estas son las correcciones que recomiendo aplicar después de leer los reportes:

### Tier A · seguro corregir (típos confirmados)

1. **`ortesis` → `órtesis`** en `05-msk-cuadros/index.html` líneas 855, 866, 1029, 1084, 1090 (5 instancias).
2. **`AVD` → `ABVD`** en `09-prescripcion/index.html:1783` (1 instancia; el contexto son actividades básicas).

### Tier B · requiere tu decisión

3. **`VO₂máx` vs `VO₂max`** — uniformar a `VO₂máx` (consistente con `FCmax` en español).
4. **`Lawton-Brody` vs `Lawton y Brody`** — 2 instancias en formato distinto en `09-adulto-mayor`.
5. **`baclofén` vs `baclofen`** — 5 instancias; decidir si nombre genérico (`baclofeno`) o comercial.
6. **`(cap. 8 completo)`** en `08-tratamientos/index.html:1120` — auto-referencia awkward.
7. **`PIpELINe`** (NEJM 2025) ×6 en `09-prescripcion` — verificar la grafía oficial del ensayo.

### Tier C · mejora estructural

8. **Siglas sin definición en su primera aparición**: MRC, FC, TUG, SPPB, AINE, ELA, UCI, TA, HTA, STC, AIVD, FITT. Como cada capítulo HTML se publica como página independiente, conviene que cada sigla esté definida la primera vez que aparece en su capítulo principal.

---

## 4. Cosas que NO encontré (señal positiva)

- **0** anclas internas rotas (todos los `href="#xxx"` apuntan a IDs válidos).
- **0** referencias a capítulos inexistentes.
- **0** contradicciones de cifras entre capítulos (SPPB ≤ 8, TUG ≥ 12 s / ≥ 20 s, Borg 6–20, MRC < 48, Fox 220−edad — todo consistente).
- **0** errores tipográficos masivos (doble espacio en texto, espacio antes de coma, comillas mezcladas).
- **0** palabras duplicadas reales (las 3 detectadas eran "de De Quervain", apellido).
- **0** errores de mayúsculas tras `.` (lo que detecté eran abreviaturas válidas: vs., cap., supl., Cord.).

El texto está **excepcionalmente cuidado** para un manuscrito en desarrollo activo.

---

## 5. Reportes generados (en este folder)

- `REVIEW_PASS1.md` — Ortografía y gramática (1 fix aplicado, 6 candidatos analizados).
- `REVIEW_PASS2.md` — Consistencia terminológica (6 hallazgos accionables, 12 siglas a revisar).
- `REVIEW_PASS3.md` — Coherencia argumentativa y referencias (2 hallazgos puntuales, red de citas mapeada).
- `INFORME_FINAL.md` — Este archivo.

Los scripts usados están en `manual_rehab/scripts/`:
- `review_pass1_html.py` (correr con `--apply` para auto-fixes; sin flag, solo reporta).
- `review_pass2_terminology.py` (solo reporta JSON).
- `review_pass3_coherence.py` (solo reporta JSON).

---

## 6. Lo que originalmente pedías y por qué se cambió

Tu brief inicial pedía revisar los **.tex** del libro LaTeX (`manual_rehab/chapters/*.tex`). En medio de la sesión decidiste cambiar el alcance a **las apps interactivas HTML** (las que sirven en `fortizc-max.github.io/manual-rehabilitacion-unal/`).

El libro LaTeX **no fue tocado en absoluto**. Si quieres que repita las 3 pasadas sobre los `.tex` (10 726 líneas de LaTeX en `manual_rehab/`), está documentado como "Pasada 4 sugerida" en `REVIEW_PASS3.md` y los scripts son fácilmente adaptables.

---

## 7. Bottom line

- **Edits aplicados:** 1 línea cambiada (item → ítem).
- **Reportes generados:** 4 archivos Markdown.
- **Tiempo estimado para revisar todos los hallazgos:** ~30 min.
- **Riesgo de retroceso:** mínimo — tag de seguridad + commits separados por pasada.
- **Estado del sitio público:** sin cambios (no se hizo push).
