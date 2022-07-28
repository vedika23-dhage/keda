# Introduction

* Kubernetes helps to orchestrate containerized workloads
* Provides a clean interface to manage distributed systems across many nodes, including replication, scaling and state management

# What is Keda

* Kubernetes Event-driven Autoscaling (KEDA) is an autoscaling technology to the built-in Kubernetes Horizontal Pod Autoscaler
* KEDA does not to replace the HPA, it still uses it to do its magic
* KEDA is an open-source Cloud Native project backed by Microsoft
* It is used by big corporations such as Microsoft, Zapier and Alibaba cloud and many others
* The official KEDA website can be found https://keda.sh/

# Why Keda?

* KEDA is a Kubernetes-based Event Driven Autoscaler
* KEDA helps to scale the containers in Kubernetes based on the number of events needing to be processed
* It runs alongside with kubernetes HPA without duplication

# How Keda works?

* KEDA monitors metrics from an external metric provider system
* It communicates directly with the metric provider system

# Type of scaling Keda can do

* Memory based scaling
* CPU based scaling
* Event based scaling