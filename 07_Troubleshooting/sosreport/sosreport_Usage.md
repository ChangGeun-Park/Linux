# sosreport
---

## Contents
---

### INTRO

sosreport는 RHEL 시스템에서 문제 해결 및 진단을 위해 사용되는 시스템 상태 수집 도구이다. 시스템 관련 문제를 분석할 때 sosreport를 활용하여 다양한 정보를 자동으로 수집하고 압축된 보고서를 생성할 수 있다.

`sos` 패키지를 설치하여 sosreport를 실행할 수 있다.

`sosreport --batch`  명령어를 통해 sosreport를 생성한다. `/var/tmp/` 하위에 `sosreport-{hostname}-{date}-{random}` 생성된다.

---

### Directory Structure

```sh
[root@r86 sosreport-r86-2025-03-04-nzzjdfl]# ll
total 28
dr-xr-xr-x.   5 root root   44 Feb 22 21:43 boot
lrwxrwxrwx.   1 root root   38 Mar  4 16:49 chkconfig -> sos_commands/services/chkconfig_--list
lrwxrwxrwx.   1 root root   32 Mar  4 16:49 date -> sos_commands/systemd/timedatectl
lrwxrwxrwx.   1 root root   37 Mar  4 16:48 df -> sos_commands/filesys/df_-al_-x_autofs
lrwxrwxrwx.   1 root root   31 Mar  4 16:49 dmidecode -> sos_commands/hardware/dmidecode
-rw-r--r--.   1 root root  173 Mar  4 16:50 environment
drwxr-xr-x.  63 root root 4096 Mar  4 10:53 etc
lrwxrwxrwx.   1 root root   24 Mar  4 16:49 free -> sos_commands/memory/free
lrwxrwxrwx.   1 root root   26 Mar  4 16:49 hostname -> sos_commands/host/hostname
lrwxrwxrwx.   1 root root   80 Mar  4 16:49 installed-rpms -> sos_commands/rpm/sh_-c_rpm_--nodigest_-qa_--qf_-59_NVRA_INSTALLTIME_date_sort_-V
lrwxrwxrwx.   1 root root   34 Mar  4 16:49 ip_addr -> sos_commands/networking/ip_-o_addr
lrwxrwxrwx.   1 root root   23 Mar  4 16:49 last -> sos_commands/login/last
lrwxrwxrwx.   1 root root    7 Feb 22 21:30 lib -> usr/lib
lrwxrwxrwx.   1 root root   25 Mar  4 16:49 lsmod -> sos_commands/kernel/lsmod
lrwxrwxrwx.   1 root root   36 Mar  4 16:49 lsof -> sos_commands/process/lsof_M_-n_-l_-c
lrwxrwxrwx.   1 root root   28 Mar  4 16:49 lspci -> sos_commands/pci/lspci_-nnvv
lrwxrwxrwx.   1 root root   29 Mar  4 16:48 mount -> sos_commands/filesys/mount_-l
lrwxrwxrwx.   1 root root   41 Mar  4 16:49 netstat -> sos_commands/networking/netstat_-W_-neopa
dr-xr-xr-x. 242 root root 8192 Feb 22 22:16 proc
lrwxrwxrwx.   1 root root   31 Mar  4 16:49 ps -> sos_commands/process/ps_auxwwwm
lrwxrwxrwx.   1 root root   31 Mar  4 16:49 pstree -> sos_commands/process/pstree_-lp
dr-xr-x---.   2 root root   29 Mar  4 13:40 root
lrwxrwxrwx.   1 root root   32 Mar  4 16:49 route -> sos_commands/networking/route_-n
drwxr-xr-x.   5 root root   54 Mar  4 16:49 run
drwxr-xr-x.  82 root root 4096 Mar  4 16:49 sos_commands
drwxr-xr-x.   2 root root   35 Mar  4 16:50 sos_logs
drwxr-xr-x.   2 root root   74 Mar  5 14:30 sos_reports
drwx------.   4 root root   36 Mar  4 16:49 sos_strings
dr-xr-xr-x.  10 root root  112 Feb 22 22:17 sys
lrwxrwxrwx.   1 root root   28 Mar  4 16:49 uname -> sos_commands/kernel/uname_-a
lrwxrwxrwx.   1 root root   24 Mar  4 16:49 uptime -> sos_commands/host/uptime
drwxr-xr-x.   4 root root   30 Feb 22 21:26 usr
drwxr-xr-x.   6 root root   56 Feb 22 21:57 var
-rw-r--r--.   1 root root   14 Mar  4 16:50 version.txt
lrwxrwxrwx.   1 root root   90 Mar  4 16:49 vgdisplay -> sos_commands/lvm2/vgdisplay_-vv_--config_global_metadata_read_only_1_--nolocking_--foreign
```



