# veld_chain__train_infer_wordembeddings_multiple_architectures__wikipedia

This repo contains several chain velds relating to training and evaluation of static word embedding
architectures on wikipedia data. 

It mainly acts as a public demonstration mirroring this project setup on internal AMC data: 
https://github.com/veldhub/veld_chain__train_infer_wordembeddings_multiple_architectures__amc

## requirements and setup

- git
- docker compose

Clone the repo with all its submodules
```
git clone --recurse-submodules https://github.com/veldhub/veld_chain__train_infer_wordembeddings_multiple_architectures__wikipedia.git
```

## intergrated code and data velds

This is the list of code and data velds, integrated into chain velds within this repository:

- https://github.com/veldhub/veld_code__fasttext.git : fastText code
- https://github.com/veldhub/veld_code__glove.git : GloVe code
- https://github.com/veldhub/veld_code__wikipedia_nlp_preprocessing : wikipedia preprocessing
- https://github.com/veldhub/veld_code__word2vec.git : word2vec code
- https://github.com/veldhub/veld_code__wordembeddings_evaluation.git : Evaluation code of all 
  wordembeddings.
- https://github.com/veldhub/veld_code__wordembeddings_preprocessing.git : Preproccesing code
- https://github.com/veldhub/veld_data__wordembeddings_evaluation.git : Aggregation of evaluation
  and analysis on performance of trained models.

## how to reproduce

The entire setup can be either run through sequentially by following all 
[individual steps](#individual-steps) or by executing a [multichain](#multichain) containing all 
individual chains. 

### individual steps

[./veld_step_01_preprocess_download_and_extract.yaml](./veld_step_01_preprocess_download_and_extract.yaml) 
: downloads and extracts an entire wikipedia dump.
```
docker compose -f veld_step_01_preprocess_download_and_extract.yaml up
```

[./veld_step_02_preprocess_transform_wiki_json_to_txt.yaml](./veld_step_02_preprocess_transform_wiki_json_to_txt.yaml) 
: transforms the wikipedia json files into one single txt
```
docker compose -f veld_step_02_preprocess_transform_wiki_json_to_txt.yaml up
```

[./veld_step_03_preprocess_lowercase.yaml](./veld_step_03_preprocess_lowercase.yaml) : make entire 
text lowercase.
```
docker compose -f veld_step_03_preprocess_lowercase.yaml up
```

[./veld_step_04_preprocess_remove_punctuation.yaml](./veld_step_04_preprocess_remove_punctuation.yaml) 
: removes all punctuation from the training data.
```
docker compose -f veld_step_04_preprocess_remove_punctuation.yaml up
```

[./veld_step_05_train_fasttext.yaml](./veld_step_05_train_fasttext.yaml) : trains a fastText 
wordembeddings model.
```
docker compose -f veld_step_05_train_fasttext.yaml up
```

[./veld_step_06_train_word2vec.yaml](./veld_step_06_train_word2vec.yaml) : trains a word2vec
wordembeddings model.
```
docker compose -f veld_step_06_train_word2vec.yaml up
```

[./veld_step_07_train_glove.yaml](./veld_step_07_train_glove.yaml) : trains a GloVe wordembeddings 
model.
```
docker compose -f veld_step_07_train_glove.yaml up
```

[./veld_step_08_eval_fasttext.yaml](./veld_step_08_eval_fasttext.yaml) : evaluates fastText models
```
docker compose -f veld_step_08_eval_fasttext.yaml up
```

[./veld_step_09_eval_word2vec.yaml](./veld_step_09_eval_word2vec.yaml) : evaluates word2vec models
```
docker compose -f veld_step_09_eval_word2vec.yaml up
```

[./veld_step_10_eval_glove.yaml](./veld_step_10_eval_glove.yaml) : evaluates GloVe models
```
docker compose -f veld_step_10_eval_glove.yaml up
```

[./veld_step_11_analyse_evaluation.yaml](./veld_step_11_analyse_evaluation.yaml) : sums up all
evaluations into a comprehensive summary and multi-dimensional visualization.
```
docker compose -f veld_step_11_analyse_evaluation.yaml up
```

### multichain

[./veld_step_all_multi_chain.yaml](./veld_step_all_multi_chain.yaml) : Aggregates all previous 
chains and makes them executable in one single command:
```
docker compose -f veld_step_all_multi_chain.yaml up
```

