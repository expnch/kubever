# kubever
Simple script to print the container image tags of running Kubernetes deployments, stateful sets, and jobs.

Dependencies: `jq`, `kubectl`

## Usage
```
Usage:
    kubever -h                      Display this help message.
    kubever -v                      Verbose - print resource types.
    kubever -l <key>=<value>        Filter by Kubernetes label.
    kubever -n <namespace>          Use a different namespace.  Defaults to current context.
    kubever -t <type>[,<type>]      Filter by resource types.  Defaults to `deployment,statefulset,job`
    kubever <search term>           Filter output by search term.
```

Example:
```
$ k get po
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-7fd6966748-486b6   1/1     Running   0          1d
nginx-deployment-7fd6966748-f9jsj   1/1     Running   0          1d
nginx-deployment-7fd6966748-g4rlj   1/1     Running   0          1d

$ kubever
 NAME                  VERSION
--------------------  --------------------
 nginx                 nginx:1.14.2 

$ kubever -n kube-system
 NAME                  VERSION
--------------------  --------------------
 coredns               k8s.gcr.io/coredns:1.3.1
```

## To do
- Fix display for pods with multiple containers
- Use `jq` to filter by keyword against resource name instead of `grep` against the entire output
- Add support for CronJobs and standalone Pods
