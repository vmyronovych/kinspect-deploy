In order to expose the argocd dashboard locally without ssl add `--insecure` arg to the argocd-server deployment (for the argocd-server container)

```yaml
...
-·args:
  -·/usr/local/bin/argocd-server
  -·--insecure
...
```