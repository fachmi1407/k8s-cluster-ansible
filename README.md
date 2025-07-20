# Kubernetes Cluster Ansible Automation

Automasi setup Kubernetes cluster (1 Master + 2 Worker) menggunakan Ansible di Ubuntu dengan Docker sebagai container runtime.

---

## 📦 Komponen

- Ubuntu 20.04/22.04 (semua node)
- Docker
- kubeadm, kubelet, kubectl
- Flannel CNI

---

## 🗺️ Topologi

+---------+ +--------+ +--------+
| Master | --> | Node 1 | --> | Node 2 |
+---------+ +--------+ +--------+

---

Master : 192.168.50.20
Node 1 : 192.168.50.21
Node 2 : 192.168.50.22


---

### 🚀 Cara Menjalankan

```bash
1. Install Ansible
sudo apt install ansible -y

2. Clone Repository

git clone https://github.com/fachmi1407/k8s-cluster-ansible.git
cd k8s-cluster-ansible

3. Pastikan Akses SSH Tanpa Password ke Semua Node

ssh-copy-id quadrant@192.168.50.20
ssh-copy-id quadrant@192.168.50.21
ssh-copy-id quadrant@192.168.50.22

4. Jalankan Playbook

ansible-playbook -i inventory.ini playbook.yml

✅ Verifikasi

Login ke master:
ssh quadrant@192.168.50.20
kubectl get nodes

🧰 Struktur Project

k8s-cluster-ansible/
├── inventory.ini
├── playbook.yml
└── roles/
    ├── common/
    ├── docker/
    ├── kubernetes/
    ├── master/
    └── worker/

