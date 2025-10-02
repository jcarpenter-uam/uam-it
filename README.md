# UAM-IT

## Setup

### Find your virtio disk

```bash
talosctl get disk -n $CONTROL_PLANE_IP --insecure
```

### Generate your config replacing install disk if necessary

```bash
talosctl gen config --install-disk "/dev/vda" talos-proxmox-cluster https://$CONTROL_PLANE_IP:6443 --output-dir talos --install-image factory.talos.dev/installer/ce4c980550dd2ab1b17bbf2b08801c7eb59418eafe8f279833297925d67c7515:v1.11.0
```

### For my setup I wanted only 3 control plane nodes

- uncomment the very last line in the controlplane.yaml config file to allow schedueling pods on the control plane nodes

### Apply the config to all nodes

```bash
talosctl apply-config --insecure --nodes $CONTROL_PLANE_IP --file talos/controlplane.yaml
```

### Bootstrap cluster

```bash
export TALOSCONFIG="talos/talosconfig"
talosctl config endpoint $CONTROL_PLANE_IP
talosctl config node $CONTROL_PLANE_IP
```

```bash
talosctl bootstrap
```

```bash
talosctl kubeconfig .
```
