---
title: 'Aplicación de ingeniería de características para el entrenamiento del modelo en datos textuales: ML.NET'
description: Obtenga información sobre cómo aplicar ingeniería de características para el entrenamiento de modelos en datos textuales con ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ed24561c8cc821ece8a21ca61e22a11bda2516d1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297642"
---
# <a name="apply-feature-engineering-for-machine-learning-model-training-on-textual-data-with-mlnet"></a>Aplicación de ingeniería de características para el entrenamiento del modelo de Machine Learning en datos textuales con ML.NET

Debe convertir todos los datos que no sean de tipo float en tipos de datos `float`, ya que los elementos `learners` de ML.NET esperan características como elemento `float vector`.

Para obtener más información sobre los datos de texto, tendrá que extraer características de texto. ML.NET tiene algunos mecanismos básicos de extracción de características de texto:

- `Text normalization` (eliminación de signos de puntuación, marcas diacríticas, cambio a minúsculas, etc.)
- `Separator-based tokenization`.
- Eliminación de `Stopword`.
- Extracción de `Ngram` y `skip-gram`.
- Cambio de la escala de `TF-IDF`.
- Conversión de `Bag of words`.

En el ejemplo siguiente se muestran los mecanismos de extracción de características de texto de ML.NET mediante el [conjunto de datos detox de Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):

```console
Sentiment   SentimentText
1   Stop trolling, zapatancas, calling me a liar merely demonstartes that you arer Zapatancas. You may choose to chase every legitimate editor from this site and ignore me but I am an editor with a record that isnt 99% trolling and therefore my wishes are not to be completely ignored by a sockpuppet like yourself. The consensus is overwhelmingly against you and your trolling lover Zapatancas,  
1   ::::: Why are you threatening me? I'm not being disruptive, its you who is being disruptive.   
0   " *::Your POV and propaganda pushing is dully noted. However listing interesting facts in a netral and unacusitory tone is not POV. You seem to be confusing Censorship with POV monitoring. I see nothing POV expressed in the listing of intersting facts. If you want to contribute more facts or edit wording of the cited fact to make them sound more netral then go ahead. No need to CENSOR interesting factual information. "
0   ::::::::This is a gross exaggeration. Nobody is setting a kangaroo court. There was a simple addition concerning the airline. It is the only one disputed here.   
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        new TextLoader.Column("IsToxic", DataKind.BL, 0),
        new TextLoader.Column("Message", DataKind.TX, 1),
    },
    HasHeader = true
});

// Read the data.
var data = reader.Read(dataPath);

// Inspect the message texts that are read from the file.
var messageTexts = data.GetColumn<string>(mlContext, "Message").Take(20).ToArray();

// Apply various kinds of text operations supported by ML.NET.
var pipeline =
    // One-stop shop to run the full text featurization.
    mlContext.Transforms.Text.FeaturizeText("Message", "TextFeatures")

    // Normalize the message for later transforms
    .Append(mlContext.Transforms.Text.NormalizeText("Message", "NormalizedMessage"))

    // NLP pipeline 1: bag of words.
    .Append(new WordBagEstimator(mlContext, "NormalizedMessage", "BagOfWords"))

    // NLP pipeline 2: bag of bigrams, using hashes instead of dictionary indices.
    .Append(new WordHashBagEstimator(mlContext, "NormalizedMessage", "BagOfBigrams",
                ngramLength: 2, allLengths: false))

    // NLP pipeline 3: bag of tri-character sequences with TF-IDF weighting.
    .Append(mlContext.Transforms.Text.TokenizeCharacters("Message", "MessageChars"))
    .Append(new NgramEstimator(mlContext, "MessageChars", "BagOfTrichar",
                ngramLength: 3, weighting: NgramTransform.WeightingCriteria.TfIdf))

    // NLP pipeline 4: word embeddings.
    .Append(mlContext.Transforms.Text.TokenizeWords("NormalizedMessage", "TokenizedMessage"))
    .Append(mlContext.Transforms.Text.ExtractWordEmbeedings("TokenizedMessage", "Embeddings",
                WordEmbeddingsTransform.PretrainedModelKind.GloVeTwitter25D));

// Let's train our pipeline, and then apply it to the same data.
// Note that even on a small dataset of 70KB the pipeline above can take up to a minute to completely train.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var embeddings = transformedData.GetColumn<float[]>(mlContext, "Embeddings").Take(10).ToArray();
var unigrams = transformedData.GetColumn<float[]>(mlContext, "BagOfWords").Take(10).ToArray();
```
