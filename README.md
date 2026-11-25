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