# Helm task - hello-kubernetes

## Objectives

Create a helm chart for our hello-kubernetes application so others can reuse it.

A chart which contains the manifests exists in the hello-kubernetes folder.
All manifests are still "static" and need some templating.
A values.yaml has already been prepared for you.

## Install helm

The tiller already has been deployed and must not been taken care of.
Simply download the helm cli from https://github.com/helm/helm/releases 

## Tasks

- Depending on a variable, it should either use a service of type `ClusterIP` or `LoadBalancer`
- Depending on a variable, it should either deploy the HorizontalPodAutoscaler or not
- All container images must be configurable
- The resources for all containers must be configurable

## Hints

### Namespace

To install a chart into a specific namespace, the `--namespace` flag must be used.
Most commands below use a placeholder variable `$MY_NAMESPACE` which must either be set in the environment or manually replaced.

### Install a chart
```bash
helm install --namespace $MY_NAMESPACE -n hello-kubernetes ./hello-kubernetes
```

### Upgrade a release
```bash
# !!! Take the release name you got during the installation !!!
helm upgrade --namespace $MY_NAMESPACE $RELEASE_NAME ./hello-kubernetes
```

### Delete a release
```bash
# !!! Take the release name you got during the installation !!!
helm delete $RELEASE_NAME
# If you want to reuse the release name, use --purge
```

### Debug/Dry run
To test what helm would install/upgrade the `--debug --dry-run` flags can be used.

### Cause some load on the hello-kubernetes application

```bash
MY_NAMESPACE=default kubectl run \
  load-generator \
  --namespace=$MY_NAMESPACE \
  --generator=run-pod/v1 \
  --image=busybox \
  --command -- /bin/sh -c "while true; do wget -q -O /dev/null http://hello-kubernetes:8080; done"
```

### Check resource usage of pods

```bash
kubectl top pod
```


### Check HPA(Horizontal Pod Autoscaler)

```bash
kubectl get hpa
```
