# Insight-DevOps-Tanay-2020

# Orchestration of Kafka on Kubernetes

My project explores the challenge of containerizing Kafka on Kubernetes.  To help achieve this challenge, I have used Terraform to provision the infrastructure, then used the confluent operator to deploy kafka on an EKS Cluster, further I have created a small data pipeline producing json interent stream data on Kafka brokers and consuming it on the kafka-s3 connector. My sink of the pipeline is an amazon s3 bucket which I have created.

## Use Case

Running Kafka on Kubernetes allows organizations to simplify operations such as upgrades, scaling, restarts, and monitoring which are more-or-less built into the Kubernetes platform.First, if you are running most of your other applications and microservices on Kubernetes, it becomes the organizational path of least resistance. 

This is just like how organizations who standardized on VMs have found it very difficult to allocate physical machines with local disks for Kafka.Kubernetes, especially with Confluent Operator, does make it easier to deploy and manage new clusters. Once you get used to Kubernetes (and it does not take long), you’ll see that Kafka management becomes much easier. It becomes easier to scale up—adding new brokers is a single command or a single line in a configuration file. And it is easier to perform configuration changes, upgrades and restarts on all brokers and all clusters.

A key benefit for operations teams of running Apache Kafka on Kubernetes is infrastructure abstraction: it can be configured once and run everywhere. Operations teams in the modern age typically manage diverse arrays of on premises and cloud resources, and Kubernetes allows them to treat these assets as pools of compute resources to which they can allocate their software resources, including Apache Kafka. Furthermore, this same Kubernetes layer allows a single environment for managing all of their Apache Kafka instances.

## Architecture

![architecture](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/Tanay%20insight%20latest%20latest.png)
