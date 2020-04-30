# kubever
Simple script to print out running versions of Kubernetes containers.

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


## To do
- Fix display for pods with multiple containers
- Use `jq` to filter by keyword against resource name instead of `grep` against the entire output
