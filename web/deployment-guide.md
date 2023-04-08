1. ### Test Django Project locally 
```
python manage.py test
```

2. ### Build container image and Push to container registry
```
docker build -t <tag_name> Dockerfile
docker push <tag_name/image_name>
```

3. ### Update Secrets (if setup)
```
kubectl delete secret <secret_name>
kubectl create secret generic <secret_name> --from-env-file=<.env file_path>
```
 