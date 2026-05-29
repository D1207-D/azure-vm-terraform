# azure-vm-terraform

Terraform configuration provisioning a Linux VM on Azure with networking, security, and cloud-init bootstrap.

![HCL](https://img.shields.io/badge/Terraform-HCL-7B42BC?style=flat&logo=terraform)
![Azure](https://img.shields.io/badge/Azure-VM-0078D4?style=flat&logo=microsoftazure)

## Overview

Provisions a complete Azure VM environment from scratch using Terraform, including all networking components, security rules, and SSH-based authentication. Cloud-init script runs on first boot to configure the VM.

## Infrastructure Components

| Resource | Details |
|---|---|
| Resource Group | Scoped resource group for all components |
| Virtual Network | 10.0.0.0/16 address space |
| Subnet | 10.0.1.0/24 dedicated subnet |
| Network Security Group | Inbound rules for SSH (22) and HTTP (80) |
| Public IP | Dynamic public IP for external access |
| Linux VM | Ubuntu 18.04 LTS, Standard_B1s |
| Cloud-init | Bootstrap script on first boot |

## Prerequisites

- Azure subscription
- Terraform >= 1.1.0
- Azure CLI authenticated
- SSH key pair at ~/.ssh/id_rsa

## Getting Started

    git clone https://github.com/D1207-D/azure-vm-terraform.git
    cd azure-vm-terraform
    az login
    terraform init
    terraform plan
    terraform apply

## Variables

| Variable | Description | Default |
|---|---|---|
| labelPrefix | Prefix for all resource names | dani0197 |
| region | Azure region | Canada Central |
| admin_username | VM admin username | daniyal |
| ssh_public_key_path | Path to SSH public key | ~/.ssh/id_rsa.pub |

## Architecture

![Architecture](a05-architecture.png)
