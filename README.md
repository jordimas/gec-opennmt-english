# Introduction

This repository constains a description on how to use OpenNMT on the Grammar Error Correction (GEC) task

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

