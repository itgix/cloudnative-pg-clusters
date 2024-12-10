# CloudNativePG Example Configurations
This directory contains example configurations (values.yaml files) for deploying CloudNativePG clusters with Helm. These examples demonstrate common configurations, such as enabling backups to MinIO or Azure storage accounts and specifying PostgreSQL parameters.

## Prerequisites
Before using these examples, ensure that the following prerequisites are met:

**Credentials:**

- Backup configurations require valid credentials for external storage services (e.g., MinIO, Azure Blob Storage or S3 bucket).
- Create Kubernetes Secrets to store these credentials. For example:
	- **Azure:** Store the `connectionString` in a Secret (e.g., azure-credentials) with a key named `AZURE_BLOB_STRING`.
MinIO: Provide access and secret keys in a similar Secret format.

**Certificates (if required):**

Ensure TLS certificates are available and configured for secure connections to backup storage systems.

**Storage Providers:**

We have used MinIO and Azure Blob Storage for tests in the provided configurations. You can adapt these to other storage providers with similar configurations - Google Cloud Storage and AWS S3.

**Storage Class (Optional)**:

Ensure a suitable storage class exists in your Kubernetes cluster for persistent volume claims (PVCs).
Update the storageClass field in the values.yaml file as necessary.

## Example Configurations
### 1. **Standalone Cluster (cnpg-cluster)**
   
This example configures a standalone PostgreSQL cluster with:

- Default settings for PostgreSQL parameters
- Backup disabled by default:
```console
backup:
  enabled: false
```
- Update the fields in a custom `values.yaml` file based on your environment requirements

### 2. Backup Configuration
The backup section in the example enables:

- Full backups with immediate checkpoints
- Backup retention policy of 30 days (by default)
- Scheduled backups with the cron expression `0 0 0 * * *` (daily at midnight UTC)

You can modify the fields in a custom `values.yaml` file based on your environment requirements


### 3. Point-in-Time Recovery (PITR)

The point_in_time_recovery field demonstrates how to configure PITR scenarios. To use PITR:

- Set `point_in_time_recovery: true`.
- Ensure proper WAL archiving is configured.


### 4. Resource Configuration
The example provides resource requests and limits for PostgreSQL instances and connection poolers (`pgbouncer`). Adjust these settings based on your cluster's resource availability and workload requirements.

### 5. Monitoring
Monitoring can be enabled using the enablePodMonitor field. This integrates with monitoring tools like Prometheus to provide visibility into cluster performance.


## Notes
- These examples are not production-ready configurations. They are designed for demonstration purposes and must be customized for specific environments.
- Always validate your Kubernetes cluster configuration, storage classes, and credentials before applying the examples.
- For detailed configuration options, refer to the CloudNativePG Helm Chart Documentation.

---
## Pending Features

We are actively working on enhancing these configurations with the following features:

1. **Testing with Additional Storage Providers**:
   - Complete test for **Google Cloud Storage** for backups.
   - Complete test for **AWS S3** for backups.

2. **Replica Clusters Across Multiple Regions**:
   - Configuring and testing replica clusters deployed across different regions for improved disaster recovery and fault tolerance.

Stay tuned for updates as we extend support for these use cases.