# Introduction

This repository contains a description on how to use [OpenNMT](https://opennmt.net/) on the Grammar Error Correction (GEC) task. 
The idea is to approch GEC as a translation task

# Quick start

Quick start with pre-trained model

```bash
wget https://www.softcatala.org/pub/softcatala/opennmt/models/gec-english/gec-english-2021-11-11.zip
unzip gec-english-2021-11-11.zip
```


```python

import pyonmttok
tokenizer=pyonmttok.Tokenizer(mode="none", sp_model_path = "tokenizer/sp_m.model")
tokenized=tokenizer.tokenize("The water are hot. My friends are going to be late. Today mine mother is in Barcelona.")

import ctranslate2
translator = ctranslate2.Translator("ctranslate2/")
translated = translator.translate_batch([tokenized[0]])
print(tokenizer.detokenize(translated[0][0]['tokens']))
The water is hot. My friends are going to be late. Today my mother is in Barcelona.
```
# Model

The model has been training using the [clang8](https://github.com/google-research-datasets/clang8) corpus for English language.

* English GEC model (https://www.softcatala.org/pub/softcatala/opennmt/models/gec-english/gec-english-2021-11-11.zip)
  * Total number of sentences: 2159674
  * Model: TransformerBase
  * Tokenizer: SentencePiece
  * BLEU = 85.50

# Papers

Relevant papers:

* [Approaching Neural Grammatical Error Correction as a Low-Resource Machine Translation Task](https://aclanthology.org/N18-1055.pdf)
* [A Simple Recipe for Multilingual Grammatical Error Correction](https://arxiv.org/pdf/2106.03830.pdf)


# Contact

Email address: Jordi Mas: jmas@softcatala.org
