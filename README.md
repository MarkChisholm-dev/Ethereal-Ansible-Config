# Ethereal: Ansible Node Configurator

[![Ansible](https://img.shields.io/badge/ansible-%23EE0000.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Compliance: TPN](https://img.shields.io/badge/Compliance-TPN--Ready-red?style=for-the-badge)](https://www.ttpn.org/)

## Overview
This repository manages the automated post-provisioning configuration for **Ethereal Cloud Systems** compute fleets. It bridges the gap between raw cloud infrastructure (Terraform) and a production-ready HPC environment.



## Configuration Layers
1. **OS Hardening (`common`):** Implements CIS Level 1 benchmarks, SSH lockdown, and audit logging.
2. **GPU Orchestration (`nvidia_gpu`):** Automates the installation of NVIDIA headless drivers and CUDA toolkits with persistence mode enabled.
3. **HPC Optimization (`hpc_tuning`):** Kernel-level sysctl tuning for high-concurrency TCP throughput and memory mapping.

## Usage
Ensure your inventory is updated, then execute the site playbook:
```bash
ansible-playbook -i inventory.ini site.yml --limit compute_nodes
