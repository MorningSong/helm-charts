![Artifact Hub](https://img.shields.io/badge/ArtifactHub-informational?logoColor=white&color=417598&logo=artifacthub&link=https%3A%2F%2Fartifacthub.io%2Fpackages%2Fsearch%3Frepo%3Dvictoriametrics%26verified_publisher%3Dtrue)
![Helm: v3](https://img.shields.io/badge/Helm-v3.14%2B-gray?logo=helm&link=https%3A%2F%2Fgithub.com%2Fhelm%2Fhelm%2Freleases%2Ftag%2Fv3.14.0)
![License](https://img.shields.io/github/license/VictoriaMetrics/helm-charts?labelColor=green&label=&link=https%3A%2F%2Fgithub.com%2FVictoriaMetrics%2Fhelm-charts%2Fblob%2Fmaster%2FLICENSE)
![Slack](https://img.shields.io/badge/Join-4A154B?logo=slack&link=https%3A%2F%2Fslack.victoriametrics.com)
![X](https://img.shields.io/twitter/follow/VictoriaMetrics?style=flat&label=Follow&color=black&logo=x&labelColor=black&link=https%3A%2F%2Fx.com%2FVictoriaMetrics)
![Reddit](https://img.shields.io/reddit/subreddit-subscribers/VictoriaMetrics?style=flat&label=Join&labelColor=red&logoColor=white&logo=reddit&link=https%3A%2F%2Fwww.reddit.com%2Fr%2FVictoriaMetrics)

This repository contains helm charts for VictoriaMetrics and VictoriaLogs.

## Add a chart helm repository (can be skipped for OCI repository)

Access a Kubernetes cluster.

Add a chart helm repository with follow commands:

```console
helm repo add vm https://victoriametrics.github.io/helm-charts/

helm repo update
```

List [all charts](#list-of-charts) and versions of `vm` repository available to installation:
    
```console
helm search repo vm/
```

The command must display existing helm chart e.g.

```shell
NAME                             	CHART VERSION	APP VERSION         	DESCRIPTION
vm/victoria-logs-cluster                0.0.8           v1.25.1                 VictoriaLogs cluster version - high-performance...
vm/victoria-logs-single                 0.11.5          v1.25.1                 Victoria Logs Single version - high-performance...
vm/victoria-metrics-agent               0.19.0          v1.116.0                Victoria Metrics Agent - collects metrics from ...
vm/victoria-metrics-alert               0.18.0          v1.116.0                Victoria Metrics Alert - executes a list of giv...
vm/victoria-metrics-anomaly             1.9.1           v1.22.0-experimental    Victoria Metrics Anomaly Detection - a service ...
vm/victoria-metrics-auth                0.13.0          v1.116.0                Victoria Metrics Auth - is a simple auth proxy ...
vm/victoria-metrics-cluster             0.21.0          v1.116.0                Victoria Metrics Cluster version - high-perform...
vm/victoria-metrics-common              0.0.42                                  Victoria Metrics Common - contains shared templ...
vm/victoria-metrics-distributed         0.14.0          v1.116.0                A Helm chart for Running VMCluster on Multiple ...
vm/victoria-metrics-gateway             0.11.0          v1.116.0                Victoria Metrics Gateway - Auth & Rate-Limittin...
vm/victoria-metrics-k8s-stack           0.45.0          v1.116.0                Kubernetes monitoring on VictoriaMetrics stack....
vm/victoria-metrics-operator            0.45.0          v0.56.0                 Victoria Metrics Operator                         
vm/victoria-metrics-operator-crds       0.1.0           v0.56.0                 Victoria Metrics Operator CRDs                    
vm/victoria-metrics-single              0.18.0          v1.116.0                Victoria Metrics Single version - high-performa...
```

## Installing the chart

Export default values of `victoria-metrics-cluster` chart to file `values.yaml`:

  - For HTTPS repository

    ```console
    helm show values vm/victoria-metrics-cluster > values.yaml
    ```
  - For OCI repository

    ```console
    helm show values oci://ghcr.io/victoriametrics/helm-charts/victoria-metrics-agent > values.yaml
    ```

Change the values according to the need of the environment in ``values.yaml`` file.

Test the installation with command:

  - For HTTPS repository

    ```console
    helm install victoria-metrics vm/victoria-metrics-cluster -f values.yaml -n NAMESPACE --debug --dry-run
    ```

  - For OCI repository

    ```console
    helm install victoria-metrics oci://ghcr.io/victoriametrics/helm-charts/victoria-metrics-cluster -f values.yaml -n NAMESPACE --debug --dry-run
    ```

Install chart with command:

  - For HTTPS repository
    
    ```console
    helm install victoria-metrics vm/victoria-metrics-cluster -f values.yaml -n NAMESPACE
    ```

  - For OCI repository

    ```console
    helm install victoria-metrics oci://ghcr.io/victoriametrics/helm-charts/victoria-metrics-cluster -f values.yaml -n NAMESPACE
    ```

## Validate installation

Get the pods lists by running these commands:

```console
kubectl get pods -A | grep 'victoria-metrics'

# or list all resources of victoria-metrics

kubectl get all -n NAMESPACE | grep victoria
```

Get the application by running this commands:

```console
helm list -f victoria-metrics -n NAMESPACE
```

See the history of versions of ``victoria-metrics`` application with command.

```console
helm history victoria-metrics -n NAMESPACE
```

## How to uninstall VictoriaMetrics

Remove application with command.

```console
helm uninstall victoria-metrics -n NAMESPACE
```

## Kubernetes compatibility versions

helm charts tested at kubernetes versions from 1.28 to 1.30.

## List of Charts

- [VictoriaLogs Single](https://docs.victoriametrics.com/helm/victorialogs-single)
- [VictoriaLogs Cluster](https://docs.victoriametrics.com/helm/victorialogs-cluster)
- [VictoriaMetrics Single](https://docs.victoriametrics.com/helm/victoriametrics-single)
- [VictoriaMetrics Cluster](https://docs.victoriametrics.com/helm/victoriametrics-cluster)
- [VictoriaMetrics Agent](https://docs.victoriametrics.com/helm/victoriametrics-agent)
- [VictoriaMetrics Alert](https://docs.victoriametrics.com/helm/victoriametrics-alert)
- [VictoriaMetrics Anomaly](https://docs.victoriametrics.com/helm/victoriametrics-anomaly)
- [VictoriaMetrics Auth](https://docs.victoriametrics.com/helm/victoriametrics-auth)
- [VictoriaMetrics Gateway](https://docs.victoriametrics.com/helm/victoriametrics-gateway)
- [VictoriaMetrics Distributed](https://docs.victoriametrics.com/helm/victoriametrics-distributed)
- [VictoriaMetrics K8s Stack](https://docs.victoriametrics.com/helm/victoriametrics-k8s-stack)
- [VictoriaMetrics Operator](https://docs.victoriametrics.com/helm/victoriametrics-operator)
- [VictoriaMetrics Operator CRDs](https://docs.victoriametrics.com/helm/victoriametrics-operator-crds)

