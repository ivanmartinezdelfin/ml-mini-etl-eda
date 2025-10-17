# Mini-ETL & EDA (Nivel 0-1)

**objetivo:** leer CSV/JSON, limpiar nulos/outliers, generar KPIs y gráficos.
**Stack:** Python, Pandas, scikit-lear, matplotlib (ydata-profiling opcional).

## Flujo Natural
1.**Ingesta** (`src/utils_io.py`): leer CSV/JSON y unificar esquema.
2.**Limpieza**(`src/data_cleaning.py`): nulos, outliers (IQR), tipos; guardar ``data/processed/clean.csv`.
3.**EDA** (`notebooks/01_eda.ipynb`): KPIS, gráficos. ``make eda` genera `reports/eda.html`.
**Features** (`src/features/build_features.py`): `ColumnTransformer` con *imputers*, `OneHotEncoder`, bins, datetime & texto; exporta `models/feature_store.parquet`.
5.**Tests**(`pytest`): validan funciones clave.
6.**Makefile**: atajos (`make eda`, `make features`, `make test`).

## Datos de ejemplo
Coloca un CSV/JSON en `data/raw/` (ej. `data/raw/sample.csv`).
Debe tener columnas numéricas y categóricas; si incluye fechas o texto, mejor:
- `amount` (num), `category` (cat), `date` (fecha), `description` (texto), `target` (opcional).
