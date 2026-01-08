# Kubernetes Automation Ansible

This repository contains automation scripts for deploying Kubernetes manifests and managing persistent volumes using Ansible.

## Overview

The project includes playbooks that facilitate the deployment of Kubernetes resources and the management of persistent storage.

## Playbook: Deploy Kubernetes Manifest

The `deploy-manifest.yaml` playbook is designed to apply Kubernetes manifests using Ansible. Below is a brief overview of its structure:

```yaml
# playbooks/deploy-manifest.yml
- name: Deploy Kubernetes manifest
  hosts: localhost
  gather_facts: false

  vars:
    manifest_path: "manifests/app.yaml"   # override in Template if you want

  tasks:
    - name: Apply manifest (kubectl apply equivalent)
      kubernetes.core.k8s:
        state: present
        src: "{{ manifest_path }}"
```

### Variables
- `manifest_path`: Path to the Kubernetes manifest file to be applied.

## Persistent Volume Configuration

The `aap.yaml` file defines a Persistent Volume (PV) for use in Kubernetes. Here is the configuration:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: aap-pv
spec:
  accessModes:
    - ReadWriteMany
  capacity:
    storage: 100Gi
  persistentVolumeReclaimPolicy: Retain
  nfs:
    path: /shares/registry
    server: 10.10.0.2
```

### Specifications
- **Access Modes**: ReadWriteMany
- **Storage Capacity**: 100Gi
- **Reclaim Policy**: Retain
- **NFS Server**: 10.10.0.2
- **NFS Path**: /shares/registry

## Usage

To deploy the Kubernetes manifest, run the following command:

```bash
ansible-playbook playbooks/deploy-manifest.yml
```

Ensure that your Kubernetes cluster is accessible and that the necessary permissions are granted for the deployment.

## Conclusion

This repository provides a streamlined approach to managing Kubernetes resources and persistent storage using Ansible. For further customization, modify the variables in the playbooks as needed.