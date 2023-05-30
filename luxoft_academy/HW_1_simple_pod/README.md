# Luxoft Academy - "Practical Kubernetes"
## Homw work 1 - simple pod

1. Generate your API key at <https://api.nasa.gov/>

2. use kubectl to secure this key
<https://kubernetes.io/docs/concepts/configuration/secret/>

3. create a pod in your namespase that have access to this secret, echo key and URL

    - use only 1 yaml (not a directory)
    - use busybox container
    - command: echo $URL $TOKEN

4. to check result:

```sh
kubectl get pods
kubectl logs <pod name>
```

5. destroy pod

## results

to store secret i used command:

```sh
kubectl create secret generic nasa-token --from-literal=token="<token>"
```

to create a pod:

```sh
kubectl apply -f busybox.yaml
```

to check results:

```sh
$ kubectl get pods
NAME         READY   STATUS             RESTARTS      AGE
fetch-apod   0/1     CrashLoopBackOff   5 (32s ago)   3m30s

$ kubectl logs fetch-apod
https://api.nasa.gov/planetary/apod <token>
```

to destroy pod:

```sh
$ kubectl delete pod fetch-apod
pod "fetch-apod" deleted

$ kubectl get pods
No resources found in sergei-silantev namespace.
```
