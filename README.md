#  CRF-Cut: Sentence Segmentation

The objective of CRF-Cut (Conditional Random Fields - Cut) is to cut sentences and we will able to utilize these sentences.

The process of training is to get sentences and we will tokenize words and assign label for each word `I`: Inside of sentence and `E`: End of sentence.

The result of CRF-Cut is trained by different datasets are as follows:

| dataset_train              | dataset_validate | E_f1-score | space_correct_accuracy |
|----------------------------|------------------|------------|------------------------|
| Ted                        | Ted              | 0.72       | 0.82                   |
| Ted                        | Orchid           | 0.36       | 0.73                   |
| Ted                        | Fake review      | 0.77       | 0.78                   |
| Orchid                     | Ted              | 0.58       | 0.71                   |
| Orchid                     | Orchid           | 0.77       | 0.87                   |
| Orchid                     | Fake review      | 0.69       | 0.70                   |
| Fake review                | Ted              | 0.56       | 0.56                   |
| Fake review                | Orchid           | 0.53       | 0.67                   |
| Fake review                | Fake review      | 0.97       | 0.97                   |
| Ted + Orchid + Fake review | Ted              | 0.72       | 0.78                   |
| Ted + Orchid + Fake review | Orchid           | 0.69       | 0.83                   |
| Ted + Orchid + Fake review | Fake review      | 0.97       | 0.96                   |

Google colab: 
- Train 1 dataset: https://colab.research.google.com/drive/12nszk-N5LwpHzitlYvhNWVUDSBj30Z1Y
- Train 3 datasets: https://colab.research.google.com/drive/1qPEuLZdNNsxhURn8HK7DLi7gbA84coWZ

# Sentence Breaking Journal

## What doesn't work

* POS-perceptron
* Larger features than window = 2, max_n_gram = 3
* Number of verbs to the left and right
* Rule-based override
* L2 regularization - also not practical
* POS-artagger - not really too slow
* ORCHID - different domains get totally different results

## What to try

* TNC

## What worked

* Fake "convolutions" of window = 2, max_n_gram = 3
* L1 regularization of 1
* Predict end of sentence (space) instead of beginning of sentence
* Custom POS - only faster convergence
* Try with ORCHID to compare performance more fairly - 87% vs 95% SOTA

# Requirements

- pythainlp
- python-crfsuite
- pandas
- numpy
- scikit-learn
- tqdm