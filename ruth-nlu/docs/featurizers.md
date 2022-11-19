# Ruth-Featurizers

Ruth Featurizers are a set of tools for featurizing text. They are designed to be used in a pipeline, with the output of one featurizer being the input to the next.

# Sparse Featurizers

 Sparse Featurizers are used to convert text into a sparse matrix of features ( scipy sparse matrix format ). Every featurizer has a different way of converting text into features. The features are then used by the intent classifier to determine the intent of the text.

## CountVectorFeaturizer

The CountVectorFeaturizer is a simple featurizer that converts text into a vector of word counts. It is the default featurizer used by RUTH.

To use the CountVectorFeaturizer, add the following to your `pipeline-data.yml` file:

```yml
task:
pipeline:
  - name: 'CountVectorFeaturizer'
```
## TfidfVectorFeaturizer

The TfidfVectorFeaturizer is a simple featurizer that converts text into a vector of word counts frequency. It is the default featurizer used by RUTH.

To use the TfidfVectorFeaturizer, add the following to your `pipeline-data.yml` file:

```yml
task:
pipeline:
  - name: 'TfidfVectorFeaturizer'
```

# Dense Featurizers

Dense Featurizers are used to convert text into a dense matrix of features ( numpy array format ). Every dense featurizer inherits from the `DenseFeaturizer` class. The features are then used by the intent classifier to determine the intent of the text.

```bash
tbd
```

