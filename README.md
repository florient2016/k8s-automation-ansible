# Kubernetes NGINX Deployment with Ansible

## Overview
This playbook deploys an NGINX webserver with a custom web page via Kubernetes NodePort service using Ansible.

## Prerequisites
- Kubernetes cluster running
- `kubernetes.core` Ansible collection installed
- `kubectl` configured
- Local Kubernetes context set to target cluster

## What Gets Deployed

### 1. Namespace
- **Name:** `aap-deploy`
- Isolates all resources for this deployment

### 2. ConfigMap
- **Name:** `nginx-index`
- Contains a responsive HTML5 webinar landing page (French)
- Custom CSS with modern dark theme styling

### 3. Deployment
- **Name:** `nginx`
- **Replicas:** 2
- **Image:** `nginx:1.25`
- Mounts custom index.html from ConfigMap

### 4. Service
- **Type:** NodePort
- **Port:** 80 (internal)
- **NodePort:** 30080
- Exposes NGINX externally

## Running the Playbook

```bash
ansible-playbook main.yml
```

## Access the Webinar Page

**Local access via port-forward:**
```bash
kubectl -n aap-deploy port-forward svc/nginx 8080:80
```
Then visit: `http://localhost:8080`

**Direct NodePort access:**
```
http://<node-ip>:30080
```

## Webinar Details
- **Title:** Gouverner l'automatisation à grande échelle
- **Date:** January 8, 2026
- **Time:** 21:00 (Paris)
- **Duration:** ~60 min + Q&A
- **Format:** Online Live

## Notes
- Update the registration link in HTML (`Je m'inscris` button)
- Replace `miniature.jpeg` with your actual webinar image
- Adjust replicas and nodePort as needed