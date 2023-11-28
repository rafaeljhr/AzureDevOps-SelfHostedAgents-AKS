# Reveal git secrets
```
gpg --import public.key
git secret tell -m <user@example.com> # email from previous imported key
```
```
git secret reveal  # pre-existent public key needed
git secret hide # symmetric key used to encrypt files will now also be encrypted with the new public key
```

# Build and push azure pipelines agent Docker image
```
docker login -u 'USERNAME' -p 'PASSWORD' acragentspool.azurecr.io
docker build --tag "acragentspool.azurecr.io/azure-devops-agent:latest"
docker push acragentspool.azurecr.io/azure-devops-agent:latest
```

# Apply manifests in cluster
```
kubectl apply -f ./secrets/azure-devops-token.yml
kubectl apply -f ./secrets/registry-login.yml
kubectl apply -f agents.yml
kubectl apply -f keda-manifests.yml
kubectl apply -f keda-azure-pipelines.yml
```

