---
layout: page
title: About
permalink: /about/
---

# General

Hello, I'm Igor Buyanov, natural language processing researcher.

You can check out my CV on [LinkedIn](https://www.linkedin.com/in/igor-buyanov/).

You may contact with me by 
* Email: buyanov.igor.o@yandex.ru
* Telegram: [@Astromis](https://t.me/Astromis)

# Papers

## The dataset for presuicidal signals detection in text and its analysis

**Abstract:** The paper says about dataset for presuicidal signal detection in Russian posts from social media. To the best of our knowledge, it is a first dataset of a such type for this language. We develop a collection methodology and conduct linguistic analysis of completed dataset. We also build a classification baseline with machine learning models to solve the detection task.

([paper](./assets/pdf/buyanoviplussochenkovi046.pdf), [code](https://github.com/Astromis/research/tree/master/presuicidal_detection_dataset), [dataset](https://data.mendeley.com/datasets/86v3z38dc7/1))

**Cite**:
```bibtex
@article{Buyanov2022TheDF,
  title={The dataset for presuicidal signals detection in text and its analysis},
  author={Igor Buyanov and Ilya Sochenkov},
  journal={Computational Linguistics and Intellectual Technologies},
  year={2022},
  url={https://api.semanticscholar.org/CorpusID:253195162}
}
```

## Who is answering to whom? Modeling reply-to relationships in Russian asynchronous chats

**Abstract:** The study highlights the asynchronous nature of modern group chats and related problems such as retrieving relevant information on the asked question and understanding reply-to relationships. In this work, we formalize the reply recovery task as a building block toward solving described problems. Using simple heuristics, we try to apply the result reply recovery model to a thread reconstruction problem. As a result, we show that modern pre-trained models such as BERT show great results on the task of reply recovery compared to more simple models, though it cannot be applied to thread reconstruction with just simple heuristics. In addition, experiments have shown that model performance depends on the chat domain. We open-sourced a model that can automatically predict which message the particular reply responds to and provide a representative Russian dataset that we built from Telegram chats of different domains. We also provide a test set for a thread reconstruction task.

([paper](./assets/pdf/buyanoviplusetal046.pdf), [code](https://github.com/Astromis/research/tree/master/reply_recovery), [model](https://huggingface.co/astromis/rubert_reply_recovery), [dataset for the reply recovery](https://data.mendeley.com/datasets/xm86yszck2/1), [dataset for the thread reconstruction](https://data.mendeley.com/datasets/7rms5vdhf8/1))

**Cite**:
```bibtex
@article{Buyanov2023WhoIA,
  title={Who is answering to whom? Modeling reply-to relationships in Russian asynchronous chats},
  author={Igor Buyanov and and Darya Yaskova and Ilya Sochenkov},
  journal={Computational Linguistics and Intellectual Technologies},
  year={2023},
  url={https://www.dialog-21.ru/media/5871/buyanoviplusetal046.pdf}
}
```

