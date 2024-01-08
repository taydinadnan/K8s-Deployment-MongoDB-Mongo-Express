# MongoDB and Mongo Express Deployment Demo

This demo project demonstrates how to deploy MongoDB and Mongo Express using Kubernetes. The project consists of several YAML files, each responsible for a specific component of the deployment. The files include `mongo.yaml` (deployment and service for MongoDB), `mongo-secret.yaml` (for storing sensitive information), `mongo-express.yaml` (deployment for Mongo Express), and `mongo-configmap.yaml` (for configuration settings).

## Prerequisites
- Kubernetes cluster set up and configured
- `kubectl` command-line tool installed and configured to connect to your cluster

## Steps to Deploy

### 1. Create Secret for MongoDB

Before deploying MongoDB, create a Kubernetes Secret to securely store sensitive information such as the MongoDB root password.

```bash
kubectl apply -f mongo-secret.yaml
```

### 2. Deploy MongoDB

Deploy MongoDB using the provided YAML file.

```bash
kubectl apply -f mongo.yaml
```

### 3. Create ConfigMap for MongoDB

Apply the ConfigMap to set custom configurations for MongoDB (e.g., setting the storage engine, journaling, etc.).

```bash
kubectl apply -f mongo.yaml
```

### 4. Deploy Mongo Express

Deploy the Mongo Express service to provide a web-based interface for MongoDB management.

```bash
kubectl apply -f mongo-express.yaml
```

### 5. Accessing MongoDB and Mongo Express

Wait for the pods to be in the Running state, and then access MongoDB and Mongo Express.

MongoDB
To connect to MongoDB, you can use the internal service created:

```bash
kubectl get services
# Find the service for MongoDB (usually named "mongodb-internal-service")
# Use the ClusterIP to connect to MongoDB
```

Mongo Express
To access the Mongo Express web interface externally, use the external service created:

```bash
kubectl get services
# Find the service for Mongo Express (usually named "mongo-express-external-service")
# Use the external IP and port to access the Mongo Express web interface
```


### 6. Clean Up

Deploy the Mongo Express service to provide a web-based interface for MongoDB management.

```bash
kubectl delete -f mongo-express.yaml
kubectl delete -f mongo-configmap.yaml
kubectl delete -f mongo.yaml
kubectl delete -f mongo-secret.yaml
```


Note: Ensure you have backups of your data before deleting resources.

Now, you have successfully deployed MongoDB and Mongo Express on Kubernetes! Adjust the configuration files as needed for your specific use case.