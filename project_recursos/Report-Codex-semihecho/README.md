# Report-Codex - Entrega P1

Proyecto reproducible para la P1 de **Introduccion a Ciencia de Datos e Inteligencia Artificial**. Analiza el dataset `Smartphone Usage and Addiction Analysis` sin entrenar modelos; el modelamiento pertenece a P2.

## Contenido

- `P1-Smartphone-Addiction.qmd`: reporte Quarto con analisis, tablas, figuras y referencias.
- `p_datos/Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv`: dataset usado por el reporte.
- `references.bib`: fuentes bibliograficas citadas en el documento.
- `_extensions/numbats/report/`: extension y estilo de portada del template UTEC.
- `Report-Codex.Rproj`: archivo de proyecto para abrir la carpeta con RStudio o Positron.
- `requirements.txt`: dependencias de Python necesarias para ejecutar las celdas del reporte.

## Requisitos

1. Quarto (version 1.4 o posterior).
2. Una distribucion LaTeX con `pdflatex` (MiKTeX funciona en Windows).
3. Python 3.10 o posterior con las dependencias de `requirements.txt`.

Instalar las bibliotecas de Python:

```powershell
python -m pip install -r requirements.txt
```

## Generar el reporte

Desde esta carpeta, ejecutar:

```powershell
quarto render P1-Smartphone-Addiction.qmd
```

El resultado sera `P1-Smartphone-Addiction.pdf`. El documento genera sus tablas y graficos directamente del CSV. No se deben editar manualmente resultados ni figuras: basta con actualizar el dataset y volver a renderizar.

## Decisiones analiticas importantes

- Hay 819 celdas vacías exclusivamente en `addiction_level`; representan el nivel `None` y no se imputan porque la columna se elimina por fuga de información. No hay filas duplicadas completas.
- Se excluyen `transaction_id` y `user_id` de futuros predictores por ser identificadores.
- Se excluye `addiction_level` de P2 por fuga de informacion: determina exactamente `addicted_label` en este archivo.
- La P1 no contiene modelos. La P2 debera usar division estratificada, codificacion realizada dentro del flujo de entrenamiento y metricas como F1, precision, recall y matriz de confusion.
