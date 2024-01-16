# demo-vector

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This repository contains companion code for the tools in  action talk: "Avec Vector, reprenez le contrôle sur vos données d'observabilité"

## Pre-requisites

### Kubernetes cluster
For demonstration purpose, you can directly run this demo on a local kubernetes cluster like minikube, k3d or kind.

### Application - Emojivoto
To illustrate this tools in action, I deploy [Bunyant Emojivoto application](https://github.com/BuoyantIO/emojivoto) on a running kubernetes cluster.

To deploy this application, run the following command:
```bash
kubectl apply -k emojivoto/base/
```

And then check if it is properly working:

```bash
kubectl get deploy --namespace emojivoto
```

```bash
kubectl get svc --namespace emojivoto
```

You can port forward web-svc to check if service is healthy:
```bash
kubectl port-forward -n emojivoto svc/web-svc 9090:80
```
and open your browser at http://localhost:9090

### Install linkerd

Install Linkerd
```bash
LINKERD2_VERSION=stable-2.14.8 curl -sL https://run.linkerd.io/install | sh
linkerd install | kubectl apply -f -
```

Install Linkerd vizualisation plugin
```bash
linkerd viz install | kubectl apply -f -
```
Check Linkerd installation

```bash
linkerd check
```
### Install jaeger linkerd plugin

Install Linkerd Jaeger plugin and configure Linkerd Opencensus collector to send spans to our Jaeger backend:
```bash
linkerd jaeger install --set collector.jaegerAddr='http://jaeger-collector.tracing:14268/api/traces' | kubectl apply -f -
```
### Install traefik

Install traefik on your cluster
```bash
kubectl apply -k traefik/demo
```

You can check if your installation is correct :
1. Try to access to [Emojivoto homepage](http://emojivoto.127.0.0.1.nip.io/)
2. Try to access to [Traefik dashboard](http://traefik.127.0.0.1.nip.io:8080/dashboard)

### Observability stacks

- Datadog account
- Grafana cloud account

## Vector demo
### Vector installation
>For this demo, I assume to only install vector as a daemonset. It will be deployed in each node of your cluster to
> scrape logs, metrics and traces. For production environment, I recommend to follow instructions on [Vector documentation - Going to production guide](https://vector.dev/docs/setup/going-to-prod/)

To install vector as a daemonset, apply this command:
```bash
kubectl apply -k vector/base
```

In this first step, we configure Vector agent to scrape logs and export them to stdout. Host metrics and internal metrics from vector are exported to a prometheus endpoint.

Check if it is correctly installed:
```bash
kubectl --namespace vector get daemonsets.apps
```
## Conferences

- Touraine Tech - February 2024
- WeShare - February 2023 (WeScale - internal conference)

## References
- My article (in French) on Vector : [Blog WeScale - Vector une solution pour l'observabilité](https://blog.wescale.fr/vector-une-solution-pour-lobservabilit%C3%A9)
- Emojivoto : [Emojivoto - A microservice application](https://github.com/BuoyantIO/emojivoto)

## License

[MIT](https://opensource.org/licenses/MIT)

