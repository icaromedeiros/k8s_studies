# Concepts

Inspired by https://kubebyexample.com/.

All kube by example tutorial can be cloned with `git clone https://github.com/openshift-evangelists/kbe.git`

# Containers

TL;DR Docker.

Isolated space of infrastructure with a more fine-grained management abstraction than VMs.
Kubernetes is basically leveraging and managing containerized applications in different deployment environments.

## Container orchestration features

TL;DR Infra-as-code makes deployments more reliable and flexible to scale

- High availability
- Scalability
- Disaster Recovery

# Pods

https://kubebyexample.com/concept/pods

A pod is a collection of **runnable containers sharing a network**, acting as the basic unit of deployment in Kubernetes.

- All containers in a pod are scheduled on the same node
- Abstract away the container tech, 1 layer above them
- 1 application per pod, so imagine a typical application with HTTP API code in one container + a containerized database, sharing a pod


# Labels

https://kubebyexample.com/en/concept/labels

Labels are the mechanism used to organize Kubernetes objects:
- key-value pair with certain restrictions concerning length and allowed values but without any pre-defined meaning.
- Used to express tags like environments such as "this pod is running in production" or ownership, like "department X owns that pod"

# Deployments

https://kubebyexample.com/en/concept/deployments

A deployment is a supervisor for pods, with fine-grained control over how and when a new pod version is rolled out as well as rolled back to a previous state.

