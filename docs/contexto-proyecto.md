# COOMO México — Contexto del proyecto

> Documento de traspaso. Reúne lo establecido hasta el 8 de septiembre de 2026.
> Sirve para retomar el trabajo desde cualquier sesión o cuenta.

---

## 1. Situación del negocio

- Franquicia de **COOMO** firmada para **Ciudad de México**, en septiembre.
- **Local comercial** ya conseguido.
- **Viaje a China** realizado; **personal capacitado en instalación**.
- **Proyecto en Nueva York** en curso, obtenido mientras se conseguía el local.
- Etapa actual: **cotización de muebles para el showroom**. COOMO ya envió la
  cotización y existe un sistema propio de "cálculo rápido"; al cotizar a
  detalle aparecen variaciones respecto de ese cálculo.

---

## 2. La empresa

**COOMO = 楷模 (Kǎimó)**, fundada en **2003**.
Razón social: 东莞市楷模家居用品制造有限公司 (Dongguan COOMO Home Furnishings
Manufacturing Co., Ltd.). Grupo: COOMO Furnishings Manufacturer (Group) Co., Ltd.

| Dato | Valor |
|---|---|
| Sede | Houjie (厚街镇), Dongguan, Guangdong |
| Fábricas | 13 (algunas fuentes 15) |
| Superficie | +800.000 m² construidos |
| Empleados | +6.000 |
| Tiendas | +2.000 en China y el exterior; ~200 "life halls" de +3.000 m² |
| Producción | Líneas importadas de Alemania e Italia |
| I+D | ~30 diseñadores internacionales, +2.000 patentes nacionales |
| Exporta a | Europa, América, Sudeste Asiático, Medio Oriente |

Posicionamiento: gama media-alta y alta, mueble contemporáneo de lectura
"clásico-moderno", residencial y hostelería.

### Líneas de marca

| Marca | Chino |
|---|---|
| COOMO | 楷模 |
| DAPU | 大普 |
| Latte | 拿铁 |
| PUSU | 普术 |
| COOMO 100 | 楷模100 |
| DASHU | 大术 |
| XINGDAO | 型道 |
| Cradle | 摇篮 |
| XISHE | 希奢 |
| SUMO | 素墨 |

Filiales/divisiones: COOMO HOME, Cosra (科斯拉), Weile (围乐), Particle (粒子).
Listados más antiguos añaden 梵帝尼, 歌特 y 圣萝莎 (textil, cocinas, armarios).

**Precisiones:**
- "Dusu" mencionado coloquialmente corresponde con alta probabilidad a
  **大术 DASHU**, la línea de estilo europeo del grupo.
- **"CNC"** no aparece en ninguna lista pública de marcas del grupo. Pendiente
  de confirmar con documentación contractual.
- Existe otra marca china llamada **璞素 PUSU** (Shanghái, 2011, mueble de autor
  en maderas nobles) **sin relación con COOMO**. No confundir con 普术.

### ⚠️ Dos empresas distintas usan el nombre 楷模

Confusión conocida en el sector chino, con artículos publicados solo para
explicarla.

| | **楷模家居 — COOMO** | **楷模木门 — KOOMO CASA** |
|---|---|---|
| Empresa | 东莞市楷模家居用品制造有限公司 | 江苏楷模家居科技有限公司 |
| Ubicación | Dongguan, Guangdong | Jiangsu |
| Negocio | Mueble + 全屋定制 | Puertas de madera y 整木家居 (carpintería integral) |
| Escala | 15 fábricas, +6.000 empleados | +300 salones, ~1.500 M RMB/año, +5.000 empleados, +700 referencias |

Origen del cruce: la entidad de Beijing 北京楷模伟业 fue dada de baja y su
representante legal fundó después la empresa de Jiangsu que opera 楷模木门.

**Pendiente crítico:** confirmar con cuál de las dos entidades está firmada la
franquicia, qué marcas habilita el contrato y para qué territorio —
especialmente si incluye carpintería fija.

### Presencia internacional

Operación documentada en **Australia** (showroom en Sídney, cuenta `@coomoau`).
No se encontró presencia establecida en Latinoamérica ni España: territorio
nuevo para ellos. Implica palanca de negociación, pero también ausencia de
logística y posventa local.

---

## 3. Auditoría del archivo `Matriz_Precios_1.xlsx`

### Estructura

| Hoja | Función |
|---|---|
| **MATRIZ** | Captura de medidas. 7 gabinetes + paneles recámara + 2 islas. Calcula m² |
| **CATALOGO** | Cotizador. 7 bloques de gabinete + islas + paneles + puertas vestidor + puertas cocina |
| **LISTA** | Tablero de muestras, 199 acabados con precio unitario. **No conectada** a las otras hojas |

Lógica por bloque:
`CANTIDAD` (m² de MATRIZ) × `PRECIO UNITARIO`,
donde `PRECIO UNITARIO = COSTO REAL + GANANCIA` y `GANANCIA = COSTO REAL × %`.
Tres bandas de altura: hasta 2.4, de 2.4 a 2.7, de 2.7 a 3.05.

### Hallazgos

**🔴 1. Margen cero.** La columna `%` (H) está vacía en las 40+ partidas.
`I17 = G17 × H17 = 1015 × (vacío) = 0`, por lo que `E17 = G17 + 0 = 1015`.
El precio de venta es idéntico al costo. Los 414,618 del TOTAL son costo puro.

**🔴 2. Puertas de cocina fuera del total.** El TOTAL (E236) suma `F224:F231`,
ocho subtotales. El bloque PUERTAS COCINA (fila 211, subtotal **14,823**) no
está incluido. SUPERFICIE DE COCINA tampoco.

**🔴 3. La isla aplica el factor 1.5 dos veces.**
```
D180 = F175 × 1.5           ← en la cantidad
F180 = E180 × D180 × 1.5    ← otra vez en el subtotal
```
Da 19,642.50 en vez de 13,095. **6,547.50 de más.** Las filas 169-171 del otro
bloque de islas aplican el factor una sola vez: la fila 180 es la errónea.

**🟠 4. Bandas de altura inconsistentes.** Los 7 gabinetes miden **2.73 m** en
MATRIZ, pero:

| Bloque | Banda que suma el subtotal |
|---|---|
| COCINA | hasta 2.4 |
| LIVING TV | 2.4 – 2.7 |
| VESTIDOR | 2.4 – 2.7 |
| LIVING 2 | hasta 2.4 |
| Sample 1, 2, 3 | 2.4 – 2.7 |

Ningún bloque usa la banda correcta (2.7–3.05), y COCINA y LIVING 2 usan una
banda distinta a los demás siendo el mismo producto a la misma altura. La banda
2.7–3.05 tiene el precio unitario escrito a mano como `0` en los seis bloques,
con costos 500/600 idénticos en todos — aparentan ser valores de relleno.
Alinear COCINA y LIVING 2 a la banda 2.4–2.7 suma **+31,352**.

**🟠 5. Las líneas "DOLLARS" dan cero.** Cada bloque cierra con
`DOLLARS = SUM(F29)`, pero el subtotal está en **E29**; F29 está vacía. Las
siete líneas dan 0. Más de fondo: **no hay tipo de cambio, flete, pedimento ni
IVA en ninguna parte del archivo**.

**🟠 6. Subtotal de puertas de vestidor incompleto.** `E208 = F205` únicamente.
Omite D-01 (puertas hasta 2.4) y C-02 FRAME — 15 ml de marco sin cobrar.

**🟡 7. Referencias rotas y cadena paramétrica cortada.**
- `E173 = SUM(F118:F118)` — apunta a una fila del bloque 6. Da 0.
- `J234` y `J236` = `#REF!`. El total de ganancia está muerto.
- `D182:D184` apuntan a F178 (vacía). `C186` apunta a B162 (vacía).
- `C219` etiquetado "PUERTAS VESTIDOR" estando en el bloque de cocina.
- Cantidades escritas a mano, desconectadas de MATRIZ: islas = 5, puertas
  vestidor = 7.5, puertas cocina = 5, D205 = 4 pzas, D217 = 18 ml.
- El descuento de ventana (`E26 = B26×C26 − B28×C28`) resta cero siempre:
  B28/C28 son celdas de encabezado.

**🟡 8. Datos sucios en LISTA.**
- Desde la fila 102 el espesor dice `0.18m` en vez de `0.018m`.
- MP-18 a 2 caras cuesta 50 y a 1 cara 597 (comparar MP-23: 631 → 848).
- Fila 191: categoría y código invertidos.
- Se salta el consecutivo #82; G-72P y G-75P duplicados con categorías distintas.

### Impacto acumulado

| Concepto | Monto |
|---|---|
| TOTAL como está | **414,618.18** |
| + Alinear COCINA y LIVING 2 de banda | +31,352.47 |
| + Puertas de cocina faltantes | +14,823.00 |
| − Doble factor de la isla | −6,547.50 |
| **Subtotal corregido, aún a costo** | **454,246.15** |
| Margen | **0** |

Sin tipo de cambio, flete, aduana ni IVA.

---

## 4. El manual técnico de cotización

> Incorporado el 8 de septiembre de 2026, leyendo el Drive de la cuenta de
> empresa (`coomomx@gmail.com`).

### Qué es cada archivo

El archivo del Drive llamado **`Lista de precio cabinets`** (PDF, 34 MB) **no es
la cotización de México**. Es el **manual técnico de cotización de COOMO,
edición A11, del 14/abr/2026**, 311 páginas, en versión bilingüe
chino-inglés. Es decir: la pieza que se daba por faltante ya estaba en el Drive,
bajo otro nombre.

| Archivo | Qué es | Estado |
|---|---|---|
| `Lista de precio cabinets` (PDF, 34 MB) | Manual técnico **A11**, 14/abr/2026, 311 pp. | ✅ Leído |
| `楷模定制技术报价手册 A12版2026.7.01给墨西哥.xlsx` (754 MB) | Manual **A12**, 1/jul/2026, "para México" | ❌ Ilegible, ver abajo |

El A12 es un **Excel, no un PDF**, y pesa 754 MB — el extractor devuelve
contenido vacío. Casi con certeza son fotos de producto incrustadas; los datos
de celda deben pesar poco. **Para leerlo hay que exportar sus hojas a CSV** (o
guardar una copia sin imágenes) y volver a subirla al Drive.

`Matriz_Precios_1.xlsx` **no está en el Drive de la empresa** — sigue en la
cuenta personal.

### 🟢 Resuelto: la moneda

El manual cotiza todo en **`RMB/m²`**, con dos columnas: `Factory Price`
(precio de fábrica) y `Selling Price`. Los recargos van en yuanes (`元`):
150 元 por esquina de ensamble, 150 元 por cara de ranurado, 173 元 por hoja.

El cruce contra el Excel es exacto. Los tableros se cotizan por espesor:

```
木皮板 双面  (chapa de madera, dos caras)
  9mm → 954    18mm → 1015    25mm → 1065
  40mm → 1128  60mm → 1187    70mm → 1215

双面多层板  (multilaminado, dos caras)
  9mm → 722    18mm → 842     25mm → 962
  40mm → 1021  60mm → 1067    70mm → 1089
```

**`1015` — el primer costo del Excel — es el precio de fábrica del tablero de
chapa a dos caras en 18 mm.** También coinciden como valores del manual 1746,
1003, 344, 1198, 213 y 330. Solo 1304 no aparece (posible cambio entre A11 y
A12).

> **Conclusión: la columna `COSTO REAL` es precio de fábrica COOMO en RMB/m².**
> El TOTAL de 414,618 son **yuanes**, no pesos ni dólares. Falta encima:
> tipo de cambio, flete, arancel, IVA y margen.

### 🔴 Las bandas de altura del Excel están mal planteadas

El manual **no maneja tres precios por altura**. Maneja **un precio estándar a
medida 2420×1200 mm, multiplicado por un coeficiente** según el tamaño real
(regla 1 de la P.12: *"All panel prices quoted at std. size 2420×1200mm"*):

| Material | Rango | Coeficiente |
|---|---|---|
| Melamina / aglomerado / OSB / ENF | 2420×1200 → 2720×1200 | **× 1.16** |
| Laca y chapa de madera | 2420×1200 → 3050×1200 | **× 1.10** |
| Laca y chapa de madera | 3050×1220 → 3600×1220 | **× 1.15** |
| Panel de aluminio tipo panal | 2420×1200 → 2720×1200 | **× 1.25** |

Esto explica el hallazgo 🟠4 de la auditoría: las tres bandas escritas a mano
(y el `0` en la banda 2.7–3.05) son un intento de codificar estos coeficientes
sin tenerlos. **El cálculo correcto es precio base × coeficiente**, no tres
precios independientes.

⚠️ **Ojo con los 2.73 m de MATRIZ:** 2730 mm **excede los 2720 mm** donde topan
los coeficientes de melamina y de panel de aluminio. En chapa de madera sí
entra en el tramo ×1.10. Hay que verificar material por material si la altura
del proyecto obliga a saltar de tramo o cambiar de sustrato.

### Otras reglas de la P.12 que el Excel no aplica

- **Mínimos facturables:** puerta de gabinete y panel europeo de menos de
  0.3 m² se cobran como 0.3 m². Otras partidas, menos de 0.5 m² se cobran
  como 0.5 m².
- **Piso por precio de fábrica:** si el costo por área de una pieza cae por
  debajo del precio de fábrica tabulado, se cobra el tabulado. Ejemplo del
  manual: G-39C de 1000×50×18 mm da 24.3, pero se factura **63**.
- **Veta horizontal ×1.2.** **Sustrato especial ×1.5.**
- **Color especial ×1.1**, y muestra de color a 300 元.
- Laca y chapa por debajo de 0.09 m² se cobran a precio de listón.

Ninguno de estos mínimos ni recargos está en el Excel, y todos empujan el
costo **hacia arriba**.

---

## 5. Preguntas abiertas

1. ~~¿En qué moneda está la columna `COSTO REAL`?~~ → **RMB, precio de fábrica.
   Resuelto** (sección 4).
2. **¿Qué margen se va a correr?** ¿Uno solo, o distinto por partida (gabinete
   vs. puerta vs. isla)? El manual trae una columna `Selling Price` propia de
   COOMO: falta ver si trae valores en el A12 o si la define el franquiciatario.
3. **¿El factor 3.5** que multiplica los interiores es "m² de tablero por m² de
   fachada"? Es el multiplicador más pesado del archivo. No aparece en la P.12
   del A11 — hay que buscarlo en la sección de cuerpo de gabinete (P.301).
4. **¿Con cuál entidad está firmada la franquicia** — COOMO (Dongguan) o
   KOOMO CASA (Jiangsu)? Determina el alcance en carpintería fija.
5. **¿Qué es "CNC"** en la lista de líneas de marca?
6. **¿Qué cambió entre A11 y A12?** El A12 se hizo explícitamente "para
   México". Si trae precios distintos, manda el A12.

---

## 6. Documentos y dónde viven

Los archivos del negocio están repartidos en **dos cuentas de Google**. La
cuenta de empresa ya está conectada como conector de Drive, así que se puede
leer directo desde la sesión.

**Cuenta personal** (`jromanomasri@gmail.com`) — *no conectada*:
- `1.楷模报价册-出厂价20250630.pdf` — catálogo COOMO a precio de fábrica (出厂价), corte 30/jun/2025
- `Mexico-Manhattan-Furnishing 04012026 (1).xlsx` — posible proyecto de Nueva York
- **`Matriz_Precios_1.xlsx`** — el archivo auditado en la sección 3

**Cuenta de empresa** (`coomomx@gmail.com`) — *conectada*:
- `Lista de precio cabinets` (PDF, 34 MB) — **manual técnico A11**, ver sección 4
- `楷模定制技术报价手册 A12版2026.7.01给墨西哥.xlsx` (754 MB) — manual A12, ilegible por tamaño
- `BRANDBOOK.pdf` (636 KB), `BRANDBOOK.ai` (58 MB), `LOGO.ai`, `LOGO-01/02.png`
- `iluminacion.pdf` (117 MB), carpeta `CATALOGOS`, carpeta `MULTIMEDIA`
- `AGOSTO Content_Calendar_COOMO` (Sheets, compartido por `esdelirarte@gmail.com`)

**Límite práctico:** subir archivos al chat topa en 30 MB, y este entorno no
alcanza `drive.google.com` por red. Todo lo grande entra por el conector de
Drive, y lo que el conector no puede extraer hay que exportarlo a un formato
liviano (CSV) y volver a subirlo al Drive.

---

## 7. Siguientes pasos

1. **Exportar el A12 a CSV** y subirlo al Drive de la empresa, para comparar sus
   precios y coeficientes contra los del A11 ya leído. Es el único archivo clave
   que sigue sin poder abrirse.
2. **Subir `Matriz_Precios_1.xlsx` al Drive de la empresa** (hoy está en la
   cuenta personal, que no está conectada). Sin él no se puede corregir el
   archivo, solo describir los errores.
3. **Rehacer el cálculo con la lógica real del manual:** precio base a
   2420×1200 × coeficiente de tamaño, en vez de tres bandas de altura escritas a
   mano. Verificar material por material qué pasa con los 2.73 m.
4. **Aplicar las reglas que faltan:** mínimos de 0.3 y 0.5 m², piso por precio
   de fábrica tabulado, recargos por veta horizontal, sustrato y color especial.
5. **Corregir los errores de la auditoría:** columna de margen viva, referencias
   `#REF!` reparadas, doble factor de la isla eliminado, puertas de cocina
   incluidas en el total.
6. **Añadir el bloque de costeo de importación:** TC RMB→MXN + flete + arancel +
   pedimento + IVA. Hoy el archivo se queda en precio de fábrica en yuanes, que
   es apenas el punto de partida.
7. **Definir el margen** (pregunta abierta 2) y evaluar una versión web del
   cotizador en este repositorio.
