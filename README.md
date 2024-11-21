# ArgoCD Vault Plugin Test Application

This is a test application demonstrating the ArgoCD Vault Plugin integration.

## Prerequisites
1. Vault is installed and configured
2. ArgoCD is installed with Vault plugin
3. Proper Vault authentication is configured

## Setup
1. Create a test secret in Vault:
   ```bash
   vault kv put secret/test \
     username=testuser \
     password=testpass
   ```

2. Apply the application:
   ```bash
   kubectl apply -f application.yaml
   ```

3. Verify the secret is created and populated:
   ```bash
   kubectl get secret -n vault-test test-secret -o jsonpath='{.data}'
   ```

## Troubleshooting
1. Check ArgoCD logs:
   ```bash
   kubectl logs -n argocd deployment/argocd-repo-server
   ```

2. Verify Vault connection:
   ```bash
   kubectl exec -n argocd deployment/argocd-repo-server -- \
     argocd-vault-plugin generate ./
   ``` # argocd-test-vault
