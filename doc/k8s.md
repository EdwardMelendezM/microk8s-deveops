# GESTION DEL CLUSTER

## Iniciar, detener, reiniciar
microk8s.start
microk8s.stop
microk8s.restart

## Actualizar MicroK8s
sudo snap refresh microk8s --classic --channel=latest/stable

# GESTION DE ADD-ONS

## Listar add-ons
microk8s status --wait-ready

## Habilitar/deshabilitar add-ons
microk8s.enable dns dashboard
microk8s.disable dashboard

# ACCESO AL CLUSTER

## Obtener credenciales
microk8s.kubectl config view --raw

## Configurar kubectl
alias kubectl='microk8s.kubectl'

# DESPLIEGUE DE APLICACIONES

## Crear despliegue
kubectl create deployment nginx --image=nginx

## Escalar despliegue
kubectl scale deployment nginx --replicas=3

# REDES Y ALMACENAMIENTO

## Exponer servicio
kubectl expose deployment/nginx --port=80 --type=NodePort

## Configurar almacenamiento persistente

# SEGURIDAD

## Crear un rol y asignarlo a un usuario
kubectl create role my-role --verb=get,list,watch --resource=pods --namespace=default
kubectl create rolebinding my-role-binding --role=my-role --user=<user>
