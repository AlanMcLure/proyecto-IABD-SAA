# Predicción de precios de viviendas

Proyecto del módulo de Sistemas de Aprendizaje Automático: predecir el precio de las casas de Ames (Iowa), desde la exploración de los datos hasta comparar modelos.

## Contenido

| Archivo | Descripción |
| --- | --- |
| `entregable_Alan_McLure_Alarcon.ipynb` | Proyecto completo |
| `entregable_Alan_McLure_Alarcon.html` | Exportación, para leerlo sin instalar nada |
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

## Ideas para seguir aprendiendo

1. **Separar train, validation y test antes de transformar los datos.** El propio notebook señala que no se hizo porque el enunciado lo simplificaba.
2. **Usar `Pipeline` y `ColumnTransformer`** para evitar filtraciones de datos.
3. **Búsqueda de hiperparámetros** con validación cruzada.
4. **Probar gradient boosting** y explicar el modelo con SHAP.
5. **Publicarlo**: un formulario en Streamlit y una API que prediga el precio.
6. **Hacerlo útil en España**: el mismo enfoque con precios reales de vivienda de tu zona.
