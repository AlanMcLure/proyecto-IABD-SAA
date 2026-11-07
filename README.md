# Predicción de precios de viviendas

Proyecto del módulo de Sistemas de Aprendizaje Automático: predecir el precio de las casas de Ames (Iowa), desde la exploración de los datos hasta comparar modelos.

## Contenido

| Archivo | Descripción |
| --- | --- |
| `entregable_Alan_McLure_Alarcon.ipynb` | Proyecto completo |
| `entregable_Alan_McLure_Alarcon.html` | Exportación, para leerlo sin instalar nada |
| `experimento_pipeline.ipynb` | Revisión del modelo: evaluación contra el precio real, sin fugas de datos y con validación temporal |
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

Los experimentos se abren igual, cambiando el nombre del archivo.

## Resultados de la revisión

`experimento_pipeline.ipynb` reproduce las métricas de la entrega y después las corrige. Resultados en test (ventas de enero a julio de 2010):

| Modelo | Se mide contra | MAE | R² |
| --- | --- | --- | --- |
| Random forest de la entrega | Precio recortado | $14.064 | 0,890 |
| El mismo modelo | Precio real | $18.389 | 0,809 |
| Gradient boosting con `log(precio)`, ajustado | Precio real | $13.330 | 0,925 |

Las conclusiones y los límites están al final del notebook.

## Ideas para seguir aprendiendo

1. **Explicar el modelo con SHAP.** El experimento ya separa los datos antes de transformarlos, usa `Pipeline`, busca hiperparámetros con validación temporal y prueba gradient boosting.
2. **Publicarlo**: un formulario en Streamlit y una API que prediga el precio.
3. **Hacerlo útil en España**: el mismo enfoque con precios reales de vivienda de tu zona.
