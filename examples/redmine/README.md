# Kubernetes task - Redmine

## Objectives

Deploy a high available [Redmine](https://www.redmine.org/) to Kubernetes.

Broken manifests are inside the task folder - those must be fixed.

## TASKS
- Read the following Hints
- Deploy Redmine as Deployment
- Use a LoadBalancer or NodePort service
- Deploy a MySQL with a PersistentVolumeClaim
- Use a Service for the MySQL
- Replace the MySQL Deployment with a stateful set and with volumeClaimTemplates.

## Hints

### LoadBalancer

Information on how to create a LoadBalancer: https://kubernetes.io/docs/concepts/services-networking/#loadbalancer

### Deployments

Information on Deployments: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

### StatefulSets

Information on StatefulSets: https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/

### MYSQL
- The mysql container is listing on the port 3306.
- MYSQL also needs a password set over the environment variable `MYSQL_ROOT_PASSWORD`
 
### Redmine 

The container listens on port 3000.

Redmine has some important environment variables which should be used to configure it:
  
`REDMINE_DB_MYSQL`
Address of the MySQL instance.

`REDMINE_DB_PASSWORD`
Database password of the MySQL instance

`REDMINE_USERNAME`
Default admin username in Redmine

`REDMINE_PASSWORD`
Password of the admin username in Redmine

`REDMINE_EMAIL`
Email address of the admin user in Redmine

`REDMINE_LANG`
Default language of Redmine.
Possible value: `en`
