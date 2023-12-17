# microk8s
## Install

- Install microk8s and set authorization
```
sudo snap install microk8s --classic --channel=1.29
sudo usermod -a -G microk8s $USER
mkdir .kube
sudo chown -f -R $USER ~/.kube
su - $USER
```

- Verify status
```
microk8s status --wait-ready
```

- Enable features
```
microk8s enable dns
microk8s enable hostpath-storage
microk8s enable registry
microk8s enable ingress
```

## Configuration
- Copy this
```
{
  "insecure-registries" : ["localhost:32000"]
}
```
- In this path
```
sudo nano `daemon`.json
/etc/docker/daemon.json
```

- Verify docker
```
sudo docker ps -a
sudo systemctl restart docker
```

- Set key in config local
```
microk8s config > $HOME/.kube/config-local
```

- Create new namespace
```
kubectl --kubeconfig=$HOME/.kube/config-local create namespace ASDU
```

