# Service Mesh: Crash Course on ISTIO

Based on
<https://www.youtube.com/watch?v=Cn2LHqdHwXM>

## K3S with wsl2

<https://gist.github.com/ibuildthecloud/1b7d6940552ada6d37f54c71a89f7d00>
<https://boxofcables.dev/deploying-rancher-on-k3s-on-wsl2/>

`/mnt/c/Users/eric/k3s-local.yaml` must have th right ip addr as shown by
`ip addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}'`

## istio on k3s

```bash
sudo ./k3s server

sudo ./k3s kubectl create namespace istio-tutorial

./istio-1.12.0/bin/istioctl analyze -c k3s-local.yaml

sudo ./k3s kubectl label namespace istio-tutorial istio-injection=enabled

// install istio
./istio-1.12.0/bin/istioctl install --set profile=demo -y -c k3s-local.yaml
./istio-1.12.0/bin/istioctl verify-install --kubeconfig k3s-local.yaml

sudo ./k3s kubectl apply -f istio-1.12.0/samples/bookinfo/platform/kube/bookinfo.yaml -n istio-tutorial


```
