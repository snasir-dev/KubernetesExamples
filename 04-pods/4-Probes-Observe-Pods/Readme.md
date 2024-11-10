# Kubernetes - Pods - Probes - Monitoring

## Deploy the pod

    kubectl apply -f pod.yaml -f all-main-probes.yaml

## Look at the pod events

    kubectl describe pod liveness-example

## Access Kubernetes Test Image - e2e-test-images

TO ACCESS ON LOCALHOST - Port Forward as follows.

kubectl port-forward pod/probe-example 8080:8080. Then just go and hit following endpoints.

Then can run following commands

- "curl http://localhost:8080/ready"
- "curl http://localhost:8080/healthz"
- "curl http://localhost:8080/startup"

## Cleanup

    kubectl delete -f pod.yaml --force --grace-period=0 -f all-main-probes.yaml --force --grace-period=0
