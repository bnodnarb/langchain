# Hugging Face

This page covers how to use the Hugging Face ecosystem (including the [Hugging Face Hub](https://huggingface.co)) within LangChain.
It is broken into two parts: installation and setup, and then references to specific Hugging Face wrappers.

## Installation and Setup

If you want to work with the Hugging Face Hub:
- Install the Hub client library with `pip install huggingface_hub`
- Create a Hugging Face account (it's free!)
- Create an [access token](https://huggingface.co/docs/hub/security-tokens) and set it as an environment variable (`HUGGINGFACEHUB_API_TOKEN`)

If you want work with the Hugging Face Python libraries:
- Install `pip install transformers` for working with models and tokenizers
- Install `pip install datasets` for working with datasets

## Wrappers

### LLM

There exists two Hugging Face LLM wrappers, one for a local pipeline and one for a model hosted on Hugging Face Hub.
Note that these wrappers only work for models that support the following tasks: [`text2text-generation`](https://huggingface.co/models?library=transformers&pipeline_tag=text2text-generation&sort=downloads), [`text-generation`](https://huggingface.co/models?library=transformers&pipeline_tag=text-classification&sort=downloads)

To use the local pipeline wrapper:
```python
from langchain.llms import HuggingFacePipeline
```

To use a the wrapper for a model hosted on Hugging Face Hub:
```python
from langchain.llms import HuggingFaceHub
```
For a more detailed walkthrough of the Hugging Face Hub wrapper, see [this notebook](../modules/models/llms/integrations/huggingface_hub.ipynb)


### Embeddings

There exists two Hugging Face Embeddings wrappers, one for a local model and one for a model hosted on Hugging Face Hub.
Note that these wrappers only work for [`sentence-transformers` models](https://huggingface.co/models?library=sentence-transformers&sort=downloads).

To use the local pipeline wrapper:
```python
from langchain.embeddings import HuggingFaceEmbeddings
```

To use a the wrapper for a model hosted on Hugging Face Hub:
```python
from langchain.embeddings import HuggingFaceHubEmbeddings
```
For a more detailed walkthrough of this, see [this notebook](../modules/models/text_embedding/examples/embeddings.ipynb)

### Tokenizer

There are several places you can use tokenizers available through the `transformers` package.
By default, it is used to count tokens for all LLMs.

You can also use it to count tokens when splitting documents with 
```python
from langchain.text_splitter import CharacterTextSplitter
CharacterTextSplitter.from_huggingface_tokenizer(...)
```
For a more detailed walkthrough of this, see [this notebook](../modules/indexes/text_splitters/examples/textsplitter.ipynb)


### Datasets

The Hugging Face Hub has lots of great [datasets](https://huggingface.co/datasets) that can be used to evaluate your LLM chains.

For a detailed walkthrough of how to use them to do so, see [this notebook](../use_cases/evaluation/huggingface_datasets.ipynb)
