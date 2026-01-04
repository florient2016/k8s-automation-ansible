# k8s-automation-ansible

## Overview
This repository contains Ansible playbooks and roles for automating Kubernetes cluster deployment, configuration, and management.

## Prerequisites
- Ansible 2.9+
- Python 3.6+
- kubectl configured
- Access to Kubernetes cluster

## Quick Start

1. **Clone the repository**
    ```bash
    git clone <repository-url>
    cd k8s-automation-ansible
    ```

2. **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ansible-galaxy install -r requirements.yml
    ```

3. **Configure inventory**
    Edit `inventory/hosts.yml` with your cluster details.

4. **Run playbooks**
    ```bash
    ansible-playbook site.yml
    ```

## Directory Structure
```
├── roles/              # Ansible roles
├── playbooks/          # Main playbooks
├── inventory/          # Host inventory files
├── group_vars/         # Group variables
├── host_vars/          # Host variables
└── README.md           # This file
```

## Usage
Review playbooks in `playbooks/` directory and customize variables as needed.

## License
MIT

## Contributing
Submit issues and pull requests to improve this project.