---
title: Transformaciones de datos
description: Explore las diferentes transformaciones de datos que se admiten en ML.NET.
ms.date: 10/16/2018
ms.openlocfilehash: 5df4598de6fcd08689d72c378f51d792860ef49c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187746"
---
# <a name="data-transforms"></a>Transformaciones de datos

En las tablas siguientes se incluye información sobre todas las transformaciones de datos admitidas en ML.NET (seleccione el tipo de transformación de datos para navegar a la tabla correspondiente):

* [Categóricas](#categorical)
* [Combinadores y segregadores](#combiners-and-segregators)
* [Selección de características](#feature-selection)
* [Caracterizadores](#featurizers)
* [Análisis de etiquetas](#label-parsing)
* [Valores ausentes](#missing-values)
* [Normalización](#normalization)
* [Filtros de fila](#row-filters)
* [Esquema](#schema)
* [Características y procesamiento de texto](#text-processing-and-featurization)
* [Varios](#miscellaneous)

> [!NOTE]
> ML.NET se encuentra actualmente en versión preliminar. En la actualidad no se admiten todas las transformaciones de datos. Para enviar una solicitud para una transformación determinada, abra un tema en el repositorio [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) de GitHub.

## <a name="categorical"></a>Categóricas

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalHashOneHotVectorizer> | Codifica la variable de categoría con codificación basada en código hash. |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer> | Codifica la variable de categoría con codificación uno activo en función de un diccionario de términos. |

## <a name="combiners-and-segregators"></a>Combinadores y segregadores

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CombinerByContiguousGroupId> | Agrupa los valores de una columna escalar en un vector en función de un identificador de grupo contiguo. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Combina todas las características en una columna de características. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Combina una secuencia de TransformModels y un PredictorModel en un único PredictorModel. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Combina una secuencia de TransformModels en un único modelo. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Desagrupa todas las columnas de vector en secuencias de filas; es la transformación inversa a Group. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Combina un TransformModel y un PredictorModel en un único PredictorModel. |

## <a name="feature-selection"></a>Selección de características

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByCount> | Selecciona las ranuras para las que el recuento de valores no predeterminados es mayor o igual que un umbral. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByMutualInformation> | Selecciona las ranuras k principales entre todas las columnas especificadas ordenadas por su información mutua con la columna de etiqueta. |

## <a name="featurizers"></a>Caracterizadores

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Convierte los valores de columna en valores hash. Esta transformación acepta entradas numéricas y de texto, en columnas de un solo valor y de valores de vector. |
| <xref:Microsoft.ML.Legacy.Transforms.TreeLeafFeaturizer> | Entrena un TreeEnsemble, o bien lo carga desde un archivo y, después, asigna un vector de características numérico a tres salidas: 1. Un vector que contiene las salidas de árbol individual del TreeEnsemble. 2. Vector que indica las hojas del TreeEnsemble donde se encuentra el vector de características. 3. Vector que indica las rutas de acceso del TreeEnsemble donde se encuentra el vector de características. Si se especifican un archivo de modelo y un instructor, el vector usará el archivo de modelo. Si no se especifica ninguno, el vector entrenará un modelo FastTree predeterminado. Esto puede controlar las etiquetas de clave mediante el entrenamiento de un modelo de regresión hacia sus índices permutados de forma opcional. |

## <a name="label-parsing"></a>Análisis de etiquetas

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Convierte valores de entrada (palabras, números, etc.) en el índice de un diccionario. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Transforma la etiqueta en una clave o un valor booleano (si es necesario) para adecuarla para la clasificación. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelIndicator> | Reasignador de etiquetas que se usa en OVA. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Transforma la etiqueta a un valor float para adecuarla para la regresión. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Transforma una columna de etiqueta prevista a sus valores originales, a menos que sea de tipo bool. |

## <a name="missing-values"></a>Valores ausentes

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueHandler> | Controla los valores que faltan y los sustituye por el valor predeterminado o el valor medio, mínimo o máximo (solo para las columnas que no sean de texto). Opcionalmente, se puede concatenar una columna de indicador si el tipo de la columna de entrada es numérico. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueIndicator> | Crea una columna de salida booleana con el mismo número de ranuras que la columna de entrada, donde el valor de salida es true si falta el valor en la columna de entrada. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesDropper> | Quita los NA de las columnas de vector. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesRowDropper> | Filtra las filas que contienen valores que faltan. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueSubstitutor> | Crea una columna de salida del mismo tipo y tamaño que la columna de entrada, donde los valores que faltan se reemplazan con el valor predeterminado o el valor medio, mínimo o máximo (solo para las columnas que no sean de texto). |

## <a name="normalization"></a>Normalización

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.BinNormalizer> | Los valores se asignan en contenedores de equidensidad y se asigna un valor a su número_de_contenedor / número_de_contenedores. |
| <xref:Microsoft.ML.Legacy.Transforms.ConditionalNormalizer> | Normaliza las columnas solo si es necesario. |
| <xref:Microsoft.ML.Legacy.Transforms.GlobalContrastNormalizer> | Realiza una normalización de contraste global en los valores de entrada: Y = (s * X - M) / D, donde s es una escala, M es la media y D es la norma L2 o la desviación estándar. | 
| <xref:Microsoft.ML.Legacy.Transforms.LogMeanVarianceNormalizer> | Normaliza los datos en función de la media calculada y la varianza del logaritmo de los datos. |
| <xref:Microsoft.ML.Legacy.Transforms.LpNormalizer> | Normaliza los vectores (filas) de forma individual volviéndolos a escalar a la norma de unidad (L2, L1 o LInf). Realiza la operación siguiente en un vector X: Y = (X - M) / D, donde M es la media y D es la norma L2, L1 o LInf. |
| <xref:Microsoft.ML.Legacy.Transforms.MeanVarianceNormalizer> | Normaliza los datos en función de la media calculada y la varianza de los datos. |
| <xref:Microsoft.ML.Legacy.Transforms.MinMaxNormalizer> | Normaliza los datos en función de los valores mínimo y máximo observados de los datos. |

## <a name="row-filters"></a>Filtros de fila

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.RowRangeFilter> | Filtra una vista de datos en una columna de tipo Single, Double o Key (contigua). Mantiene los valores que se encuentran en el intervalo mínimo y máximo especificado. Los valores NaN se filtran siempre. Si la entrada es un tipo de clave, los valores mínimo y máximo se consideran porcentajes del número de valores. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipAndTakeFilter> | Permite limitar la entrada a un subconjunto de filas con un desplazamiento opcional. Se puede usar para implementar la paginación de datos. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipFilter> | Permite limitar la entrada a un subconjunto de filas mediante la omisión de un número de filas. |
| <xref:Microsoft.ML.Legacy.Transforms.RowTakeFilter> | Permite limitar la entrada a un subconjunto de filas tomando las primeras N filas. |

## <a name="schema"></a>Schema

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> | Concatena dos columnas del mismo tipo de elemento. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> | Duplica las columnas del conjunto de datos.|
| <xref:Microsoft.ML.Legacy.Transforms.ColumnDropper> | Quita columnas del conjunto de datos. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnSelector> | Selecciona un conjunto de columnas y quita todas las demás. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnTypeConverter> | Convierte una columna a otro tipo, mediante conversiones estándar. |
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform usa metadatos de KeyValues para asignar índices de clave a los valores correspondientes en los metadatos de KeyValues. |
| <xref:Microsoft.ML.Legacy.Transforms.NGramTranslator> | Genera un contenedor de los recuentos de n-gramas (secuencias de valores consecutivos de longitud 1-n) en un vector de claves especificado. Lo hace mediante la creación de un diccionario de n-gramas y con el identificador del diccionario como el índice del contenedor. | 
| <xref:Microsoft.ML.Legacy.Transforms.OptionalColumnCreator> | Si después de la deserialización la columna de origen no existe, crea una columna con el tipo y los valores predeterminados correctos. |

## <a name="text-processing-and-featurization"></a>Características y procesamiento de texto

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CharacterTokenizer> | Tokenizador orientado a caracteres donde el texto se considera una secuencia de caracteres. |
| <xref:Microsoft.ML.Legacy.Transforms.TextFeaturizer> | Una transformación que convierte una colección de documentos de texto en vectores de características numéricos. Los vectores de características son recuentos normalizados de n-gramas (palabras o caracteres) en un texto con tokens determinado. |
| <xref:Microsoft.ML.Legacy.Transforms.TextToKeyConverter> | Convierte valores de entrada (palabras, números, etc.) en el índice de un diccionario. |
| <xref:Microsoft.ML.Legacy.Transforms.WordEmbeddings> | Una transformación que convierte los vectores de tokens de texto en vectores numéricos mediante un modelo previamente entrenado. Para obtener más información sobre la técnica, vea la página de Wikipedia [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) (Inserción de palabras). |
| <xref:Microsoft.ML.Legacy.Transforms.WordTokenizer> | La entrada de esta transformación es texto y el resultado es un vector de texto que contiene las palabras (tokens) en el texto original. El separador es un espacio, pero se puede especificar cualquier otro carácter (o varios). |

## <a name="miscellaneous"></a>Varios

| Transformación | de esquema JSON |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ApproximateBootstrapSampler> | Muestreo de arranque aproximado. |
| <xref:Microsoft.ML.Legacy.Transforms.BinaryPredictionScoreColumnsRenamer> | Para la predicción binaria, cambia el nombre de las columnas PredictedLabel y Score para incluir el nombre de la clase positiva.|
| <xref:Microsoft.ML.Legacy.Transforms.DataCache> | Almacena en caché con la opción de caché especificada. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetScorer> | Puntúa un conjunto de datos con un modelo de predicción. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetTransformScorer> | Puntúa un conjunto de datos con un modelo de transformación. |
| <xref:Microsoft.ML.Legacy.Transforms.NoOperation> | No hace nada. |
| <xref:Microsoft.ML.Legacy.Transforms.RandomNumberGenerator> | Agrega una columna con una secuencia de números generada. |
| <xref:Microsoft.ML.Legacy.Transforms.ScoreColumnSelector> | Selecciona solo las columnas de la última puntuación y las columnas adicionales especificadas en los argumentos. |
| <xref:Microsoft.ML.Legacy.Transforms.Scorer> | Convierte el modelo de predicción en un modelo de transformación. |
| <xref:Microsoft.ML.Legacy.Transforms.SentimentAnalyzer> | Usa un modelo de opinión previamente entrenado para puntuar las cadenas de entrada. |
| <xref:Microsoft.ML.Legacy.Transforms.TrainTestDatasetSplitter> | Divide el conjunto de datos en conjuntos de entrenamiento y prueba. |
