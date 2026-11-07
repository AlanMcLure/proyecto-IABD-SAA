# Predicción de precios de viviendas

Proyecto del módulo de Sistemas de Aprendizaje Automático: predecir el precio de las casas de Ames (Iowa), desde la exploración de los datos hasta comparar modelos.

## Contenido

| Archivo | Descripción |
| --- | --- |
| `entregable_Alan_McLure_Alarcon.ipynb` | Proyecto completo |
| `entregable_Alan_McLure_Alarcon.html` | Exportación, para leerlo sin instalar nada |
| `experimento_pipeline.ipynb` | Revisión del modelo: evaluación contra el precio real, sin fugas de datos y con validación temporal |
| `experimento_valencia.ipynb` | El mismo método con pisos anunciados en València en 2018. Descarga sus datos en `data_valencia/` |
| `data/house-price-data.csv` | Datos |
| `data/data_description.txt` | Descripción de las columnas |

## Ejecutarlo

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt jupyter
jupyter notebook entregable_Alan_McLure_Alarcon.ipynb
```

> El notebook es la entrega original: no se modifica. Para experimentar, crea otro.

Los experimentos se abren igual, cambiando el nombre del archivo. `experimento_valencia.ipynb` necesita conexión la primera vez para descargar sus datos.

## Resultados de la revisión

`experimento_pipeline.ipynb` reproduce las métricas de la entrega y después las corrige. Resultados en test (ventas de enero a julio de 2010):

| Modelo | Se mide contra | MAE | R² |
| --- | --- | --- | --- |
| Random forest de la entrega | Precio recortado | $14.064 | 0,890 |
| El mismo modelo | Precio real | $18.389 | 0,809 |
| Gradient boosting con `log(precio)`, ajustado | Precio real | $13.330 | 0,925 |

Las conclusiones y los límites están al final del notebook.

## Modelo para València

`experimento_valencia.ipynb` predice el precio **anunciado** de pisos en 2018: no es un precio de venta ni un precio actual. Resultados en el cuarto trimestre de 2018, entrenando con los tres anteriores:

| Modelo | MAE | MAPE | R² |
| --- | --- | --- | --- |
| Precio por m² de la zona | 50.217 € | 24,4 % | 0,748 |
| Gradient boosting con `log(precio)`, ajustado | 35.934 € | 16,6 % | 0,852 |

El notebook también reescala las estimaciones a 2026 con el [valor tasado del municipio](https://apps.fomento.gob.es/BoletinOnline2/sedal/35103500.XLS) (Ministerio de Vivienda y Agenda Urbana). Es una orientación a nivel de ciudad, sin validar para zonas ni pisos concretos: el factor va de 2,15 a 2,32 y, al probarlo dentro de 2018, el índice no mejoró la predicción.

Contiene información de [`idealista18`](https://github.com/paezha/idealista18) (Rey-Blanco, Arbués, López y Páez), disponible bajo la licencia [Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/). Los autores añadieron ruido a precios y coordenadas para proteger la privacidad. Esos datos no se incluyen en este repositorio: el notebook los descarga y comprueba su hash.

## Ideas para seguir aprendiendo

1. **Explicar el modelo con SHAP.** El experimento ya separa los datos antes de transformarlos, usa `Pipeline`, busca hiperparámetros con validación temporal y prueba gradient boosting.
2. **Publicarlo**: un formulario en Streamlit y una API que prediga el precio.
3. **Actualizar el modelo de València** con precios más recientes o de compraventas reales, si se encuentra una fuente abierta con datos por vivienda.
