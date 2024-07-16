Install MicroStack on an ubuntu server 22.04

`sudo snap install openstack --channel 2024.1/edge`

Results:

```bash
ubuntu@ubuntu:~$ sudo snap install openstack --channel 2024.1/edge
openstack (2024.1/edge) 2024.1 from Canonical✓ installed
```

`sunbeam prepare-node-script | bash -x && newgrp snap_daemon`

Results:
```bash
ubuntu@ubuntu:~$ sunbeam prepare-node-script | bash -x && newgrp snap_daemon
++ lsb_release -sc
+ '[' jammy '!=' jammy ']'
++ whoami
+ USER=ubuntu
++ id -u
+ '[' 1000 -eq 0 -o ubuntu = root ']'
+ SUDO_ASKPASS=/bin/false
+ sudo -A whoami
+ sudo grep -r ubuntu /etc/sudoers /etc/sudoers.d
+ grep NOPASSWD:ALL
+ dpkg -s openssh-server
+ sudo usermod --append --groups snap_daemon ubuntu
+ '[' -f /home/ubuntu/.ssh/id_rsa ']'
+ ssh-keygen -b 4096 -f /home/ubuntu/.ssh/id_rsa -t rsa -N ''
Generating public/private rsa key pair.
Your identification has been saved in /home/ubuntu/.ssh/id_rsa
Your public key has been saved in /home/ubuntu/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:06lvwacsrJWwuLINRi4/qZTSD4h8N+aDJG7sA7x8wIk ubuntu@ubuntu
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|                 |
|                 |
|         . .     |
|+ o   . S.o      |
|E@.. . o +o .    |
|X+@oo+..+. +     |
|o@=B+o..o.+      |
|+o=++.o. o.      |
+----[SHA256]-----+
+ cat /home/ubuntu/.ssh/id_rsa.pub
++ hostname --all-ip-addresses
+ ssh-keyscan -H 192.168.122.146
# 192.168.122.146:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
# 192.168.122.146:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
# 192.168.122.146:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
# 192.168.122.146:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
# 192.168.122.146:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
+ grep -E 'HTTPS?_PROXY' /etc/environment
+ curl -s -m 10 -x '' api.charmhub.io
+ sudo snap connect openstack:ssh-keys
+ sudo snap install --channel 3.5/stable juju
juju (3.5/stable) 3.5.2 from Canonical✓ installed
+ mkdir -p /home/ubuntu/.local/share
+ mkdir -p /home/ubuntu/.config/openstack
++ snap list openstack --unicode=never --color=never
++ grep openstack
+ snap_output='openstack  2024.1   559  2024.1/edge  canonical**  -'
++ awk -v col=4 '{print $col}'
+ track=2024.1/edge
+ [[ 2024.1/edge =~ edge ]]
+ risk=edge
+ [[ edge != \s\t\a\b\l\e ]]
+ sudo snap set openstack deployment.risk=edge
+ echo 'Snap has been automatically configured to deploy from' 'edge channel.'
Snap has been automatically configured to deploy from edge channel.
+ echo 'Override by passing a custom manifest with -m/--manifest.'
Override by passing a custom manifest with -m/--manifest.
```

`sunbeam cluster bootstrap --accept-defaults`

Results:
```bash
ubuntu@ubuntu:~$ sunbeam cluster bootstrap --accept-defaults
Node has been bootstrapped with roles: control, compute
```


`sunbeam configure --accept-defaults --openrc demo-openrc`


`sunbeam launch ubuntu --name test`