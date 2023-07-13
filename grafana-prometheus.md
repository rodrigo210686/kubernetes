### Install Prometheus in the Kubernetes cluster.

To do this, make sure you have cloned the Kubernetes charts repo:

```sh
cd ~/
git clone https://github.com/kubernetes/charts
cd charts
git checkout efdcffe0b6973111ec6e5e83136ea74cdbe6527d
cd ../
```
Create a prometheus-values.yml with this content:

```sh
  alertmanager:
    persistentVolume:
      enabled: false
  server:
    persistentVolume:
      enabled: false
```
Use helm to install Prometheus with prometheus-values.yml:

```sh
helm install -f ~/prometheus-values.yml ~/charts/stable/prometheus --name prometheus --namespace prometheus

```
Install Grafana in the Kubernetes cluster.

```sh
cd ~/
git clone https://github.com/kubernetes/charts
```
Create a grafana-values.yml with this content (you will use this password to log in to Grafana):

```sh
adminPassword: somePassword

```
Use helm to install Grafana with grafana-values.yml:

```sh
helm install -f ~/grafana-values.yml ~/charts/stable/grafana --name grafana --namespace grafana

```



