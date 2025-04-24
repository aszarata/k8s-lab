### Uruchomienie klastra Kubernetes (Minikube)
```bash
minikube start
```

### Ustawienie Docker ENV dla Minikube
```bash
eval $(minikube docker-env)
```

### Instalacja NFS server i provisioner przez Helm
```bash
helm repo add stable https://charts.helm.sh/stable
helm repo update
helm install nfs-server stable/nfs-server-provisioner --set persistence.enabled=true --set persistence.size=1Gi --set storageClass.name=nfs-storage
```

### Utworzenie Persistent Volume Claim (PVC)
```bash
kubectl apply -f pvc.yaml
```

### Utworzenie Deployment z nginx
```bash
kubectl apply -f deployment.yaml
```

### Utworzenie Service dla nginx
```bash
kubectl apply -f service.yaml
```

### Utworzenie Job, który zapisuje pliki HTML do NFS
```bash
kubectl apply -f job.yaml
```

### Sprawdzenie IP Minikube
```bash
minikube ip
```

### Testowanie serwera HTTP w przeglądarce
```bash
http://<IP>:30007
```

