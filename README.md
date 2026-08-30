# MLOps Pipeline using Dagger

This repository contains an automated end-to-end MLOps pipeline using **Dagger** and **GitHub Actions**. The pipeline covers data preprocessing, model training, model selection, and deployment.

## Project Overview

The project uses **Dagger** for orchestrating the pipeline and **GitHub Actions** for CI/CD automation. The workflow processes raw data, trains machine learning models, selects the best-performing model, and deploys it to staging.

## How to Trigger the Workflow

The pipeline is automated via a **GitHub Actions** workflow. You can trigger it in two ways.

**Push to the `main` branch** — simply commit and push changes to the `main` branch, this will automatically run the pipeline.

**Manually trigger the workflow** — go to the **Actions** tab in your GitHub repository, select the **Setup Dagger Pipeline** workflow, then click **Run Workflow** to trigger it.

## Pipeline Stages

The pipeline executes the following steps.

**Data preparation** — pulls raw data using DVC, then preprocesses it (`preprocessing.py`) to handle missing values and outliers.

**Model training** — trains machine learning models (`training.py`) using Scikit-Learn and XGBoost.

**Model selection** — selects the best-performing model based on evaluation metrics (`model_select.py`).

**Model deployment** — deploys the selected model to staging (`deploy.py`).

## Artifacts and Outputs

After the pipeline execution, the trained model is stored as an artifact. You can find the artifact (`model.pkl`) under the **Artifacts** section in the GitHub Actions tab.

## CI/CD Integration

The GitHub Actions workflow (`github_workflow.yml`) automates the following tasks: runs the Dagger pipeline, saves the trained model as an artifact, moves the model to the `output` directory, and validates the model using a test action.

This ensures a fully automated and reproducible pipeline for training and deploying machine learning models.
