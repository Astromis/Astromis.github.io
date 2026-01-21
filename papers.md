---
layout: page
title: Мои статьи
permalink: /papers/
---

## The dataset for presuicidal signals detection in text and its analysis

**Abstract:** The paper says about dataset for presuicidal signal detection in Russian posts from social media. To the best of our knowledge, it is a first dataset of a such type for this language. We develop a collection methodology and conduct linguistic analysis of completed dataset. We also build a classification baseline with machine learning models to solve the detection task.

([paper](./assets/pdf/buyanoviplussochenkovi046.pdf), [doi](https://www.doi.org/10.28995/2075-7182-2022-21-81-98), [code](https://github.com/Astromis/research/tree/master/presuicidal_detection_dataset), [dataset](https://data.mendeley.com/datasets/86v3z38dc7/1))

**Cite**:
```bibtex
@article{Buyanov2022TheDF,
  title={The dataset for presuicidal signals detection in text and its analysis},
  author={Igor Buyanov and Ilya Sochenkov},
  journal={Computational Linguistics and Intellectual Technologies},
  year={2022},
  month={June},
  number={21},
  pages={81--92},
  url={https://api.semanticscholar.org/CorpusID:253195162},
}
```

## Who is answering to whom? Modeling reply-to relationships in Russian asynchronous chats

**Abstract:** The study highlights the asynchronous nature of modern group chats and related problems such as retrieving relevant information on the asked question and understanding reply-to relationships. In this work, we formalize the reply recovery task as a building block toward solving described problems. Using simple heuristics, we try to apply the result reply recovery model to a thread reconstruction problem. As a result, we show that modern pre-trained models such as BERT show great results on the task of reply recovery compared to more simple models, though it cannot be applied to thread reconstruction with just simple heuristics. In addition, experiments have shown that model performance depends on the chat domain. We open-sourced a model that can automatically predict which message the particular reply responds to and provide a representative Russian dataset that we built from Telegram chats of different domains. We also provide a test set for a thread reconstruction task.

([paper](./assets/pdf/buyanoviplusetal046.pdf), [doi](https://www.doi.org/10.28995/2075-7182-2023-22-1052-1060), [code](https://github.com/Astromis/research/tree/master/reply_recovery), [model](https://huggingface.co/astromis/rubert_reply_recovery), [dataset for the reply recovery](https://data.mendeley.com/datasets/xm86yszck2/1), [dataset for the thread reconstruction](https://data.mendeley.com/datasets/7rms5vdhf8/1))

**Cite**:
```bibtex
@article{Buyanov2023WhoIA,
  title={Who is answering to whom? Modeling reply-to relationships in Russian asynchronous chats},
  author={Igor Buyanov and and Darya Yaskova and Ilya Sochenkov},
  journal={Computational Linguistics and Intellectual Technologies (Supplementary volume)},
  year={2023},
  month={June},
  number={22},
  pages={1052--1060},
  url={https://www.dialog-21.ru/media/5871/buyanoviplusetal046.pdf}
}
```

## Нейросетевые методы сжатия векторов для задачи приближенного поиска ближайших соседей

**Аннотация**: В статье проверяется гипотеза применимости нейросетевых автокодировщиков как метод векторного сжатия для задачи приближенного поиска ближайших соседей. Проверка проводилась на нескольких больших датасетах с различными архитектурами автокодировщиков и индексов. Она показала, что, хотя ни одна из комбинаций автокодировщиков и индексов не может полностью превзойти чистые решения, в некоторых случаях они могут быть полезными. Мы также выявили некоторые эмпирические связи оптимальной размерности скрытого слоя и внутренней размерности наборов данных. Было также показано, что функция потерь является определяющим фактором качества сжатия.

([paper](./assets/pdf/Buyanov2024-ps.pdf), [doi](https://doi.org/10.15514/ISPRAS-2024-36(1)-1),)

**Cite**:
```bibtex
@ARTICLE{Buyanov2024-ps,
  title     = "Neural vector compression in approximate nearest neighbor search
               on large datasets",
  author    = "Buyanov, Igor Olegovich and Yadrinsev, Vasiliy Vladimirovich and
               Sochenkov, Ilia Vladimirovich",
  journal   = "Proc. Inst. Syst. Program. RAS",
  publisher = "Institute for System Programming of the Russian Academy of
               Sciences",
  volume    =  36,
  number    =  1,
  pages     = "7--22",
  year      =  2024
}
```

## Transferring Natural Language Datasets Between Languages Using Large Language Models for Modern Decision Support and Sci-Tech Analytical Systems

**Abstract**: The decision-making process to rule R&D relies on information related to current trends in particular research areas. In this work, we investigated how one can use large language models (LLMs) to transfer the dataset and its annotation from one language to another. This is crucial since sharing knowledge between different languages could boost certain underresourced directions in the target language, saving lots of effort in data annotation or quick prototyping. We experiment with English and Russian pairs, translating the DEFT (Definition Extraction from Texts) corpus. This corpus contains three layers of annotation dedicated to term-definition pair mining, which is a rare annotation type for Russian. The presence of such a dataset is beneficial for the natural language processing methods of trend analysis in science since the terms and definitions are the basic blocks of any scientific field. We provide a pipeline for the annotation transfer using LLMs. In the end, we train the BERT-based models on the translated dataset to establish a baseline.

([paper](./assets/pdf/BDCC-09-00116-with-cover.pdf), [doi](https://doi.org/10.3390/bdcc9050116), [code](https://github.com/Astromis/research/tree/master/rudeft), [dataset](https://huggingface.co/datasets/astromis/ruDEFT))

**Cite**:
```bibtex
@article{Popov2025TransferringNL,
  title={Transferring Natural Language Datasets Between Languages Using Large Language Models for Modern Decision Support and Sci-Tech Analytical Systems},
  author={Dmitrii Popov and Egor Terentev and Danil Serenko and Ilya Sochenkov and Igor Buyanov},
  journal={Big Data and Cognitive Computing},
  year={2025},
  url={https://api.semanticscholar.org/CorpusID:278179500}
}
```