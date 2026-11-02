# Runbook: app on Kubernetes

Pods not starting: kubectl get pods, then kubectl describe pod <name>.
Check events for image pull errors or missing resources.

Rollout stuck: kubectl rollout status deployment/app. If the new version
is bad, kubectl rollout undo deployment/app puts the last good version
back.

Service not reachable: kubectl get svc app, check the selector matches
the pod labels, and check the readiness probe on /health.

Database connection errors: check the secret name the deployment mounts
and confirm the database endpoint is reachable from the cluster.
