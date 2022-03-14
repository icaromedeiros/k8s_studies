# Deployments

In [this example](https://github.com/openshift-evangelists/kbe/blob/main/specs/deployments/d09.yaml) or
`kbe/specs/deployments/d09.yaml` we see the definition of a replicaset containing two containers

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sise-deploy
spec:
  replicas: 2
  selector:
    matchLabels:
      app: sise
  template:
    metadata:
      labels:
        app: sise
    spec:
      containers:
      - name: sise
        image: quay.io/openshiftlabs/simpleservice:0.5.0
        ports:
        - containerPort: 9876
        env:
        - name: SIMPLE_SERVICE_VERSION
          value: "0.9"
```

So, running, `kubectl apply -f https://raw.githubusercontent.com/openshift-evangelists/kbe/main/specs/deployments/d09.yaml`:
you'd get the following kube pods, replicaset and deployment specifications locally

```
kubectl get pod,replicaset,deployment

NAME                               READY   STATUS    RESTARTS   AGE
pod/sise-deploy-747848cd97-d2hkf   1/1     Running   0          73s
pod/sise-deploy-747848cd97-klr7z   1/1     Running   0          73s

NAME                                     DESIRED   CURRENT   READY   AGE
replicaset.apps/sise-deploy-747848cd97   2         2         2       74s

NAME                          READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/sise-deploy   2/2     2            2           74s
```