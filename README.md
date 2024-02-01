# demo-vector

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This repository contains companion code for the tools in  action talk: "Avec Vector, reprenez le contrôle sur vos données d'observabilité"

## Pre-requisites

### tasks
To help installing and executing step by step this demo, you should install [Taskfile](https://taskfile.dev/) on your machine.
### Kubernetes cluster
For demonstration purpose, you can directly run this demo on a local kubernetes cluster like minikube, k3d or kind.

## Demo

> **Note:** Thanks to Taskfile, you can list existing tasks
> ```bash
> task
>```

### Provisioning a Local Kubernetes cluster
I provide some tasks to easily setup a k3d, kind or orb K8s cluster.

#### K3d cluster

To create a k3d cluster:
```bash
task k8s:k3d:create
```

To list existing k3d clusters:
```bash
task k8s:k3d:list
```

To list check k3d cluster:
```bash
task k8s:k3d:check
```

To destroy k3d cluster:
```bash
task k8s:k3d:destroy
```

#### Kind cluster

To create a kind cluster:
```bash
task k8s:kind:create
```

To list existing kind clusters:
```bash
task k8s:kind:list
```

To list check kind cluster:
```bash
task k8s:kind:check
```

To destroy kind cluster:
```bash
task k8s:kind:destroy
```

#### ORB cluster (MacOS X only)

To start a orb cluster:
```bash
task k8s:orb:start
```
To restart a orb cluster:
```bash
task k8s:orb:restart
```
To stop a orb cluster:
```bash
task k8s:orb:stop
```

To list check orb cluster:
```bash
task k8s:orb:check
```

To destroy orb cluster:
```bash
task k8s:orb:destroy
```
### Utilities installation

### Application - Wescale - Microservices-demo

## Conferences

- Touraine Tech - February 2024
- WeShare - February 2023 (WeScale - internal conference)

## References
- My article (in French) on Vector : [Blog WeScale - Vector une solution pour l'observabilité](https://blog.wescale.fr/vector-une-solution-pour-lobservabilit%C3%A9)
- Emojivoto : [Emojivoto - A microservice application](https://github.com/BuoyantIO/emojivoto)

## License

[MIT](https://opensource.org/licenses/MIT)

