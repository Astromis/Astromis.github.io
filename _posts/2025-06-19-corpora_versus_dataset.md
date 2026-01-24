--- 
layout: post 
author: Astromis 
title: Corpora versus dataset. What is the difference?
use_math: false
--- 

_Дисклеймер: Оригинальная статья размещалась на давно почившем сайте "Corpus linguistic methods" по [этому адресу](https://corpuslinguisticmethods.wordpress.com/2013/12/28/corpora-versus-datasets/
). Часть ссылок в статье не работают, потому что ведут на тот же сайт. Возможно, их можно найти на Wayback Machine. Этот текст был сохранен у меня в документе, где я разбирался в разнице понятий «корпус» и «датасет». Считаю, что текст в целом эту разницу определяет._

As a corpus linguist, the terms _corpus_ and _dataset_ are sometimes very confusing. Indeed, they are very similar:
* both contain linguistic production,
* both usually provide further information about the production in the form of annotations,
* these annotations can be linguistic in nature, but may also reveal meta-information about the language producer, or the context in which the production found place.

In fact, some people would go so far as to say that there is no difference between a corpus and a dataset. However, I do not agree and I would like to suggest a prototype-based approach.
For both a corpus and a dataset, I stick to the following two minimal definitions:
* A corpus is a representative sample of _actual language production_ within a _meaningful context_ and with a _general purpose_.
* A dataset is a representative sample of a _specific linguistic phenomenon_ in a _restricted context_ and with annotations that relate to a _specific research question_.

The prototypical corpus and the prototypical dataset can thus be summarized in the following table:

|          | Prototypical corpus     | Prototypical dataset |
|----------|-------------------------|----------------------|
| Language | unrestricted production | specific phenomenon  |
| Context  | wide                    | restricted           |
| Purpose  | general                 | research question    |

Now, obviously, these prototypical cores do not necessarily correspond to all corpora and datasets out there. Let me nonetheless give some extreme examples. As a prototypical corpus, I consider the [Usenet corpus of Westbury](http://www.psych.ualberta.ca/~westburylab/downloads/usenetcorpus.download.html). This corpus is pure text downloaded from Usenet servers and presented as is (except for a couple of clean-up measurements). There is no restriction on the context, and everybody is in principle free to use it for whatever research question they like. A prototypical dataset is for me the [horse name corpus](http://corplinguistics.wordpress.com/2013/06/06/horse-name-corpus-for-belmont-stakes/) (yes, it is called a corpus, let the troubles begin). There is only a very specific phenomenon sampled in the data (horse names), and there is actually no context whatsoever. Although you can think up a small amount of research questions for this data, it is quite obvious that the purpose is much more limited than the Usenet corpus.

In reality, however, corpora and datasets are somewhat of a mix between the two. Most corpora are annotated (with part-of-speech, lemmatized, syntax, named entities, etc.) and do not contain full texts (usually paragraphs or chapters, snippets, fragments) for copyright reasons. And often, corpora are compiled with a certain research question in mind. Vice versa, datasets are often based on Keywords in Context, so that they in fact also contain a relatively wide context, so that they could be used for other research questions on different linguistic phenomena, too.

For me, however, there is one distinctive characteristic that sets corpora and datasets apart from each other. [Datasets are in the unstacked format](https://corpuslinguisticmethods.wordpress.com/2013/12/12/how-to-build-a-dataset-for-a-corpuslinguistic-study/) and [freely](https://corpuslinguisticmethods.wordpress.com/2013/12/19/share-your-datasets/) [distributed as csv files](https://corpuslinguisticmethods.wordpress.com/2013/12/13/save-your-datasets-as-csv-files/), whereas corpora may have a wide range of formats (vertical, xml, graphs).
