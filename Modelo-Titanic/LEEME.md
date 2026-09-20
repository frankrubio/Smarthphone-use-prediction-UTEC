# Modelo de reporte EDA — Titanic

Ejemplo completo y funcionando de un reporte de análisis exploratorio en Quarto.
El dataset es Titanic (el de seaborn, el mismo de las slides del profe), **no** el
del proyecto del curso: la idea es copiar la estructura, no el contenido.

## Archivos

| Archivo | Qué es |
|---|---|
| `Modelo-EDA.qmd` | El archivo fuente. Es lo que hay que leer e imitar. |
| `Modelo-EDA.pdf` | El resultado ya renderizado (20 páginas). |
| `references.bib` | Las 6 referencias citadas, en formato BibTeX. |
| `datos/titanic.csv` | El dataset, para que corra sin descargar nada. |
| `_extensions/` | La plantilla `report-pdf` del profe, necesaria para renderizar. |

## Cómo renderizarlo

Desde esta carpeta, en una terminal:

```
quarto render Modelo-EDA.qmd
```

La primera vez TinyTeX descargará solo los paquetes de LaTeX que falten
(`lmodern`, `babel-spanish`, `bera`, `mathdesign`, `biblatex` y `biber`).
Eso es normal y solo pasa una vez.

## Las cinco cosas que vale la pena copiar

1. **Un solo chunk de configuración al inicio.** Librerías, paleta de colores y
   funciones de apoyo se definen una vez en `#| label: setup`. Los chunks de
   análisis quedan limpios porque no repiten configuración.

2. **Etiqueta y título en cada figura y tabla.** `#| label: fig-objetivo` +
   `#| fig-cap: "..."`. Con eso Quarto las numera solas, las mete en el índice de
   figuras y permite referenciarlas en el texto con `@fig-objetivo`, que se
   imprime como "Figura 1". Si después se agrega un gráfico en el medio, toda la
   numeración se reacomoda sin tocar nada.

3. **Ningún número escrito a mano.** Cada cifra del texto salió de correr el
   código del propio archivo. Si el dato cambia, el texto sigue siendo cierto
   tras volver a renderizar.

4. **Después de cada bloque de código, un párrafo que lo interpreta.** No basta
   con mostrar el gráfico: hay que decir qué se ve, qué implica y qué se decidió
   por eso. Un gráfico sin lectura no vale nota.

5. **La paleta se define una vez y no cambia.** Dos colores fijos para la
   variable objetivo (azul y ámbar, que se distinguen también en daltonismo e
   impresión en blanco y negro), un gris para las series únicas. El mismo color
   significa lo mismo en todo el documento.

## Equivalencias con el proyecto del curso

La estructura del modelo es la misma de `Project-Report.qmd`, y hay dos paralelos
casi exactos que conviene mirar:

| En el modelo (Titanic) | En el proyecto (smartphone) |
|---|---|
| `alive` reproduce exactamente a `survived` → fuga de información | `nivel_adiccion` frente a `etiqueta_de_adiccion` |
| `class` repite a `pclass` en otro formato → redundancia | `tiempo_en_pantalla_fin_de_semana` frente a `horas_diarias_pantalla` (r ≈ 0.96) |

La sección 4.1 del modelo muestra cómo se audita y se documenta esa decisión.
