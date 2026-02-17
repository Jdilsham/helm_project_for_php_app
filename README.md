# PHP + MySQL Helm Chart (Minikube)

This project is a Helm chart that deploys a **PHP application** and a **MySQL database** on Kubernetes.
It includes:
- Namespace (`php-app`)
- PHP Deployment + Service (`php-app`, `php-service`)
- MySQL Deployment + Service (`mysql`, `mysql-service`)
- Persistent storage (PVCs for PHP uploads + MySQL data)
- ConfigMaps (`app-config`, `mysql-init` with `init.sql`)
- Secret (`db-secret`) for MySQL + PHP DB credentials
- Health checks (`/health.php`) for PHP readiness/liveness

---

## Chart Structure
php-app/
  Chart.yaml
  values.yaml
  templates/
    _helpers.tpl
    namespace.yaml
    configmap-app.yaml
    configmap-mysql-init.yaml
    secret-db.yaml
    pvc-php.yaml
    pvc-mysql.yaml
    service-php.yaml
    service-mysql.yaml
    deployment-php.yaml
    deployment-mysql.yaml

---

## Prerequisites
- Kubernetes cluster (tested on **Minikube**)
- `kubectl`
- `helm`

---

## Quick Start (Minikube)

Install the chart:

```helm install php-app ./php-app -n php-app --create-namespace```

Verify resources:

```kubectl get all -n php-app```
```kubectl get pvc -n php-app```
```kubectl get cm -n php-app```
```kubectl get secret -n php-app```

Access the PHP Application:

```kubectl port-forward -n php-app svc/php-service 8080:80```

Open in browser: http://localhost:8080

Uninstall / Cleanup:

```helm uninstall php-app -n php-app```

Helm uninstall does NOT delete PersistentVolumeClaims (PVCs)

Persistent Volumes Cleanup:

```kubectl delete pvc php-pvc mysql-pvc -n php-app```



## Author

Janitha Dilsham
DevOps / Kubernetes / Helm practice project.