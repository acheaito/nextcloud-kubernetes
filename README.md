# Kubernetes NextCloud
A [NextCloud](https://nextcloud.com/) Kubernetes deployment with Apache, MariaDB, Cron, and Redis. For more context around the code, see [my article on Medium](https://medium.com/@acheaito/nextcloud-on-kubernetes-19658785b565)

## Requirements
* A functional k8s cluster (I used [Rancher](https://rancher.com/what-is-rancher/overview/) to set up mine)
* A kubernetes storage manager (I user [OpenEBS](https://www.openebs.io/) installed via Rancher catalog)
* [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
* [Kustomize](https://github.com/kubernetes-sigs/kustomize)
* An HTTPS enabled proxy in front of the k8s cluster (e.g: [nginx with Let's Encrypt](https://www.nginx.com/blog/free-certificates-lets-encrypt-and-nginx/))

## Deployment
* Update mariadb/secret.yaml with MYSQL_PASSWORD and MYSQL_ROOT_PASSWORD (can be set to anything, must be base64 encoded) 
* Update nextcloud/ingress.yaml with your kubernetes domain name
* Adjust storage size in nextcloud/pvc.yaml to fit your needs 
* (Optional) To preview generated configuration before deploying:
        `kustomize build -o final-deployment.yaml` 
* Run the following command to build and deploy

        kustomize build | kubectl apply -f -
         
