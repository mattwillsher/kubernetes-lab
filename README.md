# Minikube Development Environment

## Configuration Overview

### Hardware Specifications

- **Memory**: 8GB
- **CPUs**: 4 cores
- **Container Runtime**: containerd
- **Driver**: docker

### Enabled Addons

- `ingress` - NGINX Ingress Controller
- `ingress-dns` - DNS resolution for ingress
- `metrics-server` - Resource metrics API
- `dashboard` - Kubernetes Dashboard UI
- `storage-provisioner` - Dynamic volume provisioning
- `default-storageclass` - Default storage class

### Installed Applications

| Application          | Namespace            | Ingress Address                           | Description                     |
| -------------------- | -------------------- | ----------------------------------------- | ------------------------------- |
| Kubernetes Dashboard | kubernetes-dashboard | [dash.test](http://dash.test)             | Web-based Kubernetes UI         |
| ArgoCD               | argocd               | [argocd.test](http://argocd.test)         | GitOps continuous delivery      |
| Vault                | vault                | [vault.test](http://vault.test)           | Secrets management              |
| Grafana              | monitoring           | [grafana.test](http://grafana.test)       | Metrics visualization           |
| Prometheus           | monitoring           | [prometheus.test](http://prometheus.test) | Metrics collection and alerting |

### Storage Configuration

- **Prometheus Retention**: 2 days
- **Prometheus Storage**: 5Gi persistent volume

### Management Commands

To bring up the environment run: `task bootstrap`.

## Linux DNS

Tested on Fedora with modifications because split DNS and stub on
systemd-resolved don't work as expected and result in lookup failures.

Task assumes `/etc/NetworkManager/NetworkManager.conf` contains:

```conf
[main]
dns=dnsmasq
```

and that is has been restarted `systemctl restart NetworkManager`
