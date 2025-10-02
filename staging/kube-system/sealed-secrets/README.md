# Seal a Secret

```bash
apiVersion: v1
kind: Secret
metadata:
  name: secret-name
  namespace: namespace-where-secret-is-referenced
type: Opaque
stringData:
  access-token: "secret-text-value"
```

```bash
kubeseal --controller-name sealed-secrets --controller-namespace kube-system --format yaml < unsealed-secret.yaml > sealed-secret.yaml
```
