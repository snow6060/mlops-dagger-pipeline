
# SDSE Project

This repository contains the **Final SDSE Project**, which automates the end-to-end MLOps pipeline using **Dagger** and **GitHub Actions**. The pipeline covers data preprocessing, model training, model selection, and deployment.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [How to Trigger the Workflow](#how-to-trigger-the-workflow)
3. [Pipeline Stages](#pipeline-stages)
4. [Artifacts and Outputs](#artifacts-and-outputs)
5. [CI/CD Integration](#ci-cd-integration)

---

## Project Overview

The project uses **Dagger** for orchestrating the pipeline and **GitHub Actions** for CI/CD automation. The workflow processes raw data, trains machine learning models, selects the best-performing model, and deploys it to staging.

---

## How to Trigger the Workflow

The pipeline is automated via a **GitHub Actions** workflow. You can trigger it in two ways:

1. **Push to the `main` branch**:  
   Simply commit and push changes to the `main` branch. This will automatically run the pipeline.

2. **Manually Trigger the Workflow**:
   - Go to the **Actions** tab in your GitHub repository.
   - Select the **Setup Dagger Pipeline** workflow.
   - Click on **Run Workflow** to trigger it.

---

## Pipeline Stages

The pipeline executes the following steps:

1. **Data Preparation**:
   - Pulls raw data using DVC.
   - Preprocesses data (`preprocessing.py`) to handle missing values and outliers.

2. **Model Training**:
   - Trains machine learning models (`training.py`) using Scikit-Learn and XGBoost.

3. **Model Selection**:
   - Selects the best-performing model based on evaluation metrics (`model_select.py`).

4. **Model Deployment**:
   - Deploys the selected model to staging (`deploy.py`).

---

## Artifacts and Outputs

After the pipeline execution:
- The trained model is stored as an artifact.
- You can find the artifact (`model.pkl`) under the **Artifacts** section in the GitHub Actions tab.

---

## CI/CD Integration

The GitHub Actions workflow (`github_workflow.yml`) automates the following tasks:
- Runs the Dagger pipeline.
- Saves the trained model as an artifact.
- Moves the model to the `output` directory.
- Validates the model using a test action.

---

This ensures a fully automated and reproducible pipeline for training and deploying machine learning models.
