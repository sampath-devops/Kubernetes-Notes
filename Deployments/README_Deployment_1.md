# Deployment_1.yaml

This YAML file defines a Kubernetes Deployment named "webapp-deployment" with 4 replicas. It uses a rolling update strategy with maxSurge and maxUnavailable set to 25%, and the type is incorrectly set to "Recreate" (should be "RollingUpdate" for rolling updates). The Pods run a webapp container.