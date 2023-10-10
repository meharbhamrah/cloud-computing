#### How to Install OpenStack on Ubuntu with DevStack

### What is Openstack
OpenStack is a free, open standard cloud computing platform. It is mostly deployed as infrastructure-as-a-service in public and private clouds where virtual servers and other resources are available to users.

```bash
sudo apt update
```

```bash
sudo apt upgrade
```

```bash
sudo reboot
```

---

```bash
sudo useradd -s /bin/bash -d /opt/stack -m stack
sudo chmod +x /opt/stack
```
---
```bash
echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
```
---
```bash
su - stack
```
---
```bash
sudo apt install git -y
```
---
```bash
git clone https://git.openstack.org/openstack-dev/devstack
```
---
```bash
cd devstack
```
---
```bash
vim local.conf
```
---
```bash
[[local|localrc]]
# Password for KeyStone, Database, RabbitMQ and Service
ADMIN_PASSWORD=StrongAdminSecret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
# Host IP - get your Server/VM IP address from ip addr command
HOST_IP=10.208.0.10
```
---
```bash
./stack.sh
```
---
```bash
[./stack.sh](https://server-ip/dashboard)https://server-ip/dashboard
```
---

