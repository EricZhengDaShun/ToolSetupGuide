# VirtualBox

---

## Mount Shared Folder

### 1. Add User to `vboxsf` Group

```bash
sudo usermod -aG vboxsf $USER
```

> **Note:** You need to log out and log back in for the change to take effect.  

---

### 2. Configure `fstab` / Systemd Mount

#### 2.1 Get Your UID and GID

```bash
id -u; id -g
```

Assume the output is `1000` and `1000`.  

---

#### 2.2 Example Setup

- Shared folder name in VirtualBox: **shared**  
- Mount point on guest system: **/mnt/shared**  

##### `/etc/systemd/system/mnt-shared.mount`

```ini
[Unit]
Description=VirtualBox Shared Folder /mnt/shared
After=vboxservice.service

[Mount]
What=shared
Where=/mnt/shared
Type=vboxsf
Options=uid=1000,gid=1000,dmode=0775,fmode=0664
```

##### `/etc/systemd/system/mnt-shared.automount`

```ini
[Unit]
Description=Automount VirtualBox Shared Folder /mnt/shared

[Automount]
Where=/mnt/shared

[Install]
WantedBy=multi-user.target
```

---

#### 2.3 Enable and Start

```bash
sudo mkdir -p /mnt/shared
sudo systemctl daemon-reload
sudo systemctl enable --now mnt-shared.automount
```
