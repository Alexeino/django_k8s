> [
>  {
>   "cloudName": "AzureCloud",
>   "homeTenantId": "edf442f5-b994-4c86-a131-b42b03a16c95",
>   "id": "d425194f-e7b6-4dc0-8325-21f1693bad83",
>   "isDefault": true,
>   "managedByTenants": [],
>   "name": "Free Trial",
>   "state": "Enabled",
>   "tenantId": "edf442f5-b994-4c86-a131-b42b03a16c95",
>   "user": {
>     "name": "email_id",
>     "type": "user"
>   }
> }
]

**Useful commands**
- kubectl exec <pod_name> -it -- //bin/bash => Login to Pod
- kubectl delete -f <deployment.yaml>

**AZ container registry**
-   First build the image out of Dockerfile using > docker build -t tag Dockerfile_DIR 
-   Login to AZ if isn't > az login 
-   Connect to registry > az acr login --name registry_name
-   Push image using > docker push image_name
-   djangok8s.azurecr.io/webapp


**Generate DJANGO Superuser password using env secret**
-   $ python -c "import secrets;print(secrets.token_urlsafe(32))" => Will generate a secret random string to use as password since we don't have to remember it just paste into env

**Generate Django Secret Key using Djagno get_random()**
-   python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"

**Load Secrets to Kubernetes Cluster from an env file**
-   kubectl create secret generic django-k8s-web-prod-env --from-env-file=web/.env.prod
-   kubectl get secret django-k8s-web-prod-env -o YAML => To see the secrets

**What to do if any of secret is updated or changed**
-   We can delete the secret and create a new one 
-   kubectl delete secret django-k8s-web-prod-env
-   kubectl create secret generic django-k8s-web-prod-env --from-env-file=web/.env.prod 


psql "host=djangok8spostgres.postgres.database.azure.com port=5432 dbname=djangok8spostgres user=djangok8sadmin@djangok8spostgres password=M#ni7h@2024 sslmode=require"
