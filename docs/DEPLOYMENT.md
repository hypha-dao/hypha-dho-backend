# Deploying a new Hypha Backend Kubernetes Cluster
This document describes the process for deploying a Hypha GraphQL Backend using Helm chart on a Kubernetes cluster. It describes how to setup and initialize Kubernetes cluster, how to install Helm and how to install Hypha GraphQL Helm charts.

## Setting up a Hypha Backend Kubernetes Cluster

To set up a Kubernetes cluster, use one of the following methods:
- Use kubeadm to initialize the cluster by running the command kubeadm init.
- Use a managed service like GKE or EKS to set up and configure the cluster.

## Installing Helm
To install Helm on the cluster, run the command:

    curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash

## Selecting and Adding a Helm Chart

To add a chart repository, run the command:

    helm repo add hypha-helm-charts s3://hypha-helm-charts/charts/

To search for a chart in the repository, run the command:

    helm search repo <chart-name>

Available charts are:
- Hypha GraphQL Document Cache Processor - `hypha-helm-charts/doccache`
- Hypha Document Graph Elastic Search Stream processor - `hypha-helm-charts/document-graph-elasticsearch`

## Deploying the Helm Chart
To deploy the chart, run the command:

    helm install <chart-name> --name <release-name> --namespace <namespace>

This command creates the necessary resources defined in the chart, such as pods, services, and ingress routes, and brings the application up and running.

## Managing and Updating the Deployed Chart

To list all the deployed charts in the cluster, run the command:

    helm list

To upgrade the chart to a new version, run the command:

    helm upgrade <release-name> <chart-name>

To roll back to a previous version of the chart, run the command:

    helm rollback <release-name> <revision>
