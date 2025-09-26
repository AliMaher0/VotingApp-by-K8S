🗳️ Voting App on Kubernetes

Deploy the classic Docker Voting App on Kubernetes using declarative manifests.
This project demonstrates how to containerize and orchestrate a multi-service application with K8s, Minikube, and kubectl.

Architecture

  The app consists of 5 components:
   - Vote → Python/Flask web app for casting votes
   - Redis → In-memory database for collecting votes
   - Worker → .NET worker service that transfers votes from Redis → PostgreSQL
   - DB (PostgreSQL) → Stores results persistently
   - Result → Node.js web app for displaying results
   
Prerequisites
  - Docker
  - Minikube or any Kubernetes cluster

Deployment Guide
1. Start Minikube
minikube start --driver=docker

2. Create Namespace
kubectl create namespace voting-app

3. Apply Manifests
  kubectl apply -f redis.yaml -n voting-app
  kubectl apply -f db.yaml -n voting-app
  kubectl apply -f vote.yaml -n voting-app
  kubectl apply -f worker.yaml -n voting-app
  kubectl apply -f result.yaml -n voting-app
  kubectl apply -f ingress.yaml -n voting-app   # optional

Accessing the Application

Minikube Service
  minikube service vote 
  minikube service result 
For ingress
You should cat this file "/etc/hosts" and add the below line:

<minikube-ip>  vote.local result.local






