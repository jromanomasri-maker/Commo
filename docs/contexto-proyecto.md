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

## 4. Preguntas abiertas

1. **¿En qué moneda está la columna `COSTO REAL`?** ¿RMB de fábrica, USD FOB, o
   ya nacionalizado en MXN? De esto depende todo lo demás.
2. **¿Qué margen se va a correr?** ¿Uno solo, o distinto por partida (gabinete
   vs. puerta vs. isla)?
3. **¿El factor 3.5** que multiplica los interiores es "m² de tablero por m² de
   fachada"? Es el multiplicador más pesado del archivo.
4. **¿Con cuál entidad está firmada la franquicia** — COOMO (Dongguan) o
   KOOMO CASA (Jiangsu)? Determina el alcance en carpintería fija.
5. **¿Qué es "CNC"** en la lista de líneas de marca?

---

## 5. Documentos y dónde viven

Los archivos del negocio están repartidos en **dos cuentas de Google**:

**Cuenta personal** (`jromanomasri@gmail.com`):
- `1.楷模报价册-出厂价20250630.pdf` — catálogo COOMO a precio de fábrica (出厂价), corte 30/jun/2025
- `Mexico-Manhattan-Furnishing 04012026 (1).xlsx` — posible proyecto de Nueva York
- Doc `COOMO` compartido por `esdelirarte@gmail.com`

**Cuenta de la empresa** (avatar "C"):
- `lista de precio cabinets` (antes `墨西哥定制报价.pdf`) — cotización a detalle para México
- `楷模定制技术报价手册 A12版` — **manual técnico de cotización COOMO, versión A12**; contiene la lógica del cálculo rápido
- `BRANDBOOK.pdf`, `BRANDBOOK.ai`, `LOGO.ai`, `LOGO-01.png`, `ACCESO SM`, `iluminacion.pdf`

**Nota:** el manual A12 es la pieza que falta para determinar cuál de las
variantes del Excel es la correcta según COOMO.

---

## 6. Siguientes pasos

1. Leer el manual técnico **A12** y la cotización a detalle.
2. Cruzar los costos del Excel (1015, 1746, 1003, 1304, 344, 1198, 213, 330)
   contra el catálogo de precio de fábrica, para determinar la moneda.
3. Corregir el Excel: columna de margen viva, bandas de altura consistentes,
   referencias reparadas, doble factor de la isla eliminado, puertas de cocina
   incluidas en el total.
4. Añadir un bloque de costeo de importación: TC + flete + arancel + IVA, para
   llegar a precio de venta real.
5. Evaluar una versión web del cotizador en este repositorio.
