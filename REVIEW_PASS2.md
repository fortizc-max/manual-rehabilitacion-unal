# REVIEW PASS 2 — Consistencia terminológica

**Fecha:** 2026-05-11
**Alcance:** 16 archivos HTML de `web/manual-rehabilitacion-unal/`
**Modo:** Solo reporte, sin auto-edits
**Snapshot de seguridad:** `pre-review-2026-05-11` → commit `23460f92`

---

## Resumen ejecutivo

| Categoría | Hallazgos accionables |
|---|---|
| Términos médicos con grafías inconsistentes | **6** |
| Siglas sin definición en primera aparición | **~12** |
| Variantes mayúscula/minúscula esperadas (no accionables) | muchos |
| Convenciones documentadas y respetadas | 1 (latín italicizado) |

**Conclusión:** la mayoría de variantes entre capítulos se deben a:
1. Mayúsculas iniciales por estar al comienzo de oración (esperado, no es error).
2. Convención del libro (declarada en cap. 1, línea 762) de nombrar músculos en latín italicizado seguido del nombre español.
3. Coexistencia legítima de sigla en español + nombre propio en inglés (UCI / ICU-AW).

Hay 6 hallazgos accionables (correcciones recomendadas) y un punto débil sistémico: muchas siglas se usan sin definir en su primera aparición dentro del capítulo, lo que dificulta la lectura como referencia rápida para estudiantes.

---

## A. Inconsistencias accionables (recomiendo corregir)

### A.1. `ortesis` sin tilde — 5 ocurrencias en cap 5

El resto del libro usa **`órtesis`** (27 veces) y **`Órtesis`** (3 al inicio de oración). En `05-msk-cuadros/index.html` aparece sin tilde 5 veces:

- Línea 855: "AINE corto + **ortesis** específica + fisioterapia"
- Línea 866: "**ortesis** específica; fisioterapia con énfasis en ejercicio activo"
- Línea 1029: "**ortesis** antebraquiopalmar en posición neutra para uso nocturno"
- Línea 1084: "reposo relativo, **ortesis** con inmovilización de muñeca y pulgar"
- Línea 1090: "manejo conservador con **ortesis** de muñeca y fisioterapia"

**Acción sugerida:** cambiar las 5 a `órtesis`.

---

### A.2. `AVD` ambiguo — 1 ocurrencia en cap 9-prescripcion

El libro distingue cuidadosamente **ABVD** (actividades básicas) de **AIVD** (instrumentales). Hay una sola instancia donde se usó "AVD" genérico:

- `09-prescripcion/index.html:1783`: "Limitación funcional para **AVD** (levantarse del inodoro, subir al carro, alcanzar objetos en alto)."

Los ejemplos son básicas (transferencias, alcance), por lo que debería ser **`ABVD`**.

---

### A.3. `FCmax` vs `FC máxima` — 72 vs 1 vs 1

Grafías encontradas para "frecuencia cardíaca máxima":

| Forma | Ocurrencias | Archivos |
|---|---|---|
| `FCmax` | 72 | 3 (08, 09-prescripcion, 11) |
| `FC máxima` | 1 | 1 |
| `Frecuencia cardíaca máxima` | 1 | 1 |

**Acción sugerida:** las dos ocurrencias minoritarias probablemente sean el momento en que se introduce el concepto y su sigla; verificar que estén en el primer uso del capítulo de prescripción.

---

### A.4. `VO₂máx` vs `VO₂max` — 12 vs 4

Mismo concepto con sufijo en español/inglés:

| Forma | Ocurrencias | Archivos |
|---|---|---|
| `VO₂máx` | 12 | 1 (09-prescripcion) |
| `VO₂max` | 4 | 2 (09-prescripcion, 08-tratamientos) |

**Acción sugerida:** uniformar a `VO₂máx` (consistente con `FCmax` → estarían en español ambos).

---

### A.5. Variantes de `Lawton-Brody`

| Forma | Ocurrencias |
|---|---|
| `Lawton-Brody` | 16 |
| `Lawton y Brody` | 2 |
| `Lawton` (solo) | 2 |

**Acción sugerida:** uniformar a `Lawton-Brody`. Las dos instancias de "Lawton" solo (sin Brody) están en lugares donde la referencia anterior ya estableció el nombre completo — discutible, podría dejarse.

---

### A.6. `baclofén` vs `baclofen` — 3 vs 2

El nombre genérico del fármaco en español es **`baclofeno`** (con -o final). Tanto `baclofén` (con tilde y sin -o) como `baclofen` (sin -o, sin tilde) son grafías comerciales o anglicismos.

**Acción sugerida:** revisar las 5 ocurrencias y unificar a `baclofeno` (RAE/INVIMA) o a `baclofen` si se prefiere el nombre comercial común.

---

## B. Siglas usadas sin definición en su primera aparición

Las siguientes siglas aparecen ≥10 veces sin que mi heurística haya detectado una definición en su primera ocurrencia (patrones `concepto (SIGLA)` o `SIGLA = concepto`):

| Sigla | Ocurrencias | Primer archivo | Comentario |
|---|---|---|---|
| `MRC` | 30 | 02-funciones-estructuras | Medical Research Council — escala de fuerza muscular |
| `FC` | 28 | 08-tratamientos | Frecuencia cardíaca |
| `TUG` | 27 | 02-funciones-estructuras | Timed Up & Go |
| `SPPB` | 27 | 03-actividades | Short Physical Performance Battery |
| `AINE` | 27 | 04-lumbalgia | Antiinflamatorios no esteroideos |
| `ELA` | 25 | 02-funciones-estructuras | Esclerosis Lateral Amiotrófica |
| `UCI` | 24 | 02-funciones-estructuras | Unidad de Cuidados Intensivos |
| `TA` | 18 | 07-discapacidad-neurologica | Tensión arterial |
| `HTA` | 16 | 08-tratamientos | Hipertensión arterial |
| `STC` | 15 | 05-msk-cuadros | Síndrome del Túnel del Carpo |
| `AIVD` | 15 | 03-actividades | Actividades Instrumentales de la Vida Diaria |
| `FITT` | 15 | 08-tratamientos | Frecuencia, Intensidad, Tiempo, Tipo |

**Acción sugerida:** revisar la primera aparición de cada sigla en su capítulo de uso principal y asegurar que esté **siempre definida** la primera vez, idealmente con el patrón estándar: `... la sigla XYZ (definición completa)` o `definición completa (XYZ)`.

Esto es útil porque cada capítulo HTML se publica como página independiente, y un estudiante puede entrar directamente a, por ejemplo, `04-lumbalgia` sin haber visto la definición en otro capítulo.

Para algunas (`CIF`, `TCE`, `ACV`, `MPE`) sí se detectó definición. Para otras como `NO` (42 ocurrencias en 11 archivos), es la palabra negativa común en mayúscula — falso positivo.

---

## C. Hallazgos analizados y descartados (falsos positivos)

### Nombres en latín de músculos (convención del libro)

`biceps brachii`, `triceps brachii`, `Terminologia Anatomica`, `flexor carpi radialis`, etc. aparecen sin tildes y con minúscula inicial dentro de etiquetas `<em>`. El cap. 1 línea 762 declara explícitamente la convención: *"los músculos se nombran en latín (Terminologia Anatomica) seguido del nombre tradicional en español: biceps brachii (bíceps braquial)..."*. **Todas estas instancias son correctas.**

### Nombres propios en inglés

`ICU-AW`, `ICU-acquired weakness`, `CAM-ICU`, `ICU Liberation`, `Society of Critical Care Medicine`, `Timed Up & Go`. Son nombres propios de paquetes/escalas, **no se traducen**. La sigla `ICU` aquí no es un duplicado de `UCI`; es parte del nombre.

### Variaciones de mayúscula inicial

`Rehabilitación` × 110 vs `rehabilitación` × 37; `Lesión` × 19 vs `lesión` × 63; etc. Reflejan posición de la palabra (inicio de oración vs no). **No son inconsistencia.**

### `cuando` × 50 vs `cuándo` × 28

`cuando` sin tilde es correcto como conjunción temporal o relativo; `cuándo` solo en interrogativos/exclamativos. Las cifras observadas son compatibles con uso correcto.

### `donde` × 7 vs `dónde` × 5

Mismo caso anterior, relativo vs interrogativo.

---

## D. Familias terminológicas saludables (sin acción)

Las siguientes familias se manejaron de forma consistente:

- `Karvonen` (mayúscula al inicio, siempre): correcto.
- `Parkinson` y `Alzheimer`: nombres propios siempre con mayúscula.
- `EVA` (Escala Visual Analógica), `NRS`, `EMG`, `VCN`, `CMAP`, `IMC`, `BMI`, `MMSE`, `DEXA`, `1RM`: con grafía uniforme.
- `Cochrane`, `ACSM`, `OMS/WHO`, `CIF`: bien tratadas.

---

## Cómo revertir esta pasada

```bash
cd web/manual-rehabilitacion-unal
git reset --hard pre-review-2026-05-11
```

Esta pasada solo añade el reporte; revertirla no cambia ningún HTML (no se aplicaron edits en Pasada 2).
