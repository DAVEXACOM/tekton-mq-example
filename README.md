## IBM MQ Deployment using Tekton Pipelines

Tekton is an open source project to configure and run CI/CD pipelines within a Kubernetes cluster.
This repos as created for use with davearno/ibm-mqadvanced-server-tls-tekton.
This IBM MQ v9.1.n build is enabled to TLS connection from off Cluster client tools and applilcations

THIS REPOS IS A WORK In PROGRESS

## Documentation
tekton-mq-example/doc/Install and Test Tekton on RHOCP 4.3.5 beta on IBM Cloud.doc

## Introduction

Example file set to build and deploy IBM MQ TLS enabled container on RHOCP with Tekton

## Instructions

You will need your RHOCP adminstrator to grant your user and namespace pipeline access rights OR follow other tekton tutorial instructions for creating a service account for pipelines.


mqdeploymentconfig\ibmmq.yaml creates the deployment config in RHOCP and has a copy in the https://github.com/DAVEXACOM/ibm-mqadvanced-server-tls-tekton

mqdeploymentconfig\create-tt-mq-service.yaml - a service definition to expose the mq deployment created by tekton - I have not included this in the pipeline - I manually create it in RHOCP

mqdeploymentconfig\create-tt-mq-route.yaml - a route definition to expose the mq deployment created by tekton - I have not included this in the pipeline - I manually create it in RHOCP

tekton directory has the tekton YAML files for building and deploying with
	
	a) Kaniko - do not use these
	
	b) Buildah - I took the published standard Buildah clustertask and refactored it as a ("user") task with parameter and resource settings that are a match for Kaniko. This way the rest of the tekton artifacts remain unchanged and Kaniko and buildah source-to-image( build and push) tasks can be swapped in and out when Kaniko has the root user restriction removed at some point.

Use OC CREATE commands to load the tekton artifacts into your RHOS environment

mqtls-git.yaml
mqtls-source-to-image-buildah.yaml
mqtls-deploy-using-kubectl-common.yaml
mqtls-build-and-deploy-pipeline-buildah.yaml
mqtls-pipeline-buildah-run.yaml

oc create -f c:\users\DAVIDARNOLD\IBM\gitREPOS\tekton-mq-example\tekton\run\mqtls-pipeline-buildah-run.yaml - this is the last command - it creates the "run" which starts the pipeline

USE OC REPLACE if you change and files
oc replace -f c:\users\DAVIDARNOLD\IBM\gitREPOS\tekton-mq-example\tekton\tasks\mqtls-source-to-image-buildah.yaml

USE OC DELETE -f c:\temp\tempyaml.yaml to remove any artifacts from RHOCP - use a yaml snippet in a file to identify kind: , name: and namespace: see example tempyaml.yaml below

apiVersion: tekton.dev/v1alpha1
kind: Task
metadata:
  creationTimestamp: '2020-03-03T00:27:03Z'
  generation: 3
  name: source-to-image
  namespace: da-build-project
## Test IBM MQ TLS
