# Datos extraídos del manual

## `precios-tablero-a11.csv`

801 precios de tablero extraídos del **manual técnico de cotización COOMO,
edición A11** (14/abr/2026), páginas 14 a 50. 125 materiales distintos.

| Columna | Contenido |
|---|---|
| `pagina` | Página del manual de donde salió la fila |
| `material` | Nombre del material en chino, tal como aparece |
| `espesor_mm` | Espesor del tablero |
| `precio_rmb_m2` | **Precio de fábrica en RMB/m²** |

Precios entre ¥166 y ¥2,211. Todos a medida estándar **2420×1200 mm** — para
otras medidas aplica el coeficiente de tamaño (ver `docs/contexto-proyecto.md`,
sección 4).

### Por qué esta tabla es la base de todo

Las secciones de puerta del manual (págs. 51-88) **no traen precio propio**.
Remiten al *Panel Material Summary* — esta misma tabla — y encima suman
recargos: +23/m², +125/m² con bisagra, +173 por hoja, +150 por esquina de
ensamble. Es decir, el precio de un gabinete se arma desde aquí.

### Trazabilidad con `Matriz_Precios_1.xlsx`

Siete de los ocho costos de la matriz aparecen en esta tabla, y **todos en el
renglón de 18 mm** — confirmación de que la columna `COSTO REAL` del Excel es
precio de fábrica COOMO en RMB/m².

| Costo | Espesor | Pág. | Material |
|---|---|---|---|
| ¥1,015 | 18 mm | 24 | 木皮板双面 · chapa de madera, dos caras |
| ¥1,746 | 18 mm | 31 | 木皮板双面贴北美胡桃木皮 · chapa nogal americano |
| ¥1,003 | 18 mm | 40 | 木皮板 · chapa de madera |
| ¥1,198 | 18 mm | 41 | 木皮板双面贴欧橡木皮 · chapa roble europeo |
| ¥213 | 18 mm | 15 | 免漆板 · melamina |
| ¥344 | 18 mm | 17 | 免漆板 · melamina |
| ¥330 | 18 mm | 19 | serie Egger |
| ¥1,304 | — | — | **sin coincidencia** |

Algunos precios coinciden con más de un material — son 125 materiales en un
rango acotado. Para fijar cuál corresponde a cada partida hay que cruzar contra
el acabado especificado en la hoja `LISTA` de la matriz.

## Limitaciones

Extraído del texto del PDF vía el conector de Drive, **no del archivo original**:

- El conector cortó en la **página 87 de 311**. Faltan herrajes (P.183-300),
  partes decorativas (P.89-182), la cotización de cuerpo de cocina (P.301) y la
  especificación de pedido (P.302-312).
- ~8% de los caracteres se perdieron; los nombres de material salen truncados o
  con fragmentos de encabezado pegados.
- No se leyó ninguna imagen, plano técnico ni muestra de color.
- Los precios (dígitos) salieron limpios. Los nombres, no siempre.

**Verificar contra el PDF antes de usar en una cotización a cliente.**

## Cómo completar lo que falta

El conector descarga archivos de hasta 10 MB. El manual pesa 34 MB. Partido en
cuatro (Imprimir → Guardar como PDF → rango de páginas), cada parte baja de
10 MB y se puede procesar con `pdfplumber` a fidelidad completa — mejor que esta
extracción:

```
parte 1  págs.   1 -  80
parte 2  págs.  81 - 160
parte 3  págs. 161 - 240
parte 4  págs. 241 - 311   ← trae la P.301, cuerpo de gabinete de cocina
```
