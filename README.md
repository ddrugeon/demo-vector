# demo-vector

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This repository contains companion code for the tools in  action talk: "Avec Vector, reprenez le contrôle sur vos données d'observabilité"

## Pre-requisites

### Kubernetes cluster

### Application - Emojivoto
To illustrate this tools in action, I deploy [Bunyant Emojivoto application](https://github.com/BuoyantIO/emojivoto) on a running kubernetes cluster.

To deploy this application, run the following command:
```bash
kubectl apply -k app/deployment/
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

### Observability stacks

- Datadog account
- Grafana cloud account

## Conferences

- Touraine Tech - February 2024
- WeShare - February 2023 (WeScale - internal conference)

## References
- My article (in French) on Vector : [Blog WeScale - Vector une solution pour l'observabilité](https://blog.wescale.fr/vector-une-solution-pour-lobservabilit%C3%A9)
- Emojivoto : [Emojivoto - A microservice application](https://github.com/BuoyantIO/emojivoto)

## License

[MIT](https://opensource.org/licenses/MIT)

