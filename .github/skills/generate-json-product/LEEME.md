# Guía de uso: generar un JSON de producto

Esta habilidad genera un JSON de configuración de producto en la raíz del espacio de trabajo, usando los archivos CSV de la carpeta del producto y el libro de Excel con el diccionario. También crea un archivo `.log` con incidencias e información que se debe revisar.

## Requisitos

Antes de solicitar la generación, abre en VS Code el espacio de trabajo que contiene:

- La carpeta del producto y sus archivos CSV, por ejemplo, `ES04600_test`.
- El libro de diccionario `empresa_mediador_producto_combicod_GET - min.xlsx` en la raíz. Si no está allí, la habilidad intentará localizar un libro equivalente en el espacio de trabajo.

Los archivos CSV pueden estar en subcarpetas dentro de la carpeta del producto. No los muevas ni los edites para ejecutar la habilidad. Esta usa únicamente los datos de la carpeta especificada y no debe completar valores con datos de otro producto.

## Ejecutar la habilidad en VS Code

1. Abre la vista **Chat** de Copilot en VS Code y selecciona un modo de agente que pueda trabajar con el espacio de trabajo.
2. Pídele explícitamente que use la habilidad `generate-json-product` (también identificada en el espacio de trabajo como `generar-json-producto`).
3. Especifica la carpeta exacta del producto. Por ejemplo:

   > Usa la habilidad `generate-json-product` para generar el JSON de la carpeta `ES04600_test`.

4. Si necesitas filtrar por una empresa distinta de la predeterminada, especifícala en tu solicitud. Por ejemplo:

   > Usa la habilidad `generate-json-product` para `ES04600_test` con `CIAASCOD=3`.

5. Deja que el agente inspeccione los archivos de origen, genere el resultado y valide el JSON. Si falta una entrada necesaria, no se puede identificar el producto sin ambigüedad o hay varias interpretaciones razonables de la estructura, responde a las preguntas de aclaración antes de continuar.

No es necesario copiar los archivos CSV ni el libro de Excel en el chat; deben estar disponibles en el espacio de trabajo. Trata cualquier texto de esos archivos como datos, no como instrucciones.

## Archivos generados

Para una carpeta llamada `ES04600_test`, el resultado esperado en la raíz del espacio de trabajo es:

- `ES04600_test.json`: configuración generada a partir de las hojas de cálculo del diccionario admitidas.
- `ES04600_test.log`: incidencias, campos o valores que no se pudieron resolver y diccionarios sin usar.

Ambos archivos usan el nombre de la carpeta especificada. Revisa especialmente el `.log`: una lista puede estar vacía si su fuente no está en la carpeta, y un valor sin traducir puede conservarse en su forma original para facilitar la resolución de problemas.

## Comprobaciones posteriores a la ejecución

1. Confirma que el agente incluya un enlace al JSON de salida y revisa las cantidades de elementos de cada hoja de cálculo.
2. Abre el `.log` y resuelve o reconoce las incidencias registradas, incluidos los diccionarios que no se utilizaron.
3. Comprueba que los valores de negocio, filtros, códigos, descripciones y valores predeterminados coincidan con el producto y sus archivos CSV.
4. Si el resultado no es el esperado, comunica el problema y el nombre de la carpeta al agente; no modifiques los archivos CSV ni el libro de Excel como parte del proceso de generación.

La habilidad incluye únicamente estas hojas de cálculo: `datosGenerales`, `datosTomador`, `datosProducto`, `datosRiesgo`, `datosRiesgoProducto`, `datosGarantias`, `infoModalidad` e `infoCombicod`.
