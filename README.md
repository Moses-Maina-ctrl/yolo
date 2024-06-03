# YOLO Web Application

## Overview

This repository contains a web application with a React frontend, an Express backend, and a MongoDB database. The application is containerized using Docker and deployed on a Google Kubernetes Engine (GKE) cluster.

## Accessing the Site

The application is accessible via the following IP address:

arduino

`http://34.28.238.85:3000/`


## Architecture

### Frontend

- **Technology**: React

### Backend

- **Technology**: Express.js

### Database

- **Technology**: MongoDB

## Deployment on GKE

### Step-by-Step Deployment Process

1. **Build Docker Images**
    
    Build the Docker images for the frontend and backend:
    
    

 ```
 docker build -t gcr.io/projectID/yolofrontend:v1 ./frontend docker build -t gcr.io/projectID/yolobackend:v1 ./backend

 ```
    
- **Push Docker Images to Google Container Registry**
    
    Push the built images to Google Container Registry:
    
    
 ```
 docker push gcr.io/projectID/yolofrontend:v1 docker push gcr.io/projectID/yolobackend:v1`
    
- **Create a Kubernetes Cluster on GKE**
    
    Use the Google Cloud Console or `gcloud` CLI to create a GKE cluster.
    
    
 ```
 gcloud container clusters create yolo-cluster --zone us-central1-a --num-nodes=3
 
 ```
    
- **Deploy the Application on GKE**
    
    Apply the Kubernetes manifests to deploy the frontend and backend:
    
    
 `kubectl apply -f backend.yaml kubectl apply -f frontend.yaml`
    
- **Get the External IP**
    
    Retrieve the external IP address assigned to the frontend service:
    
    

1. `kubectl get services`
    
    Note the `EXTERNAL-IP` for `frontend-service`. 
    

### Kubernetes Manifests
 
 ### Frontend Manifest

- **Deployment**: Deploys two replicas of the React frontend application.
- **Service**: Exposes the frontend using a LoadBalancer, which provides an external IP address.

### Backend Manifest

- **Deployment**: Deploys two replicas of the Express backend application.
- **Service**: Exposes the backend using a ClusterIP service, making it accessible only within the cluster.

### MongoDB Manifest

- **Deployment**: Deploys two replicas of the MongoDB database.
- **Service**: Exposes MongoDB using a ClusterIP service.
- **PersistentVolume and PersistentVolumeClaim**: Ensures data persistence by attaching a persistent disk to the MongoDB pods.