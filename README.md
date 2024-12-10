
# CloudNativePG Helm Clusters Charts
CloudNativePG Helm Charts for Standalone, Backup, PITR (Point-in-Time Recovery) and Replica Cluster.

## Prerequisites

### CloudNativePG Helm Charts

[![Stack Overflow](https://img.shields.io/badge/stackoverflow-cloudnative--pg-blue?logo=stackoverflow&logoColor=%23F48024)](https://stackoverflow.com/questions/tagged/cloudnative-pg) [![GitHub License](https://img.shields.io/github/license/cloudnative-pg/charts)](https://github.com/cloudnative-pg/charts/blob/main/LICENSE)

### Operator chart

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

Refer to the [Operator Chart documentation](https://github.com/cloudnative-pg/cloudnative-pg) for advanced configuration and monitoring.

## Cluster charts

Helm charts to install a CloudNativePG database cluster.

#### Standalone Cluster
```console
helm upgrade --install cnpg-cluster \
  charts/cnpg-cluster \
  --namespace cnpg-cluster \
  --create-namespace 
```

#### Backup Cluster 
```console
helm upgrade --install cnpg-cluster-backup \
  charts/cnpg-cluster-backup \
  --namespace cnpg-backup \
  --create-namespace 
```

#### Point-in-Time Recovery (PITR) Cluster
```console
helm upgrade --install cnpg-cluster-pitr \
  charts/cnpg-cluster-pitr \
  --namespace cnpg-pitr \
  --create-namespace 
```

#### Replica Cluster
```console
helm upgrade --install cnpg-cluster-replica \
  charts/cnpg-cluster-replica \
  --namespace cnpg-replica \
  --create-namespace 
```

**Note:** Customize cluster names and namespaces to suit your application requirements. 
Refer to the provided [example configurations ](charts/examples) for guidance on deploying different cluster setups.
Refer to the [Cluster Chart documentation](https://github.com/cloudnative-pg/charts/blob/main/charts/cluster/README.md) for advanced configuration options.
