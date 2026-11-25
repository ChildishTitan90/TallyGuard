# TallyGuard

TallyGuard es un proyecto de aprendizaje en equipo sobre detección de fraude y riesgo de crédito. El primer sprint prepara el entorno y construye un modelo de referencia para detectar fraude en transacciones.

## Configuración local

El proyecto usa Python 3.12 y `uv`. Para instalar `uv`, consulta la [guía oficial](https://docs.astral.sh/uv/getting-started/installation/).

Clona el repositorio e instala las dependencias desde el archivo `uv.lock`:

```powershell
git clone https://github.com/ChildishTitan90/TallyGuard.git
cd TallyGuard
uv sync --locked
```

Comprueba que el entorno funciona:

```powershell
uv run --locked python -c "import pandas, sklearn, joblib; print('Entorno listo')"
```

El comando debe mostrar `Entorno listo`.

## Estructura del proyecto

```text
data/
  raw/         CSV originales descargados
  processed/   Datos generados por el preprocesamiento
  docs/        Documentos de referencia y políticas del proyecto
models/        Modelos entrenados y sus metadatos locales
notebooks/     Exploración y experimentos del equipo
src/           Código reutilizable de preparación y entrenamiento
tests/         Pruebas del código del proyecto
```

## Datos de fraude

Descarga los cinco archivos de [IEEE-CIS Fraud Detection](https://www.kaggle.com/competitions/ieee-fraud-detection/data) y colócalos directamente en `data/raw/`. Conserva los nombres originales.

- `train_transaction.csv` contiene las transacciones etiquetadas con `isFraud`. Es el archivo para la exploración inicial y la división temporal de H02.
- `train_identity.csv` contiene datos de identidad que se pueden vincular mediante `TransactionID`.
- `test_transaction.csv` y `test_identity.csv` pertenecen al conjunto de evaluación de Kaggle. La prueba interna del equipo se reserva dentro de `train_transaction.csv`.
- `sample_submission.csv` es la plantilla de entrega de la competencia.

Cada integrante descarga su copia. Git ignora los datos originales, los datos procesados y los modelos generados.

## Consulta de políticas

En H24 se configurará PostgreSQL con la extensión pgvector. Los documentos fuente se guardarán en `data/docs/`. PostgreSQL almacenará los fragmentos, sus embeddings y los datos de referencia que usará el agente para citar el documento, la página y la versión de cada política.
