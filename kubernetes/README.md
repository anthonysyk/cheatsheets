## Commandes GCP

Connecter kubectl à un projet GKE
```bash
gcloud auth login
gcloud container clusters get-credentials <NAME_OF_CLUSTER> --zone <PROJECT_ZONE> --project <PROJECT_NAME>
```

Supprimer toutes les versions d'une release helm

```bash
for i in {1..100}; do kubectl delete secret "my-release-helm-secret.v$i"; done
```
Modifier le nombre de réplicats d'un pod

```bash
kubectl scale deployment --replicas=0
```

Supprimer tous les pods `Evicted`

```bash
kubectl get pods | grep Evicted | awk '{print $1}' | xargs kubectl delete pod
```
