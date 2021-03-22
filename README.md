# dotnet-local-k8s-demo
Demo for Tulsa User Group

This is from the perspective of running from Windows and not trying to leveral WSL. WSL doesn't support systemd which makes these other solutions a tad challenging.

## MicroK8s

```
microk8s kubectl apply -f https://raw.githubusercontent.com/phillipsj/dotnet-local-k8s-demo/main/src/manifests/blazork8s.yaml
```

```
multipass list
Name         State   IPv4             Image
microk8s-vm  Running 172.27.219.42    Ubuntu 18.04 LTS
```

```
http://<ip address above>:30036
```

# K3D

Again, all from the Windows perspective.

Installation

```
choco install k3d
```

```
k3d cluster create tulsa -p "8082:30036@agent[0]" --agents 2
```

```
kubectl apply -f https://raw.githubusercontent.com/phillipsj/dotnet-local-k8s-demo/main/src/manifests/blazork8s.yaml
```

```
http://localhost:8082/
```



