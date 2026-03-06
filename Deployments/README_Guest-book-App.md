# Guest-book-App.yaml

This YAML file defines a Kubernetes Deployment named "frontend" with 3 replicas for the Guest Book app frontend using a PHP Redis image, and a Service named "redis-slave" to expose Redis slaves on port 6379. Note: The Service is missing apiVersion and kind, and the Deployment has a typo in "matchesLabels" which should be "matchLabels".