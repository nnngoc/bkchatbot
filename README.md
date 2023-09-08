# POLICY INSERT FUNCTIONS IN BKHERT CHATBOT

### Goal: 
Improve the existing model by applying MLOPS to automate the deployment, monitoring, and management of ML models in production.
This pipeline will be used for the Intent and Entity model in the system.

### Pipeline:
1. Manual labeling
    - Label the data collected from the conversation of the chatbot system.
2. Store data
    - Store the labeled data in the Dagshub Storage
3. Train model
    - Every time, data is updated to Dagshub storage, Github Action will trigger the training notebook on Kaggle via Kaggle API
    - Train the model with the new updated data on Kaggle notebook.
4. Azure model storage
    - After training is done, the model will be stored in Azure model storage.
    - Use MLflow for tracking model and Azure endpoint for inference.
### Example
    - Update data from local to Dagshub storage to trigger the pipeline:
    dagshub upload --update --message "Update intent data" nnngoc/bkchatbot intent-data intent-data
