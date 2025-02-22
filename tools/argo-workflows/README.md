In order to expose the argo-workflows dashboard locally without ssl add `--secure=false` arg to the argo-server deployment (for the argo-server container)

```yaml
...
- args:                                                                                                                                       - server
  - --auth-mode=server
  - --secure=false
...
```