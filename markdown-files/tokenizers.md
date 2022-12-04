# Ruth-Tokenizers

Ruth Tokenizers are a set of tools for tokenizing text. They are designed to be used in a pipeline, with the output of one tokenizer being the input to the next.

## WhiteSpaceTokenizer

The WhiteSpaceTokenizer is a simple tokenizer that splits text on whitespace. It is the default tokenizer used by RUTH. 

To use the WhiteSpaceTokenizer, add the following to your `pipeline-data.yml` file:

```yml
task:
pipeline:
  - name: 'WhiteSpaceTokenizer'
```

## HFTokenizer

HF Tokenizer is a simple and easy to use library for tokenizing text. It is based on the Hugging Face Tokenizers library.

To use the HFTokenizer, add the following to your `pipeline-data.yml` file:

```yml
task:
pipeline:
  - name: 'HFTokenizer'
```
