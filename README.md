# Major Project 2024-2025
# INNOVATIONS IN STROKE IDENTIFICATION: AN AI-POWERED BASED DIAGNOSTIC MODEL USING NEUROIMAGES

The repository contains all the source code, development notebooks, and supplementary materials used to implement the system and generate the results discussed in the thesis.  

# What this project does

1. Classifies brain CT images as Normal or Stroke.
2. Uses VGG19 to extract image features.
3. Reduces feature size with PCA.
4. Trains a GRU model for final classification.
5. Provides a Gradio app for easy testing with a single image.
6. Adds optional audio feedback using gTTS.

# Dataset 

Source: Kaggle, “Brain Stroke CT Image Dataset”.
Two folders: Normal and Stroke.

Example paths used in Colab:

/content/drive/MyDrive/Brain_Data_Organised/Normal

/content/drive/MyDrive/Brain_Data_Organised/Stroke 

# How it works (short version)

1. Load CT images and resize to 224x224.
2. Normalize pixel values to 0–1.
3. Extract deep features using VGG19 without the top layer.
4. Flatten features and apply PCA to keep about 95% variance.
5. Feed PCA features to a GRU model.
6. Train with 10-fold stratified cross validation.
7. Save the trained GRU model and the fitted PCA model.
8. Use the Gradio UI to upload an image and get a prediction.

# Results from the example run

1. Accuracy about 95.7% across folds.
2. AUC about 0.99.
3. Normal: precision 0.94, recall 1.00, F1 0.97.
4. Stroke: precision 1.00, recall 0.89, F1 0.94.

# What is included

1. Colab-friendly training code.
2. Inference script with Gradio UI.
3. Saved models:
   
    - save_models/pca_model.pkl
    - save_models/my_gru_model.keras
5. Plots for metrics and ROC curve.
6. Example background image for the UI.

# Basic usage (Colab)

1. Mount Google Drive and set dataset paths.
2. Run the training cells to:
3. Extract features
4. Fit PCA
5. Train with cross validation
6. save models
7. Run the inference cells to:
8. Load pca_model.pkl and my_gru_model.keras
9. Launch the Gradio app
10.Upload a CT image and view the result

# Key dependencies

1. scikit-learn
2. OpenCV
3. NumPy
4. Matplotlib
5. Gradio
6. gTTS
7. Pillow and pandas
8. TensorFlow 2.x

# Important notes for reproducibility

1. Use the same preprocessing at inference as training.
2. Load the same PCA model that was fitted during training.
3. Keep random seeds consistent for numpy and TensorFlow if you need repeatable numbers.
4. Version-lock packages when possible.

# Data augmentation used

1. Rotations, width and height shifts, shear, zoom, and horizontal flips.
2. Augmented images are combined with the original set for training.

# Limitations and safety

1. This project is for research and education.
2. It is not a medical device.
3. Performance can vary on new scanners or hospitals.
4. Validate on your own data before any real use.

# Troubleshooting

1. Out of memory during feature extraction: lower batch size.
2. PCA shape mismatch: make sure you load the same pca_model.pkl.
3. Gradio in Colab: if the app does not show, set share=True when launching.
4. Color channels: ensure images are read as 3 channels and resized to 224x224.

# Credits

1. Kaggle dataset: Brain Stroke CT Image Dataset by Afridi Rahman.
2. VGG19 from TensorFlow Keras.
3. PCA and metrics from scikit-learn.
4. UI by Gradio.
5. Audio by gTTS.
