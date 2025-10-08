# Sealed-Secrets How to Guide

The `.gitignore` file is setup to ignore any file names containing the string `unsealed` with this in mind be sure to name any unsealed secrets with this prefix for example: `unsealed-api-key.yaml`

1.  **Create the unsealed secret manifest**

    This file should look something like this

    ```bash
    apiVersion: v1
    kind: Secret
    metadata:
      name: api-key-secret
      namespace: default
    type: Opaque
    stringData:
      APIKEY: "your-api-key-here"
    ```
2.  **Seal the secret**

    Now with the unsealed version complete you can seal the secret so it is encrypted and safe to push to github. Remember that before sealing the secret you must update the namespace to match the namespace the secret will be referenced from or it will not work

    ```bash
    kubeseal --controller-name sealed-secrets --controller-namespace kube-system --format yaml < unsealed-api-key.yaml > sealed-api-key.yaml
    ```
