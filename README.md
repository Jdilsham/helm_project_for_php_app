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

## Prerequisites
- Kubernetes cluster (tested on **Minikube**)
- `kubectl`
- `helm`

Check:
```bash
kubectl version --client
helm version
```

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