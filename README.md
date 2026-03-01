# Ethereal: Ansible Node Configurator

[![Ansible Linting (Quality Gate)](https://github.com/MarkChisholm-dev/Ethereal-Ansible-Config/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/MarkChisholm-dev/Ethereal-Ansible-Config/actions/workflows/ansible-lint.yml)

[![Ansible](https://img.shields.io/badge/ansible-%23EE0000.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Compliance: TPN](https://img.shields.io/badge/Compliance-TPN--Ready-red?style=for-the-badge)](https://www.ttpn.org/)

## Overview
This repository manages automated post-provisioning configuration for **Ethereal Cloud Systems** compute fleets. It bridges raw cloud infrastructure (Terraform) and a production-ready HPC environment.



## Configuration Layers
1. **OS Baseline Hardening (`common`):** Applies baseline package setup, SSH lockdown, and audit logging controls.
2. **GPU Orchestration (`nvidia_gpu`):** Automates the installation of NVIDIA headless drivers and CUDA toolkits with persistence mode enabled.
3. **HPC Optimization (`hpc_tuning`):** Kernel-level sysctl tuning for high-concurrency TCP throughput and memory mapping.

## Usage
Install required Ansible collections:
```bash
ansible-galaxy collection install -r requirements.yml
```

Ensure your inventory is updated, then execute the site playbook:
```bash
ansible-playbook -i inventory.ini site.yml --limit compute_nodes

```

Optional flags:
- Enable full package dist-upgrade (disabled by default):
```bash
ansible-playbook -i inventory.ini site.yml -e common_perform_dist_upgrade=true
```
- Skip NVIDIA role execution (useful in CI or non-GPU nodes):
```bash
ansible-playbook -i inventory.ini site.yml -e nvidia_gpu_enabled=false
```
