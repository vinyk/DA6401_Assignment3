# Recuurent Neural Networks: Transliteration with and without Attention Mechanism
This project aims to work with different kinds of RNNs that acieve the task of transliterating English (Latin) script into our native script. I've chosen this to be Hindi.

## Table of Contents

## Table of Contents

- [Structure of the Repository](#structure-of-the-repository)
- [Running the Notebooks](#running-the-notebooks)
- [Without Attention](#without-attention)
  - [Accuracies](#accuracies)
- [With Attention](#with-attention)
  - [Accuracies](#accuracies-1)
- [Visualization](#visualization)


## Structure of the Repository
1) The repository contains 4 notebooks that involve training and testing of models.
2) Notebooks `Train_without_att.ipynb` and `Train_with_att.ipynb` deal with running the hyperparameter sweeps to select the best hyperparameter set.
3) Notebooks `Test_without_att.ipynb` and `Test_with_att.ipynb` deal with testing the model on the test dataset using the best hyperparameter set.
4) The 5th notebook `visualize.ipynb` is used to build the input-output character connectivity visualization that was given in Question 6. The corresponding html file obtained is also given in the repository.
5) The predictions obtained from both the approaches (with and without attention) have been given in the `predictions_vanilla` and `predictions_attention` folder as `prediction_basic.csv` and `predictions_attention.csv` respectively.
6) The best models from both the approaches 'Model_Basic.pth` and `Attention_model.pth` have also been provided in the `Models` folder.
7) The visualization file `attention_viz.html` is provided in the `Visualization` folder. Download it to view the connectivity visualization. Also given is a gif which shows the working.

## Running the notebooks
1) All the notebooks have been designed to run cell by cell.
2) Google Colab was used for this purpose with the cloud T4 GPU access for training and inference.
3) The data was first uploaded on Google drive and was accessed in the following way to change its path to content folder in Colab for ease of access.
```
# Copy dataset from Drive to local content directory
!cp -r /content/drive/MyDrive/dakshina_dataset_v1.0 /content/
```
4) For the Hindi language, the data actually had the Hindi words in the first column and English words in the second.
5) I interchanged the columns for all three datasets (train, val, test) so that the Input and Target languages are selected properly, this dataset is also given in the repository.

## Without Attention
### Accuracies
For the best parameter set:
```
best_config = {
    'embedding_size': 64,
    'hidden_size': 256,
    'num_encoder_layers': 3,
    'num_decoder_layers': 3,
    'cell_type': 'GRU',
    'dropout': 0.2,
    'src_vocab_size': len(src_vocab),
    'tgt_vocab_size': len(tgt_vocab),
}
```

Training Accuracy - 90.5%

Validation Accuracy - 89%

For different beam sizes,

Beam size 1 → Test Accuracy: 35.41%

Beam size 3 → Test Accuracy: 36.52%

Beam size 5 → Test Accuracy: 36.52%

## With Attention
### Accuracies
For the best parameter set:
```
best_config = {
    'embedding_size': 256,
    'hidden_size': 256,
    'num_encoder_layers': 1,
    'num_decoder_layers': 1,
    'cell_type': 'LSTM',
    'dropout': 0.3,
    'src_vocab_size': len(src_vocab),
    'tgt_vocab_size': len(tgt_vocab),
}
```
For simplicity, only one encoder-decoder layer was used.


Training Accuracy - 91.25%

Validation Accuracy - 89.5%

For different beam sizes,

Beam size 1 → Test Accuracy: 21.12%

Beam size 3 → Test Accuracy: 22.72%

Beam size 5 → Test Accuracy: 22.86%

## Visualization

The connectivity visualization as given in the question works as follows:

1) Once the mouse cursor hovers over a character, the corresponding input characters contributing to the prediction of that output character are highlighted.

2) The shade of the highlighted colour (yellow here) depends on the degree of attention given to that input character for the prediction. Darker the shade, higher the attention.

3) This character to character attention weight is given in the `attention.json` file.
