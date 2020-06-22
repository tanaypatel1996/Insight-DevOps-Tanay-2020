# Insight-DevOps-Tanay-2020

# Orchestration of Kafka on Kubernetes

My project explores the challenge of containerizing Kafka on Kubernetes.  To help achieve this challenge, I have used Terraform to provision the infrastructure, then used the confluent operator to deploy kafka on an EKS Cluster, further I have created a small data pipeline producing json interent stream data on Kafka brokers and consuming it on the kafka-s3 connector. My sink of the pipeline is an amazon s3 bucket which I have created.

![project](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/Screen%20Shot%202020-06-22%20at%2012.25.13%20PM.png)

## Use Case

Running Kafka on Kubernetes allows organizations to simplify operations such as upgrades, scaling, restarts, and monitoring which are more-or-less built into the Kubernetes platform.First, if you are running most of your other applications and microservices on Kubernetes, it becomes the organizational path of least resistance. 

This is just like how organizations who standardized on VMs have found it very difficult to allocate physical machines with local disks for Kafka.Kubernetes, especially with Confluent Operator, does make it easier to deploy and manage new clusters. Once you get used to Kubernetes (and it does not take long), you’ll see that Kafka management becomes much easier. It becomes easier to scale up—adding new brokers is a single command or a single line in a configuration file. And it is easier to perform configuration changes, upgrades and restarts on all brokers and all clusters.

A key benefit for operations teams of running Apache Kafka on Kubernetes is infrastructure abstraction: it can be configured once and run everywhere. Operations teams in the modern age typically manage diverse arrays of on premises and cloud resources, and Kubernetes allows them to treat these assets as pools of compute resources to which they can allocate their software resources, including Apache Kafka. Furthermore, this same Kubernetes layer allows a single environment for managing all of their Apache Kafka instances.

## Architecture

I used Hashicorp terraform to provision my 10 node Amazon EKS cluster, using confluent operator helm charts I have deployed Kafka, zookeeper as stateful sets and exposed them via aws load balancer. Installed the confluent local to communicate with the Kafka brokers inside the EKS cluster.

After that I have produced json stream on the Kafka brokers (which are running on the cloud under the EKS cluster as pods) by command confluent local produce and then set the consumer as the kafka-s3 connect so the sink for my data was amazon s3 and the json data got stored there. Datadog agents were deployed as daemon set to monitor the infrastructure.


![architecture](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/Tanay%20insight%20latest%20latest.png)


## Technologies

![tech_stack](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/Screen%20Shot%202020-06-22%20at%2012.24.49%20PM.png)


## Engineering Challenge

First challenge was understanding the Kubernetes architecture and its definitions which include daemon sets, deployment, stateful set, replica set, ingress controller.

After that, another challenge was dealing with Kafka which is another beast figuring out its networking, advertising so that the brokers could communicat well internally as well as externally and publishing a topic to the producer and sending messages on that topic.

The third challenge was connecting Kafka with s3, creating a topic, publishing real-time json stream on that topic and consuming it on the Kafka connector with s3.

![challenge](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/challenge.png)


## Infrastrcture Monitoring using Datadog

![datadog_dashboard](https://github.com/tanaypatel1996/Insight-DevOps-Tanay-2020/blob/master/images/datadog1.png)




