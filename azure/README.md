# Terraform Crear un Clúster de Kubernetes en Azure (AKS)

Este código de terraform provisionará un servicio AKS en Azure como se detalla a continuación:
* El número de nodos actualmente es 3
* El tamaño de los nodos actualmente es Standard_D2_v2
* El plugin de red actualmente es kubenet

## Requisitos previos

* Terraform 1.0.0
* Configuración de las variables requeridas como:
  - cluster_name
  - dns_prefix
  - resource_group_name
  - agent_count
  - admin_username
* Configuración de variables en el archivo terraform.tfvars
  - aks_service_principal_app_id
  - aks_service_principal_client_secret
* Paquete CLI de kubectl para probar la conexión

## Uso

1. Inicializa terraform primero
 ```bash
terraform init
 ```
1.	Después de la inicialización, puedes planificar tu despliegue de terraform.
 ```bash
terraform plan
 ```
1.	Aplica tu configuración de terraform
 ```bash
terraform apply
 ```
1.	Después de algún tiempo (6-7 minutos), Terraform creará el AKS. Obtén el kubeconfig con
 ```bash
terraform output -raw kubeconfig > aks_kubeconfig
 ```
1.	Exporta el kubeconfig con
 ```bash
export KUBECONFIG=aks_kubeconfig
 ```
1.	Después de obtener el kubeconfig, verifica el estado del clúster con
 ```bash
kubectl get nodes
 ```
