⚙️ AutoAI Incremental Learning Notebook for Fault Detection
This notebook demonstrates how to continue training an AutoAI-generated pipeline for a multiclass classification task focused on fault detection (e.g., identifying faults like Line Breakage, Overheating, or Transformer Failure).

It leverages incremental learning techniques to process additional training data in batches using the partial_fit method — enabling efficient updates, evaluation, storage, and deployment via IBM Watson Studio and watsonx.ai.

📌 Key Objectives
✅ Data Loading: Load training data in batches using ExperimentDataLoader (PyTorch-compatible).

🔁 Incremental Training: Use partial_fit() with a RandomForestClassifier pipeline.

📊 Model Evaluation: Assess model performance and visualize learning curves.

☁️ Model Storage & Deployment: Save and deploy the trained model for real-time prediction.

🧰 Prerequisites
✅ Environment
Python: 3.11

📦 Required Packages
bash
Copy
Edit
pip install ibm-watsonx-ai
pip install autoai-libs~=2.0
pip install scikit-learn==1.3.*
pip install lale~=0.8.3
pip install snapml==1.14.*
🔐 IBM Cloud
API Key for watsonx.ai access (see IBM Cloud API Key Documentation)

Deployment Space ID for model deployment (optional)

🖥️ Hardware
The notebook dynamically adjusts to available CPU cores for optimal performance.

📁 Notebook Structure
1. 🚀 Setup
Install packages

Define experiment metadata

Configure IBM watsonx.ai credentials

2. 🧠 Incremental Learning
Get Pipeline: Download AutoAI pipeline in LALE format (e.g., Pipeline_9)

Data Loader: Load batched data (default: 506 rows)

Continue Training: Use partial_fit on batches, with optional sample_weight

Evaluate Model: Use holdout/test set and visualize learning progress

3. 💾 Store the Model
Save the final trained model to IBM Watson Studio

4. 🌐 Create Online Deployment
Promote model to deployment space

Create endpoint for real-time scoring

Test model via API with sample input

5. 📘 Summary and Next Steps
Wrap-up with resources and further reading

▶️ Usage Instructions
1. Prepare Environment
Install all packages

Get your IBM Cloud API key

Set the space_id if deploying

2. Run Notebook
Use IBM Watson Studio or local Jupyter Notebook

Execute all cells sequentially

Provide credentials when prompted

3. Customize
Change batch size (number_of_batch_rows) if needed

Enable sample_weight for imbalanced datasets

Replace X_test and y_test for custom evaluation

4. Deploy
Change deployment cells from raw to code

Insert your space_id

Run deployment and scoring cells

⚠️ Important Notes
⚙️ Data Compatibility: Use the same schema as the original AutoAI dataset.

🧹 Preprocessing: Ensure clean data (dropna(), drop_duplicates()).

⚠️ Warnings: Suppressed during training — review logs if issues occur.

☁️ Deployment: Create a deployment space via Deployment Spaces Dashboard.

📚 Additional Resources
📖 AutoAI Documentation

🧪 Watson Machine Learning Samples

🔐 IBM Cloud API Key Docs

📜 License
This notebook is released under the ILAN License. By using this notebook, you agree to the License Terms.

