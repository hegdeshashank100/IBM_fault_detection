AutoAI Incremental Learning Notebook for Fault Detection
Overview
This notebook demonstrates how to continue training an AutoAI-generated pipeline for a multiclass classification task focused on fault detection (e.g., identifying "Line Breakage," "Overheating," or "Transformer Failure"). It leverages incremental learning techniques to process additional training data in batches, using the partial_fit method for efficient model updates. The notebook also includes steps to evaluate, store, and deploy the model using IBM Watson Studio and watsonx.ai.
Key Objectives

Data Loading: Retrieve training data in batches using a DataLoader compatible with PyTorch.
Incremental Training: Use partial_fit to incrementally train a Random Forest Classifier pipeline.
Model Evaluation: Assess the pipeline’s performance using accuracy metrics and visualize learning curves.
Model Storage and Deployment: Save the trained model and create an online deployment for real-time predictions.

Prerequisites
To run this notebook successfully, ensure you have:

Python Version: Python 3.11
Required Packages:
ibm-watsonx-ai
autoai-libs (~2.0)
scikit-learn (1.3.*)
lale (~0.8.3)
snapml (1.14.*)


IBM Cloud Credentials: An API key for accessing watsonx.ai services (see IBM Cloud documentation).
Hardware: The notebook adjusts to available CPU cores for optimal performance.

Installation
Install the required packages by running the following commands in your environment:
pip install ibm-watsonx-ai
pip install autoai-libs~=2.0
pip install scikit-learn==1.3.*
pip install lale~=0.8.3
pip install snapml==1.14.*

Notebook Structure
The notebook is organized into the following key sections:

Setup:

Installs necessary packages.
Defines AutoAI experiment metadata, including data connections and model parameters.
Configures watsonx.ai credentials for API access.


Incremental Learning:

Get Pipeline: Downloads the pre-trained AutoAI pipeline (Pipeline_9) in LALE format for inspection and incremental training.
Data Loader: Uses ExperimentIterableDataset and ExperimentDataLoader to load training data in batches (default batch size: 506 rows).
Continue Model Training: Incrementally trains the pipeline using partial_fit on batched data, with optional sample weighting for imbalanced datasets.
Test Pipeline Model: Evaluates the model on a holdout set (30% of the first batch if no test set is provided) and visualizes learning curves.


Store the Model:

Saves the incrementally trained model to the IBM Watson Studio repository.


Create Online Deployment:

Provides instructions to promote the model to a deployment space and create an online deployment for scoring.
Includes optional code to test the deployment with sample data.


Summary and Next Steps:

Summarizes the notebook’s achievements and provides links to additional AutoAI resources.



Usage Instructions

Prepare Your Environment:

Ensure all prerequisites are met, including package installations and IBM Cloud API key.
Update the space_id in the deployment section if you plan to deploy the model.


Run the Notebook:

Execute the cells sequentially in a Jupyter environment (e.g., IBM Watson Studio or a local setup with Jupyter Notebook).
Provide your IBM Cloud API key when prompted.
If you have a custom test dataset, replace X_test and y_test in the evaluation section.


Customize as Needed:

Adjust the batch size (number_of_batch_rows) based on your dataset size and memory constraints.
If your data is imbalanced, enable the sample_weight parameter in the partial_fit call as shown in the notebook.


Deploy the Model:

Change the deployment cells from raw to code type and provide a valid space_id.
Run the deployment and scoring cells to test the model’s predictions via the online endpoint.



Important Notes

Data Compatibility: The pipeline is optimized for the original dataset specified in the AutoAI experiment. Using a different dataset may require retraining the pipeline.
Data Preprocessing: The pipeline converts DataFrames to NumPy arrays before training. Ensure your data is preprocessed (e.g., handle missing values with dropna() or remove duplicates with drop_duplicates()).
Warnings: The notebook suppresses warnings during incremental training to improve readability. Review any warnings if you encounter issues.
Deployment: If you don’t have a deployment space, create one using the Deployment Spaces Dashboard.

Additional Resources

IBM Watson Studio AutoAI Documentation
Watson Machine Learning Samples
IBM Cloud API Key Documentation

License
This notebook and its source code are released under the terms of the ILAN License. By using this notebook, you agree to the License Terms.
