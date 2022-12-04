# Ruth-nlu Classfiers 

Ruth Classifiers are a set of tools for classifying text. They are designed to be used in a pipeline, with the output of one classifier being the input to the next.

## Intent Classifier

The intent classifier is the first classifier in the pipeline. It is used to determine the intent of the user's input. The intent classifier is trained on a set of examples, each of which has an intent and a set of entities. 

The intent classifier is trained using the `ruth train` command. The training data is stored in a file called `training_data.json`. The format of the file is as follows:

```yml
version: "0.1"
nlu:
- intent: ham
  examples: |
    - WHO ARE YOU SEEING?
    - Great! I hope you like your man well endowed. I am  &lt;#&gt;  inches
    - Didn't you get hep b immunisation in nigeria.
    - Fair enough, anything going on?
    - Yeah hopefully, if tyler can't do it I could maybe ask around a bit
- intent: spam
  examples: |
    - Did you hear about the new Divorce Barbie? It comes with all of Ken's stuff!
    - I plane to give on this month end.
    - Wah lucky man Then can save money Hee
    - Finished class where are you.
    - K..k:)where are you?how did you performed?
```

The `intent` field is the name of the intent. The `examples` field is a list of examples of the intent. Each example is on a new line.

The `ruth train` command will train the intent classifier and store the trained model in a file called `intent_classifier.pkl`.

RUTH is a pipeline based NLU engine, it has 3 basic main components - Tokenizer - Featurizer - Intent Classifier
In `pipeline-data.yml` file is used to define the pipeline components and their order. The default pipeline is as follows:


```yml
task:
pipeline:
  - name: 'WhiteSpaceTokenizer'
  - name: 'CountVectorFeaturizer'
  - name: 'SVMClassifier'
```

to train the intent classifier, run the following command:

```bash
ruth train -d path/to/training_data.json -p path/to/pipeline.yml
```

### List of available classifiers:
- NaiveBayesClassifier
- SVMClassifier
- HFClassifier `Hugging Face Classifier`

## NaiveBayesClassifier

The NaiveBayesClassifier is a simple classifier that uses the Naive Bayes algorithm to classify text. Naive Bayes is a classification technique that is based on Bayes’ Theorem with an assumption that all the features that predicts the target value are independent of each other. It calculates the probability of each class and then pick the one with the highest probability. It has been successfully used for many purposes, but it works particularly well with natural language processing (NLP) problems. To read more about the Naive Bayes algorithm, see [here](https://en.wikipedia.org/wiki/Naive_Bayes_classifier).

To train your data using NaiveBayesClassifier the `pipeline-data.yml` file should be as follows:


```yml
task:
pipeline:
  - name: 'WhiteSpaceTokenizer'
  - name: 'CountVectorFeaturizer'
  - name: 'NaiveBayesClassifier'
```


## SVMClassifier

The SVMClassifier is a simple classifier that uses the Support Vector Machine algorithm to classify text. Support Vector Machine (SVM) is a discriminative classifier formally defined by a separating hyperplane. To read more about the Support Vector Machine algorithm, see [here](https://en.wikipedia.org/wiki/Support_vector_machine).

To train your data using SVMClassifier the `pipeline-data.yml` file should be as follows:

```yml
task:
pipeline:
  - name: 'WhiteSpaceTokenizer'
  - name: 'CountVectorFeaturizer'
  - name: 'SVMClassifier'
```

## HFClassifier

HF Classifier is a simple and easy to use library for text classification.
HF Classifier is a wrapper around the Hugging Face transformers library. Hugging Face is an open-source library for building, training, and deploying state-of-the-art machine learning models, especially about NLP. To read more about the DistilBert model, see [here](https://huggingface.co/docs/transformers/model_doc/bert).


To train your data using HFClassifier the `pipeline-data.yml` file should be as follows:

```yml
task:
pipeline:
  - name: 'HFTokenizer'
    model_name: 'bert-base-uncased'
  - name: 'HFClassifier'
    model_name: 'bert-base-uncased'
```

Popular Transformer model names follows 

```bash
        BERT-Base, uncased: 12-layer, 768-hidden, 12-heads, 110M parameters
        BERT-Large, uncased: 24-layer, 1024-hidden, 16-heads, 340M parameters
        BERT-Base, cased: 12-layer, 768-hidden, 12-heads , 110M parameters
        BERT-Large, cased: 24-layer, 1024-hidden, 16-heads, 340M parameters
        BERT-Base, multilingual cased 104 languages, 12-layer, 768-hidden, 12-heads, 110M parameters
        BERT-Base, Chinese: Chinese Simplified and Traditional, 12-layer, 768-hidden, 12-heads, 110M parameters
        BERT-Distilled, cased: 6-layer, 384-hidden, 4-heads, 33M parameters
        BERT-Distilled, uncased: 6-layer, 384-hidden, 4-heads, 33M parameters
        RoBERTa, cased: 12-layer, 768-hidden, 12-heads, 125M parameters
        RoBERTa, uncased: 12-layer, 768-hidden, 12-heads, 125M parameters
        RoBERTa, large, cased: 24-layer, 1024-hidden, 16-heads, 355M parameters
        RoBERTa, large, uncased: 24-layer, 1024-hidden, 16-heads, 355M parameters
        RoBERTa, base, cased: 12-layer, 768-hidden, 12-heads, 125M parameters
        RoBERTa, base, uncased: 12-layer, 768-hidden, 12-heads, 125M parameters
        RoBERTa, small, cased: 6-layer, 384-hidden, 6-heads, 17M parameters
        RoBERTa, small, uncased: 6-layer, 384-hidden, 6-heads, 17M parameters
```


