# Seal a Secret

```bash
kubeseal --controller-name sealed-secrets --controller-namespace kube-system --format yaml < unsealed-secret.yaml > sealed-secret.yaml
```
