# INSTALL

## Instalación
sudo snap install microk8s --classic

## Añadir tu usuario al grupo microk8s
sudo usermod -a -G microk8s $USER

## Reiniciar sesión o ejecutar para activar cambios
sudo chown -f -R $USER ~/.kube
