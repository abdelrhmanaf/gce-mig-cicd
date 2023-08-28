______________________________________________________________________

# CI/CD with Cloud Build for Nginx Web App

This repository demonstrates a continuous integration and deployment (CI/CD) pipeline using Cloud Build on Google Cloud Platform (GCP) for deploying a simple Nginx web application. The pipeline involves building a Docker image, pushing it to Google Artifact Registry, creating an instance template, and managing a managed instance group (MIG) for automatic deployment and scaling.

## Repository Structure

The repository has the following structure:

```
/
|-- nginx.conf
|-- index.html
|-- Dockerfile
|-- cloudbuild.yaml
|-- cd-create/
    |--  cloudbuild.yaml
|-- cd-update/
    |--  cloudbuild.yaml
```

- `nginx.conf`: Configuration file for Nginx server.
- `index.html`: HTML file for the web application.
- `Dockerfile`: Dockerfile for building the Nginx Docker image.
- `cloudbuild.yml`: Cloud Build configuration file for the CI/CD pipeline.

The repository also contains two additional directories, `cd-create/` and `cd-update/`, which represent different stages of the CI/CD pipeline.

## CI/CD Pipeline Overview

The CI/CD pipeline consists of the following steps:

1. **Build and Push Docker Image**: The Docker image is built using the Dockerfile in the root directory. The built image is then pushed to Google Artifact Registry for storage and versioning.

1. **Create Instance Template and MIG (Initial Deployment)**: The instance template is created using the Docker image stored in Google Artifact Registry. A managed instance group (MIG) is then created using the instance template. This step represents the initial deployment of the web application.

1. **Update MIG and Create New Instance Template (Subsequent Deployments)**: Whenever there is an update to the web application, this step is triggered. The MIG is updated with the new Docker image, and a new instance template is created. This allows for seamless rolling updates and scaling of the web application.

## Getting Started

To set up the CI/CD pipeline for the Nginx web app, follow these steps:

1. **Configure Google Cloud Platform**: Set up a project on GCP and enable the necessary APIs, including Cloud Build, Artifact Registry, and Compute Engine.

1. **Configure Cloud Build**: Create 3 Cloud Build trigger that points to the `cloudbuild.yml` file in the repository. This trigger will be responsible for executing the CI/CD pipeline whenever changes are pushed to the repository.

1. **Update Cloud Build Configuration**: Modify the `cloudbuild.yml` file according to your project-specific details, such as the GCP project ID, region, and any customization specific to your web application.

1. **Initial Deployment**: The initial deployment of the web application will be handled automatically by Cloud Build when changes are pushed to the repository. The Docker image will be built, pushed to Artifact Registry, and used to create the instance template and MIG.

1. **Subsequent Deployments**: For subsequent deployments, make updates to the web application by modifying the necessary files (`nginx.conf`, `index.html`, etc.) in the repository. Commit and push the changes to the repository, and Cloud Build will automatically trigger the pipeline to update the MIG with the new Docker image and create a new instance template.

## Contributions

Contributions to this repository are welcome! If you have any suggestions, improvements, or bug fixes, please open an issue or submit a pull request.


______________________________________________________________________
