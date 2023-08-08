<div align="center">

<img src="https://camo.githubusercontent.com/5b298bf6b0596795602bd771c5bddbb963e83e0f/68747470733a2f2f692e696d6775722e636f6d2f7031527a586a512e706e67" align="center" width="144px" height="144px"/>

### My home operations repository :octocat:

_... managed with Flux, Renovate and GitHub Actions_ 🤖

</div>

<div align="center">

[![Kubernetes](https://img.shields.io/badge/v1.26-blue?style=for-the-badge&logo=k3s&logoColor=white)](https://k3s.io/)

</div>

---

## 📖 Overview

This is a mono repository for my home infrastructure and Kubernetes cluster. Based on [onedr0p/flux-cluster-template](https://github.com/onedr0p/flux-cluster-template) and heavily inspired by [onedr0p/home-ops](https://github.com/onedr0p/home-ops) and [szinn/k8s-homelab](https://github.com/szinn/k8s-homelab)

---

### Installation

My cluster is [k3s](https://k3s.io/) provisioned on VM's running Ubuntu Server using the [Ansible](https://www.ansible.com/) galaxy role [ansible-role-k3s](https://github.com/PyratLabs/ansible-role-k3s). All VM's and workloads are running on a single Dell PowerEdge R720 server with 512GB RAM. Three mirrored ZFS pools are used to host most VM disks. A TrueNAS server is running in a VM and connected to a separate disk tray for storage.

---

## Hardware

| Device               | Count | OS Disk Size | Data Disk Size                | RAM    | Operating System |
| ---------------------| ----- | ------------ | ------------------------------| ------ | ---------------- |
| Dell PowerEdge R720  | 1     | 800 GB       | 2x800 GB, 2x960 GB, 2x500 GB  | 512 GB | Proxmox          |
| Raspberry Pi 4       | 1     |              |                               | 8 GB   |                  |
| Raspberry Pi 4       | 1     |              |                               | 4 GB   |                  |
| Raspberry Pi 4       | 1     |              |                               | 4 GB   |                  |
| IBM EXP3000          | 1     |              | 2x10 TB SATA, 2x14 TB SATA    |        |                  |
| HP 24-port switch    | 1     |              |                               |        |                  |
| Brother Laserprinter | 1     |              |                               |        |                  |
| WIFI6 mesh AP        | 2     |              |                               |        |                  |
| ASUS WIFI router     | 1     |              |                               |        |                  |
| Lenovo MiniPC        | 1     | 1 TB         | 1 TB NVME                     | 16 GB  |                  |


## Virtual Machines

## Networking

### VPN

Sometimes PureVPN will stop working and needs manual updating to get started again (Especially if there's been a network outage, or the VPN's been offline for a while).
To fix this, login to your PureVPN account, go to "Manual Configuration", find the country you want to use and click "Download". Select "WireGuard" protocol and "Linux" device in the popup, and click "Generate Configuration". Download and view the generated .csv file. Get the secret key and IP address listed under the [Interface] section. Replace the values in the vpn/pod-gateway/downloads/secret.sops.yaml file. Commit and push the updated file. A few minutes later the VPN should be working again. Check the logs.
