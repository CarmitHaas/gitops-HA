# Horsing Around

Horsing Around is a Kubernetes-based application deployment using ArgoCD for GitOps and Helm for package management. This repository contains the configuration for deploying the Horsing Around application along with its dependencies and infrastructure components.

## Architecture

The application is deployed on Amazon EKS and consists of the following main components:

1. Horsing Around Application
2. MongoDB Replica Set
3. Ingress-Nginx Controller
4. Cert-Manager for SSL/TLS
5. Prometheus and Grafana for monitoring
6. EFK Stack for logging

[Will insert an architecture diagram here showing the components and their interactions]

## Repository Structure

- `/horsing-around-umbrella`: Main Helm chart for the Horsing Around application
- `/infra-apps`: Infrastructure applications (cert-manager, ingress-nginx, etc.)
- `/charts`: Subcharts for Horsing Around and MongoDB

## Features

- GitOps-based deployment using ArgoCD
- Automated SSL/TLS certificate management with cert-manager
- MongoDB Replica Set for high availability
- Ingress configuration for external access
- Monitoring with Prometheus and Grafana
- Logging with EFK Stack
- Secrets management using SealedSecrets

## Prerequisites

- Kubernetes cluster (EKS)
- ArgoCD installed on the cluster
- Helm 3
- kubectl

## Deployment

1. Install ArgoCD in your cluster
2. Apply the ArgoCD Application manifests:

```bash
kubectl apply -f horsing-around-app.yaml
kubectl apply -f horsing-around-secrets-app.yaml
kubectl apply -f infra-apps-app.yaml
```

ArgoCD will automatically sync and deploy the applications based on the configuration in this repository.

## Accessing the Application

Once deployed, you can access the Horsing Around application at:

https://horsing-around.zapto.org

## Monitoring and Logging

- Grafana: kubectl port-forward svc/kube-prometheus-stack-prometheus 9090:9090
           kubectl port-forward svc/kube-prometheus-stack-grafana  8080:80
- Kibana:  kubectl port-forward svc/efk-stack-kibana 15601:5601


## Contributing

Feel free to fork this repository and submit pull requests to contribute to this project.
