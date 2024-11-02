# Deploying Terraform Script using Jenkins

This repository provides an example of deploying infrastructure using Terraform and Jenkins pipelines. The goal is to automate the provisioning of cloud resources with Terraform, using Jenkins to manage the continuous integration and deployment process for consistent and reliable infrastructure deployments.

## Table of Contents

- Overview
- Requirements
- Setup
- Jenkins Pipeline
- Usage
- Best Practices
- Troubleshooting
- Contributing

## Overview

This project is designed to:
- Automate infrastructure deployment using Terraform.
- Use Jenkins to trigger deployments when changes are pushed to specific branches.
- Implement security best practices for managing sensitive information (e.g., using Jenkins credentials for secrets).

### Key Technologies
- Terraform: Infrastructure as Code (IaC) tool for provisioning and managing cloud resources.
- Jenkins: Open-source automation server for continuous integration and deployment.

## Requirements

1. Jenkins installed with access to configure pipelines.
2. Terraform (version >= 1.x) installed on the Jenkins server or agents.
3. Cloud Provider Account (e.g., AWS, GCP, Azure) and corresponding credentials for Terraform to interact with the cloud provider.
4. Jenkins Credentials configured to store sensitive information such as access keys, region, etc.

## Setup

1. Clone this Repository:
   ```bash
   git clone https://github.com/paulaali/Deploying-Terraform-script-using-Jenkins.git
   cd Deploying-Terraform-script-using-Jenkins
   
2. Configure Jenkins Credentials:

Go to your Jenkins dashboard, navigate to Manage Jenkins > Manage Credentials.
Add credentials for the required environment variables, such as:
TF_VAR_access_key: Access key for the cloud provider.
TF_VAR_secret_key: Secret key for the cloud provider.
TF_VAR_region: Desired region for infrastructure deployment.
Review Terraform Files:

Inspect the main.tf file and adjust any configurations or resources according to your requirements.
Run terraform init locally to initialize the Terraform working directory.
Jenkins Pipeline
The Jenkins pipeline (Jenkinsfile) is configured with the following stages:

Validate: Checks Terraform syntax and validates configuration.
Plan: Creates an execution plan to show the resources that will be created, modified, or destroyed.
Apply: Deploys the changes to the cloud infrastructure.

## Usage

Push Changes: Make changes to your Terraform configuration files and push them to your repository.
Run Pipeline: Jenkins will automatically trigger the pipeline if it's set up to poll the repository or via a webhook.
Review and Approve: If applicable, review the plan output before applying changes.

## Best Practices

Use Remote Backend: Configure Terraform to use a remote backend for securely storing the state file.
Modularize Terraform Code: Organize resources into modules to improve code reusability and readability.
Use Jenkins Environment Scopes: Configure separate pipelines for different environments (e.g., staging, production).

## Troubleshooting

Pipeline Failures: Review the pipeline logs in Jenkins for errors related to syntax or permissions.
Terraform State Conflicts: Ensure no other processes are accessing the state file concurrently.
Insufficient Permissions: Check IAM policies if using AWS or equivalent permissions in your cloud provider account.

## Contributing

Contributions are welcome. Please open an issue to discuss any changes or improvements.
