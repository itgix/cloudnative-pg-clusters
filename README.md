
# CloudNativePG Helm Clusters
CloudNativePG Helm Charts for Standalone, Backup, PITR and Replica Cluster.


# Prerequisites

## CloudNativePG Helm Charts

[![Stack Overflow](https://img.shields.io/badge/stackoverflow-cloudnative--pg-blue?logo=stackoverflow&logoColor=%23F48024)](https://stackoverflow.com/questions/tagged/cloudnative-pg) [![GitHub License](https://img.shields.io/github/license/cloudnative-pg/charts)](https://github.com/cloudnative-pg/charts/blob/main/LICENSE)

## Operator chart

Helm chart to install the
[CloudNativePG operator](https://cloudnative-pg.io), originally created and sponsored by
[EDB](https://www.enterprisedb.com/) to manage PostgreSQL workloads on any supported Kubernetes cluster
running in private, public, or hybrid cloud environments.

**NOTE**: supports only the latest point release of the CloudNativePG operator.
```console
helm repo add cnpg https://cloudnative-pg.github.io/charts
helm upgrade --install cnpg \
  --namespace cnpg-system \
  --create-namespace \
  cnpg/cloudnative-pg
```

Refer to the [Operator Chart documentation](charts/cloudnative-pg/README.md) for advanced configuration and monitoring.

# Cluster charts

Helm charts to install a CloudNativePG database cluster.

```console
helm upgrade --install cnpg-cluster \
  charts/cnpg-cluster \
  --namespace cnpg-cluster \
  --create-namespace \
```

```console
helm upgrade --install cnpg-cluster-backup \
  charts/cnpg-cluster-backup \
  --namespace cnpg-backup \
  --create-namespace \
```

```console
helm upgrade --install cnpg-cluster-pitr \
  charts/cnpg-cluster-pitr \
  --namespace cnpg-pitr \
  --create-namespace \
```

```console
helm upgrade --install cnpg-cluster-replica \
  charts/cnpg-cluster-replica \
  --namespace cnpg-replica \
  --create-namespace \
```

Clusters names and namespaces can be changed according to the purpose of the cluster/databse.

Refer to the [Cluster Chart documentation](charts/cluster/README.md) for advanced configuration options.
