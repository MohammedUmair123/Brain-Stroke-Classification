#Major Project 2024-2025
# INNOVATIONS IN STROKE IDENTIFICATION: AN AI-POWERED BASED DIAGNOSTIC MODEL USING NEUROIMAGES

The repository contains all the source code, development notebooks, and supplementary materials used to implement the system and generate the results discussed in this thesis.  

What this project does

1. Classifies brain CT images as Normal or Stroke.
2. Uses VGG19 to extract image features.
3. Reduces feature size with PCA.
4. Trains a GRU model for final classification.
5. Provides a Gradio app for easy testing with a single image.
6. Adds optional audio feedback using gTTS.

Dataset 

Source: Kaggle, “Brain Stroke CT Image Dataset”.
Two folders: Normal and Stroke.

Example paths used in Colab:

/content/drive/MyDrive/Brain_Data_Organised/Normal

/content/drive/MyDrive/Brain_Data_Organised/Stroke 

How it works (short version)

1. Load CT images and resize to 224x224.
2. Normalize pixel values to 0–1.
3. Extract deep features using VGG19 without the top layer.
4. Flatten features and apply PCA to keep about 95% variance.
5. Feed PCA features to a GRU model.
6. Train with 10-fold stratified cross validation.
7. Save the trained GRU model and the fitted PCA model.
8. Use the Gradio UI to upload an image and get a prediction.

Results from the example run

1. Accuracy about 95.7% across folds.
2. AUC about 0.99.
3. Normal: precision 0.94, recall 1.00, F1 0.97.
4. Stroke: precision 1.00, recall 0.89, F1 0.94.

What is included

1. Colab-friendly training code.

2. Inference script with Gradio UI.

3. Saved models:
    . save_models/pca_model.pkl
    . save_models/my_gru_model.keras

4. Plots for metrics and ROC curve.
5. Example background image for the UI.
