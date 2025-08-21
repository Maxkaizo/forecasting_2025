# Cross validation using time series split

Validación correcta para series de tiempo

Lo correcto es usar TimeSeriesSplit (scikit-learn) o un esquema manual de splits donde:

Siempre entrenas en datos anteriores.

Validas en datos posteriores (nunca usas datos futuros para predecir el pasado).

Ejemplo de esquema progresivo:

Fold 1: train = [meses 1–6], valid = [mes 7]

Fold 2: train = [meses 1–7], valid = [mes 8]

Fold 3: train = [meses 1–8], valid = [mes 9]

Y así sucesivamente.

Esto se conoce como expanding window (ventana creciente).
Otra variante es la sliding window, donde mantienes fija la longitud del train y vas desplazando (ej: train últimos 6 meses → valid siguiente mes).

---


Cómo conectar con CRISP-DM

Business Understanding
Ej: “Necesitamos predecir la demanda semanal de productos lácteos para reducir quiebres de stock en 15%”.

Data Understanding
Series de ventas históricas, calendario (festivos, promociones), precios, etc.

Data Preparation
Generación de lag features, ventanas móviles, variables exógenas (ej. clima, campañas).

Modeling
Probar CatBoost, XGBoost, Prophet, LSTM, etc.

Evaluation
Seleccionar métricas: RMSE para sensibilidad a errores grandes, MAPE/sMAPE para comunicar en % al negocio.

Deployment
Pipeline mensual/semanal con monitoreo de drift y dashboards de error en producción.

![alt text](image.png)



---

