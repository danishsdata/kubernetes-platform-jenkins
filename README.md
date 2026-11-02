# kubernetes-platform-jenkins

Deployment and service manifests for a small service, a Jenkins
pipeline that tests, builds, and deploys it, and a short runbook for
the failures that come up most.

Portfolio implementation of patterns I use as a DevOps / platform
engineer.

## Run

```
kubectl apply -f k8s/
```

Point Jenkins at this repo and it runs the Jenkinsfile on every push:
checkout, tests, image build, then a rolling deploy with a rollout
status check.
