# Recuurent Neural Networks: Transliteration with and without Attention Mechanism
This project aims to work with different kinds of RNNs that acieve the task of transliterating English (Latin) script into our native script. I've chosen this to be Hindi.

## Structure of the Repository
1) The repository contains 4 notebooks that involve training and testing of models.
2) Notebooks `Train_without_att.ipynb` and `Train_with_att.ipynb` deal with running the hyperparameter sweeps to select the best hyperparameter set.
3) Notebooks `Test_without_att.ipynb` and `Test_with_att.ipynb` deal with testing the model on the test dataset using the best hyperparameter set.
4) The 5th notebook `visualize.ipynb` is used to build the input-output character connectivity visualization that was given in Question 6. The corresponding html file obtained is also given in the repository.
5) The predictions obtained from both the approaches (with and without attention) have been given in the predictions_vanilla and predictions_attention folder as `prediction_basic.csv` and `predictions_attention.csv` respectively.
6) The best models from both the approaches 'Model_Basic.pth` and `Attention_model.pth` have also been provided.

## Running the notebooks
1) All the notebooks have been designed to run cell by cell.
2) Google Colab was used for this purpose with the cloud T4 GPU access for training and inference.
3) The data was first uploaded on Google drive and was accessed in the following way to change its path to content folder in Colab for ease of access.
```
# Copy dataset from Drive to local content directory
!cp -r /content/drive/MyDrive/dakshina_dataset_v1.0 /content/
,,,
4) For the Hindi language, the data actually had the Hindi words in the first column and English words in the second.
5) I interchanged the columns for all three datasets (train, val, test) so that the Input and Target languages are selected properly.
