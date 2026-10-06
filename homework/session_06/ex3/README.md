\# Báo cáo Bài 3: Cấu hình tường lửa UFW và chuẩn đoán cổng mạng



\## 1. Nhật ký các lệnh đã thực hiện



```bash

\# 1. Cấu hình chính sách mặc định

sudo ufw default deny incoming

sudo ufw default allow outgoing



\# 2. Cấp phép lưu lượng SSH và cổng ứng dụng Web

sudo ufw allow 22/tcp

sudo ufw allow 8080/tcp



\# 3. Kích hoạt tường lửa UFW

sudo ufw enable



2\. Kết quả kiểm tra trạng thái tường lửa (sudo ufw status verbose)

Microsoft Windows \[Version 10.0.26200.9457]

(c) Microsoft Corporation. All rights reserved.



C:\\Users\\Admin>ssh root@221.121.4.48

root@221.121.4.48's password:

Permission denied, please try again.

root@221.121.4.48's password:

Permission denied, please try again.

root@221.121.4.48's password:

root@221.121.4.48: Permission denied (publickey,password).



C:\\Users\\Admin>ssh deployer@221.121.4.48

deployer@221.121.4.48's password:

Welcome to Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-63-generic x86\_64)



&#x20;\* Documentation:  https://help.ubuntu.com

&#x20;\* Management:     https://landscape.canonical.com

&#x20;\* Support:        https://ubuntu.com/pro



This system has been minimized by removing packages and content that are

not required on a system that users do not log into.



To restore this content, you can run the 'unminimize' command.

New release '26.04.1 LTS' available.

Run 'do-release-upgrade' to upgrade to it.



Last login: Tue Oct  6 12:13:26 2026 from 183.80.56.158

deployer@lab-practice:\~$ sudo ufw default deny incoming

\[sudo] password for deployer:

deployer is not in the sudoers file.

deployer@lab-practice:\~$ su -

Password:

root@lab-practice:\~# ufw default deny incoming

\-bash: ufw: command not found

root@lab-practice:\~# ufw default allow outgoing

\-bash: ufw: command not found

root@lab-practice:\~# apt update \&\& apt install -y ufw

Get:1 http://security.ubuntu.com/ubuntu noble-security InRelease \[126 kB]

Hit:2 http://archive.ubuntu.com/ubuntu noble InRelease

Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease \[126 kB]

Get:4 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages \[1072 kB]

Get:5 http://archive.ubuntu.com/ubuntu noble-backports InRelease \[126 kB]

Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages \[1370 kB]

Get:7 http://security.ubuntu.com/ubuntu noble-security/main Translation-en \[222 kB]

Get:8 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components \[46.4 kB]

Get:9 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages \[1566 kB]

Get:10 http://security.ubuntu.com/ubuntu noble-security/restricted Translation-en \[361 kB]

Get:11 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components \[212 B]

Get:12 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages \[1216 kB]

Get:13 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en \[244 kB]

Get:14 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components \[76.3 kB]

Get:15 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Packages \[40.3 kB]

Get:16 http://security.ubuntu.com/ubuntu noble-security/multiverse Translation-en \[11.3 kB]

Get:17 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components \[208 B]

Get:18 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en \[305 kB]

Get:19 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components \[181 kB]

Get:20 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages \[1728 kB]

Get:21 http://archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en \[395 kB]

Get:22 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components \[212 B]

Get:23 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages \[1701 kB]

Get:24 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en \[341 kB]

Get:25 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components \[388 kB]

Get:26 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages \[45.7 kB]

Get:27 http://archive.ubuntu.com/ubuntu noble-updates/multiverse Translation-en \[13.3 kB]

Get:28 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components \[940 B]

Get:29 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Packages \[40.6 kB]

Get:30 http://archive.ubuntu.com/ubuntu noble-backports/main Translation-en \[9172 B]

Get:31 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components \[5764 B]

Get:32 http://archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components \[212 B]

Get:33 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Packages \[31.0 kB]

Get:34 http://archive.ubuntu.com/ubuntu noble-backports/universe Translation-en \[18.6 kB]

Get:35 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components \[12.6 kB]

Get:36 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Packages \[748 B]

Get:37 http://archive.ubuntu.com/ubuntu noble-backports/multiverse Translation-en \[340 B]

Get:38 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components \[212 B]

Fetched 11.8 MB in 5s (2265 kB/s)

Reading package lists... Done

Building dependency tree... Done

Reading state information... Done

201 packages can be upgraded. Run 'apt list --upgradable' to see them.

Reading package lists... Done

Building dependency tree... Done

Reading state information... Done

The following additional packages will be installed:

&#x20; iptables libip4tc2 libip6tc2 libjansson4 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 nftables

Suggested packages:

&#x20; firewalld rsyslog

The following NEW packages will be installed:

&#x20; iptables libip4tc2 libip6tc2 libjansson4 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 nftables ufw

0 upgraded, 10 newly installed, 0 to remove and 201 not upgraded.

Need to get 1185 kB of archives.

After this operation, 5241 kB of additional disk space will be used.

Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libip4tc2 amd64 1.8.10-3ubuntu2 \[23.3 kB]

Get:2 http://archive.ubuntu.com/ubuntu noble/main amd64 libip6tc2 amd64 1.8.10-3ubuntu2 \[23.7 kB]

Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libnfnetlink0 amd64 1.0.2-2build1 \[14.8 kB]

Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 libnetfilter-conntrack3 amd64 1.0.9-6build1 \[45.2 kB]

Get:5 http://archive.ubuntu.com/ubuntu noble/main amd64 libnftnl11 amd64 1.2.6-2build1 \[66.0 kB]

Get:6 http://archive.ubuntu.com/ubuntu noble/main amd64 iptables amd64 1.8.10-3ubuntu2 \[381 kB]

Get:7 http://archive.ubuntu.com/ubuntu noble/main amd64 libjansson4 amd64 2.14-2build2 \[32.8 kB]

Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnftables1 amd64 1.0.9-1ubuntu0.1 \[359 kB]

Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 nftables amd64 1.0.9-1ubuntu0.1 \[69.8 kB]

Get:10 http://archive.ubuntu.com/ubuntu noble/main amd64 ufw all 0.36.2-6 \[169 kB]

Fetched 1185 kB in 2s (601 kB/s)

debconf: delaying package configuration, since apt-utils is not installed

Selecting previously unselected package libip4tc2:amd64.

(Reading database ... 111249 files and directories currently installed.)

Preparing to unpack .../0-libip4tc2\_1.8.10-3ubuntu2\_amd64.deb ...

Unpacking libip4tc2:amd64 (1.8.10-3ubuntu2) ...

Selecting previously unselected package libip6tc2:amd64.

Preparing to unpack .../1-libip6tc2\_1.8.10-3ubuntu2\_amd64.deb ...

Unpacking libip6tc2:amd64 (1.8.10-3ubuntu2) ...

Selecting previously unselected package libnfnetlink0:amd64.

Preparing to unpack .../2-libnfnetlink0\_1.0.2-2build1\_amd64.deb ...

Unpacking libnfnetlink0:amd64 (1.0.2-2build1) ...

Selecting previously unselected package libnetfilter-conntrack3:amd64.

Preparing to unpack .../3-libnetfilter-conntrack3\_1.0.9-6build1\_amd64.deb ...

Unpacking libnetfilter-conntrack3:amd64 (1.0.9-6build1) ...

Selecting previously unselected package libnftnl11:amd64.

Preparing to unpack .../4-libnftnl11\_1.2.6-2build1\_amd64.deb ...

Unpacking libnftnl11:amd64 (1.2.6-2build1) ...

Selecting previously unselected package iptables.

Preparing to unpack .../5-iptables\_1.8.10-3ubuntu2\_amd64.deb ...

Unpacking iptables (1.8.10-3ubuntu2) ...

Selecting previously unselected package libjansson4:amd64.

Preparing to unpack .../6-libjansson4\_2.14-2build2\_amd64.deb ...

Unpacking libjansson4:amd64 (2.14-2build2) ...

Selecting previously unselected package libnftables1:amd64.

Preparing to unpack .../7-libnftables1\_1.0.9-1ubuntu0.1\_amd64.deb ...

Unpacking libnftables1:amd64 (1.0.9-1ubuntu0.1) ...

Selecting previously unselected package nftables.

Preparing to unpack .../8-nftables\_1.0.9-1ubuntu0.1\_amd64.deb ...

Unpacking nftables (1.0.9-1ubuntu0.1) ...

Selecting previously unselected package ufw.

Preparing to unpack .../9-ufw\_0.36.2-6\_all.deb ...

Unpacking ufw (0.36.2-6) ...

Setting up libip4tc2:amd64 (1.8.10-3ubuntu2) ...

Setting up libip6tc2:amd64 (1.8.10-3ubuntu2) ...

Setting up libnftnl11:amd64 (1.2.6-2build1) ...

Setting up libjansson4:amd64 (2.14-2build2) ...

Setting up libnfnetlink0:amd64 (1.0.2-2build1) ...

Setting up libnftables1:amd64 (1.0.9-1ubuntu0.1) ...

Setting up nftables (1.0.9-1ubuntu0.1) ...

Setting up libnetfilter-conntrack3:amd64 (1.0.9-6build1) ...

Setting up iptables (1.8.10-3ubuntu2) ...

update-alternatives: using /usr/sbin/iptables-legacy to provide /usr/sbin/iptables (iptables) in auto mode

update-alternatives: using /usr/sbin/ip6tables-legacy to provide /usr/sbin/ip6tables (ip6tables) in auto mode

update-alternatives: using /usr/sbin/iptables-nft to provide /usr/sbin/iptables (iptables) in auto mode

update-alternatives: using /usr/sbin/ip6tables-nft to provide /usr/sbin/ip6tables (ip6tables) in auto mode

update-alternatives: using /usr/sbin/arptables-nft to provide /usr/sbin/arptables (arptables) in auto mode

update-alternatives: using /usr/sbin/ebtables-nft to provide /usr/sbin/ebtables (ebtables) in auto mode

Setting up ufw (0.36.2-6) ...

debconf: unable to initialize frontend: Dialog

debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 79.)

debconf: falling back to frontend: Readline



Creating config file /etc/ufw/before.rules with new version



Creating config file /etc/ufw/before6.rules with new version



Creating config file /etc/ufw/after.rules with new version



Creating config file /etc/ufw/after6.rules with new version

Created symlink /etc/systemd/system/multi-user.target.wants/ufw.service → /usr/lib/systemd/system/ufw.service.

Processing triggers for libc-bin (2.39-0ubuntu8.4) ...

Scanning processes...

Scanning linux images...



Running kernel seems to be up-to-date.



No services need to be restarted.



No containers need to be restarted.



No user sessions are running outdated binaries.



No VM guests are running outdated hypervisor (qemu) binaries on this host.

root@lab-practice:\~# ufw default deny incoming

Default incoming policy changed to 'deny'

(be sure to update your rules accordingly)

root@lab-practice:\~# ufw default allow outgoing

Default outgoing policy changed to 'allow'

(be sure to update your rules accordingly)

root@lab-practice:\~# ufw allow 22/tcp

Rules updated

Rules updated (v6)

root@lab-practice:\~# ufw allow 8080/tcp

Rules updated

Rules updated (v6)

root@lab-practice:\~# ufw status verbose

Status: inactive

root@lab-practice:\~# ufw enable

Command may disrupt existing ssh connections. Proceed with operation (y|n)? y

Firewall is active and enabled on system startup

root@lab-practice:\~# ufw status verbose

Status: active

Logging: on (low)

Default: deny (incoming), allow (outgoing), disabled (routed)

New profiles: skip



To                         Action      From

\--                         ------      ----

22/tcp                     ALLOW IN    Anywhere

8080/tcp                   ALLOW IN    Anywhere

22/tcp (v6)                ALLOW IN    Anywhere (v6)

8080/tcp (v6)              ALLOW IN    Anywhere (v6)



3\. Kết quả chẩn đoán cổng mạng (sudo ss -tlnp)

Plaintext

State    Recv-Q   Send-Q     Local Address:Port      Peer Address:Port   Process

LISTEN   0        128              0.0.0.0:22             0.0.0.0:\*       users:(("sshd",pid=782,fd=3))

LISTEN   0        128                 \[::]:22                \[::]:\*       users:(("sshd",pid=782,fd=4))

4\. Nhận xét \& Đánh giá an ninh

Chính sách Default Deny: Toàn bộ lưu lượng truy cập từ bên ngoài vào đều bị chặn trừ các rule được định nghĩa tường minh, loại bỏ nguy cơ máy chủ bị rà quét cổng trái phép.



Port 22/tcp: Được mở cho phép SSH duy trì quản trị hệ thống từ xa an toàn.



Port 8080/tcp: Đã sẵn sàng mở cửa đón nhận các request từ Internet khi ứng dụng web khởi chạy.





<FollowUp label="Bạn có muốn cấu hình thử nghiệm một service web giả lập bằng python để te

