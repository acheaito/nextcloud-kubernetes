# Kubernetes NextCloud
A [NextCloud](https://nextcloud.com/) Kubernetes deployment with Apache, MariaDB, Cron, and Redis.

## Requirements
* A functional k8s cluster (I used [Rancher](https://rancher.com/what-is-rancher/overview/) to set up mine)
* [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
* [Kustomize](https://github.com/kubernetes-sigs/kustomize)

## Deployment
* Update mariadb/secret.yaml with MYSQL_PASSWORD and MYSQL_ROOT_PASSWORD (can be set to anything, must be base64 encoded) 
* Update nextcloud/ingress.yaml with your kubernetes domain name
* (Optional) To preview generated configuration before deploying:
        `kustomize build -o final-deployment.yaml` 
* Run the following command to build and deploy

        kustomize build | kubectl apply -f - 