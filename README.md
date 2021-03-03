# MATRUM
Matrum is a synapse matrix-server to be installed on a kubernetes cluster

## Requirements
- Kubernetes cluster

## Installation
1. In the values.yml file replace all occurrences of `example.com` with the domain that you want to use for your matrix server.
1. From project root run `helm install matrum .`