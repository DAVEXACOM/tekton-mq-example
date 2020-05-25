## Exploring Ansible

This document captures an exploration into using Ansible with MQ. Later sections explore using Ansible to run the Tekton pipelines and 
using Ansible to change configMaps that contain MQSC definitions and restarting Pods such that the new configuration is picked up
Hence, I have included a copy in this Tekton MQ repos.

THIS DOCUMENT IS A WORK In PROGRESS

## Documentation
tekton-mq-example/doc/AnsibleExploration/QuickGuideToInstallandRunAnsibleOnWinMQonBareMetalRHOCPonIBMCloud.doc

## Contents
Enable Linux subsystem on Windows	7
Install ansible	11
Test SSH into baremetal server from ubuntu on windows	12
Create the inventory file - hosts	13
Test and ansible command - ping	15
Create a playbook to test	15
Set up ansible.cfg file	16
Run a linux command on the bare metal server	18
Run a command to create a file on the bare metal server	18
Create a playbook to create, display and remove a file on baremetal	19
Install a Test MQ system on baremetal	22
Create a queue manager	30
Start the queue manager	30
Configure the queue manager for remote connection	30
Create an mqsc file for Ansible to run	32
Local test of mqsc	32
Using Ansible to administer the MQ queue manager	36
Using command line with the ansible RAW module	36
Using a basic playbook with RAW module	37
Exploring Ansible with Kubernetes	39
Install Kubectl and OC clients on Baremetal server	39
Using SSH to run kubectl/oc commands	41
Using Ansible command line	41
Use ansible command line to kick off the pipeline from Linux subsystem	43
Using the Ansible K8s connection plugin on Linux subsystem	46
Test Connectivity to the cluster from Linux subsystem	46
Set up Ansible for k8s connection plugin	48
K8s inventory source – k8s.yml	48
K8s.yml file config	48
Write a playbook to test the K8s plugin from linux subsystem	49
Run ansible playbook	50
Reconfigure playbook to run against MQ pod	51
modify ansible.cfg to fix unreachable error	51
Rerun the playbook for MQ	52
Manually investigating Config Maps and Deployment Configs	55
Create a config map with an MQSC file	55
Some examples of config Maps with volumes – deployment and pod	56
Modify an MQ deployment config to reference the configMap	59
Final DeploymentConfig for MQ to run MQSCs from ConfigMap	62
Check the Pod has restarted based on the Deployment Config change	65
Using Ansible to change the configMap	66
Create/change the configMap MQSC YAML on the baremetal server	67
Use ansible command line for the apply of the ConfigMap change from Linux subsystem	68
Use ansible command line to restart the Pod from Linux subsystem	69


