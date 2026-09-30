# Diario de depuración

## 1. Comprensión del informe
- Comportamiento esperado: La validación debe terminar con "EL catálogo es válido"
- Comportamiento observado: La aplicación busca "weather.uvl" dentro de "models/" e informa de que el fichero no existe
- Información del entorno relevante: Linux. Variables de entorno CATALOG_FILE=external/catalog.csv. UVL_MODELS_DIR=externa/models
- Información que falta o que pediríamos: 

## 2. Reproducción
- Comandos ejecutados: 
export CATALOG_FILE=external/catalog.csv
export UVL_MODELS_DIR=external/models
python validate.py
- Evidencia obtenida: 
 Línea 2: no existe models/weather.uvl
- ¿Se ha reproducido de forma consistente?:  Sí

## 3. Hipótesis y diagnóstico
- Primera hipótesis:Error en la funcion de la ruta
- Comprobación realizada:Observada la función get_models_dir() para comprobar si devolvía bien la ruta
- Causa raíz: La función get_models_dir estaba retornando siempre "models"

## 4. Reparación y validación
- Prueba de regresión añadida: test_models_directory_can_be_configured
- Cambio realizado: Añadida la ruta relativa a la variable de entorno
- Comandos de validación: python validate.py
- Resultado: El catálogo es válido ahora

## 5. Trazabilidad
- Número o URL de la incidencia: 
- Commit que la corrige:
