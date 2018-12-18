## Commandes GCP

Connecter kubectl à un projet GKE
```bash
gcloud auth login
gcloud container clusters get-credentials <NAME_OF_CLUSTER> --zone <PROJECT_ZONE> --project <PROJECT_NAME>
```

