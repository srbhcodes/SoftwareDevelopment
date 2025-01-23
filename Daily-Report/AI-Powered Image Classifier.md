# AI-Powered Image Classifier (Using Pretrained Model)

**Name:** Sourabh Narnaulia
**Date:** 30 Dec 2025
Project Name: AI-Powered Image Classifier (Using Pretrained Model)
Epic Name: Gen AL/MLOPs
Git link: https://github.com/srbhcodes/ImageClassifier

---

## Scope of Project

The scope of this project is to develop an AI-powered image classifier using a pretrained deep learning model. This application aims to classify images accurately into predefined categories. The project also explores the integration of machine learning pipelines and the deployment of the solution for broader usability.

---

## Technologies Used

- **Programming Language:** Python
- **Deep Learning Frameworks:** TensorFlow, Keras
- **Libraries:** NumPy, Pandas, Matplotlib, OpenCV
- **Pretrained Model:** TensorFlow/Keras pretrained models (e.g., ResNet, MobileNet)
- **Development Environment:** Jupyter Notebook, VS Code
- **Version Control:** Git

---

## Steps

1. **Project Setup:**
    
    - Initialized a Python virtual environment.
    - Installed necessary dependencies (TensorFlow, Keras, etc.).
2. **Data Collection and Preparation:**
    
    - Gathered a dataset of images for classification.
    - Preprocessed images (resizing, normalization, augmentation).
3. **Model Selection:**
    
    - Selected a pretrained model (e.g., MobileNet).
    - Loaded the model using TensorFlow/Keras.
4. **Training and Fine-Tuning:**
    
    - Configured the model for transfer learning.
    - Fine-tuned the model on the specific dataset.
5. **Testing and Validation:**
    
    - Evaluated the model’s performance using metrics like accuracy and loss.
    - Adjusted hyperparameters to optimize results.
6. **Deployment:**
    
    - Packaged the model for local testing.
    - Explored options for deployment (e.g., Flask, FastAPI, or cloud services).

---

## Project Outcome

The AI-powered image classifier successfully:

- Recognized and classified images into predefined categories with a high accuracy rate.
- Leveraged transfer learning for efficient training on a relatively small dataset.
- Established a foundation for future enhancements like real-time predictions and integration with other applications.

---

## Issues Faced

1. **Large Repository Size:**
    
    - Encountered issues with Git due to large files in the repository.
    - Used `git filter-repo` to remove unnecessary large files from history.
2. **Dependency Conflicts:**
    
    - Resolved version mismatches for TensorFlow and other libraries.
3. **Training Errors:**
    
    - Handled errors related to input shape mismatches.
    - Addressed out-of-memory errors by reducing batch size and optimizing image preprocessing.
4. **Model Fine-Tuning Challenges:**
    
    - Experimented with learning rates and optimizer configurations to stabilize training.
5. **Remote Repository Issues:**
    
    - Fixed errors like "src refspec main does not match any" by ensuring the correct branch and remote setup.
6. **Debugging Large Files:**
    
    - Identified and removed large files using `git verify-pack` and `git filter-repo` command

### Screenshots
Image of server running:
![[Pasted image 20250107203946.png]]

Image of Prediction:
![[Pasted image 20250107204137.png]]