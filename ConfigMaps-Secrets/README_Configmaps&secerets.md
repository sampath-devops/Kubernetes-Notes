# Configmaps&secerets.yaml

This YAML file defines a ConfigMap named "app-config" with APP_COLOR, a Secret named "app-secret" with a base64-encoded password, and a Pod that injects these via envFrom and mounts.