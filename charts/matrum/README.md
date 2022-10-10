# MATRUM
Matrum is a synapse matrix-server that focuses on an easy setup.

## Requirements
- Kubernetes cluster with ingress and cert manager
- Helm

## Installation

### Helm configuration
1. In the values.yml file replace all occurrences of `example.com` with the domain that you want to use for your matrix server.
1. Uncomment the config lines related to the domains you just changed.

### Deploy to server
From project root run `helm install matrum .`

### Add SRV record
At your DNS provider add an SRV record with these values:
- Service: `_matrix`
- Protocol: `_tcp`
- Priority: `10`
- Weight: `0`
- Port: `443`
- Target: `your.domain.com.` (the host name of your Matrum ending with a period)

### Register a user
Since user registration is disabled by default, you will need to create the (first) user by hand using a script inside the container.
1. Get into the container: `kubectl exec -it <matrum-pod> bash`
1. Run: `register_new_matrix_user -c /data/homeserver.yaml http://localhost:8008`

## Apply changes
From root folder of this project: `helm upgrade matrum .`