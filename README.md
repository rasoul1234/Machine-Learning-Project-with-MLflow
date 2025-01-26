# End-to-End Machine Learning Project with MLflow

## Overview
This repository demonstrates a complete workflow for building, training, and deploying machine learning models using MLflow. It is designed to ensure reproducibility, scalability, and production-readiness of machine learning pipelines.

---

## Workflows
1. **Update Configuration Files:** Edit `config.yaml`, `schema.yaml`, and `params.yaml` to define project settings, schema validation, and hyperparameters.
2. **Update Entities:** Make required modifications to the entities defined in the project.
3. **Update Configuration Manager:** Enhance the `src` configuration manager to manage project configurations dynamically.
4. **Update Components:** Create or modify reusable components for data preprocessing, modeling, and evaluation.
5. **Update Pipeline:** Define or refine the pipeline structure to orchestrate the workflow.
6. **Update `main.py`:** Ensure the pipeline is executable end-to-end by updating this script.
7. **Update `app.py`:** Implement or improve the application for model inference and user interaction.

---

## How to Run
### Steps:
1. Clone the repository:

   ```bash
   git clone https://github.com/rasoul1234/Machine-Learning-Project-with-MLflow.git
   cd Machine-Learning-Project-with-MLflow
   ```

2. Create a conda environment:

   ```bash
   conda create -n mlproj python=3.8 -y
   conda activate mlproj
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the application:

   ```bash
   python app.py
   ```

5. Access the web application on your local host at the specified port.

---

## MLflow
MLflow is a platform for managing the complete lifecycle of machine learning models. It provides tools for:
- Experiment tracking
- Model management
- Deployment and scaling

### Documentation
For detailed usage, refer to the [MLflow Documentation](https://mlflow.org/docs/latest/index.html).

### Commands
- Launch the MLflow UI locally:

   ```bash
   mlflow ui
   ```

- To enable remote MLflow tracking with Dagshub, export the following environment variables:

   ```bash
   export MLFLOW_TRACKING_URI=https://dagshub.com/entbappy/End-to-end-Machine-Learning-Project-with-MLflow.mlflow
   export MLFLOW_TRACKING_USERNAME=entbappy
   export MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef0
   ```

---

## AWS CI/CD Deployment with GitHub Actions

### Steps:

1. **Login to AWS Console:** Create an IAM user with the following permissions:
   - **AmazonEC2ContainerRegistryFullAccess**
   - **AmazonEC2FullAccess**

2. **Create an ECR Repository:**
   - Save the repository URI (e.g., `566373416292.dkr.ecr.ap-south-1.amazonaws.com/mlproj`).

3. **Launch an EC2 Instance (Ubuntu):**
   - Install Docker on the instance:

     ```bash
     sudo apt-get update -y
     sudo apt-get upgrade -y
     curl -fsSL https://get.docker.com -o get-docker.sh
     sudo sh get-docker.sh
     sudo usermod -aG docker ubuntu
     newgrp docker
     ```

4. **Set Up EC2 as a Self-Hosted Runner:**
   - Go to `Settings > Actions > Runners > New Self-Hosted Runner` in your GitHub repository.
   - Follow the instructions to configure the runner on your EC2 instance.

5. **Configure GitHub Secrets:** Add the following secrets:

   ```bash
   AWS_ACCESS_KEY_ID=<your-access-key>
   AWS_SECRET_ACCESS_KEY=<your-secret-key>
   AWS_REGION=us-east-1
   AWS_ECR_LOGIN_URI=566373416292.dkr.ecr.ap-south-1.amazonaws.com
   ECR_REPOSITORY_NAME=mlproj
   ```

6. **Deployment Workflow:**
   - Build the Docker image of the project.
   - Push the Docker image to ECR.
   - Launch the EC2 instance.
   - Pull the Docker image from ECR.
   - Run the Docker container on the EC2 instance.

---

## About MLflow

### Key Features
- **Production-Ready Platform:** Bridges the gap between experimentation and production.
- **Experiment Tracking:** Logs parameters, metrics, and artifacts for all experiments.
- **Model Management:** Simplifies logging, versioning, and deployment of models.

For additional support, refer to the official MLflow documentation or explore [Dagshub](https://dagshub.com/) for collaborative MLflow tracking.
