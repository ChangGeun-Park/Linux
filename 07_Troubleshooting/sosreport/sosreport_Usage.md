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

- boot/
  - 부트 로더(GRUB 등) 및 커널 관련 파일들이 저장된 디렉토리이다. 
  - 시스템 부팅과 관련된 설정을 확인하는 데 사용될 수 있다. (예: 부트 로더 설정 파일, 커널 이미지 등)
</br>
- chkconfig (심볼릭 링크)
  - `chkconfig_--list` 의 실행 결과를 담고 있으며 시스템 서비스들의 활성화/비활성화 상태를 보여준다
</br>
- date (심볼릭 링크)
  - `timedatectl` 명령어의 실행 결과를 담고 있으며 시스템의 현재 날짜, 시간, 타임존 정보를 보여준다
- df (심볼릭 링크): sos_commands/filesys/df_-al_-x_autofs 파일을 가리키는 심볼릭 링크입니다. df -al -x autofs 명령어의 실행 결과를 담고 있으며, 파일 시스템의 디스크 사용량 정보를 보여줍니다. autofs 파일 시스템은 제외됩니다.
dmidecode (심볼릭 링크): sos_commands/hardware/dmidecode 파일을 가리키는 심볼릭 링크입니다. dmidecode 명령어의 실행 결과를 담고 있으며, 시스템 하드웨어(BIOS, 시스템 보드, 메모리, CPU 등)에 대한 상세 정보를 보여줍니다.
</br>
- environment (파일): 시스템 환경 변수 정보를 담고 있는 일반 파일입니다. sosreport 실행 시점의 환경 변수 설정을 확인할 수 있습니다.
</br>
- etc/: 시스템의 다양한 설정 파일들이 저장된 디렉토리입니다. 네트워크 설정, 시스템 서비스 설정, 사용자 계정 설정 등 중요한 시스템 설정 정보들을 포함합니다.
</br>
- free (심볼릭 링크): sos_commands/memory/free 파일을 가리키는 심볼릭 링크입니다. free 명령어의 실행 결과를 담고 있으며, 시스템 메모리(RAM) 사용량 정보를 보여줍니다.
</br>
- hostname (심볼릭 링크): sos_commands/host/hostname 파일을 가리키는 심볼릭 링크입니다. hostname 명령어의 실행 결과를 담고 있으며, 시스템의 호스트 이름을 보여줍니다.
</br>
- installed-rpms (심볼릭 링크): sos_commands/rpm/sh_-c_rpm_--nodigest_-qa_--qf_-59_NVRA_INSTALLTIME_date_sort_-V 파일을 가리키는 심볼릭 링크입니다. 복잡한 명령어의 실행 결과를 담고 있으며, 설치된 RPM 패키지 목록과 설치 시간 정보를 보여줍니다. 설치된 패키지 버전 및 무결성 검증에 유용합니다.
</br>
- ip_addr (심볼릭 링크): sos_commands/networking/ip_-o_addr 파일을 가리키는 심볼릭 링크입니다. ip -o addr 명령어의 실행 결과를 담고 있으며, 네트워크 인터페이스의 IP 주소 정보를 보여줍니다.
</br>
- last (심볼릭 링크): sos_commands/login/last 파일을 가리키는 심볼릭 링크입니다. last 명령어의 실행 결과를 담고 있으며, 시스템에 성공적으로 로그인한 사용자들의 기록을 보여줍니다.
</br>
- lib (심볼릭 링크): usr/lib 디렉토리를 가리키는 심볼릭 링크입니다. 시스템 라이브러리 파일들이 저장된 디렉토리로 연결됩니다.
</br>
- lsmod (심볼릭 링크): sos_commands/kernel/lsmod 파일을 가리키는 심볼릭 링크입니다. lsmod 명령어의 실행 결과를 담고 있으며, 현재 커널에 로드된 모듈 목록을 보여줍니다.
</br>
- lsof (심볼릭 링크): sos_commands/process/lsof_M_-n_-l_-c 파일을 가리키는 심볼릭 링크입니다. lsof -M -n -l -c 명령어의 실행 결과를 담고 있으며, 열린 파일과 프로세스 정보를 보여줍니다. 네트워크 연결, 파일 핸들 등을 분석할 때 유용합니다.
</br>
- lspci (심볼릭 링크): sos_commands/pci/lspci_-nnvv 파일을 가리키는 심볼릭 링크입니다. lspci -nnvv 명령어의 실행 결과를 담고 있으며, PCI 장치 정보를 상세하게 보여줍니다.
</br>
- mount (심볼릭 링크): sos_commands/filesys/mount_-l 파일을 가리키는 심볼릭 링크입니다. mount -l 명령어의 실행 결과를 담고 있으며, 현재 마운트된 파일 시스템 정보를 보여줍니다.
</br>
- netstat (심볼릭 링크): sos_commands/networking/netstat_-W_-neopa 파일을 가리키는 심볼릭 링크입니다. netstat -W -neopa 명령어의 실행 결과를 담고 있으며, 네트워크 연결 상태, 포트 상태, 라우팅 테이블 등 네트워크 통계 정보를 보여줍니다.
</br>
- proc/: 가상 파일 시스템으로, 현재 실행 중인 프로세스 및 커널 정보를 담고 있습니다. 시스템의 실시간 상태를 반영하며, 프로세스 ID별 디렉토리, 시스템 자원 사용량, 커널 설정 등을 확인할 수 있습니다.
</br>
- ps (심볼릭 링크): sos_commands/process/ps_auxwwwm 파일을 가리키는 심볼릭 링크입니다. ps auxwwwm 명령어의 실행 결과를 담고 있으며, 현재 실행 중인 프로세스 목록과 자원 사용량 정보를 보여줍니다.
</br>
- pstree (심볼릭 링크): sos_commands/process/pstree_-lp 파일을 가리키는 심볼릭 링크입니다. pstree -lp 명령어의 실행 결과를 담고 있으며, 프로세스 트리 구조를 보여줍니다. 프로세스 간의 부모-자식 관계를 파악하는 데 유용합니다.
</br>
- root/: root 사용자의 홈 디렉토리입니다. root 사용자의 개인 설정 파일 등이 저장되어 있을 수 있습니다. (이 예시에서는 권한 때문에 접근이 제한되어 있습니다.)
</br>
- route (심볼릭 링크): sos_commands/networking/route_-n 파일을 가리키는 심볼릭 링크입니다. route -n 명령어의 실행 결과를 담고 있으며, 시스템의 라우팅 테이블 정보를 보여줍니다.
</br>
- run/: 시스템 실행 중 필요한 임시 파일이나 데이터가 저장되는 디렉토리입니다.
</br>
- sos_commands/: sosreport가 수집한 명령어 실행 결과들을 저장하는 디렉토리입니다. 하위 디렉토리로 기능별(filesys, hardware, kernel, networking, process, rpm, services, systemd 등)로 분류되어 있습니다. 심볼릭 링크들은 이 디렉토리 하위의 파일들을 가리킵니다.
</br>
- sos_logs/: sosreport 자체의 실행 로그를 저장하는 디렉토리입니다. sosreport 실행 과정 중 발생한 오류나 경고 메시지를 확인하여 문제 진단에 활용할 수 있습니다.
</br>
- sos_reports/: sosreport 실행 결과 보고서 파일이 저장되는 디렉토리입니다. (이 예시에서는 sosreport 디렉토리만 존재합니다.)
</br>
- sos_strings/: sosreport가 수집한 텍스트 문자열 정보를 저장하는 디렉토리입니다. 특정 명령어의 출력을 텍스트 형태로 저장하거나, 시스템 로그에서 특정 문자열을 추출하여 저장할 수 있습니다.
</br>
- sys/: 커널에서 제공하는 시스템 정보 및 디바이스 정보를 담고 있는 가상 파일 시스템입니다. 하드웨어 정보, 커널 모듈 정보, 시스템 설정 등을 확인할 수 있습니다.
</br>
- uname (심볼릭 링크): sos_commands/kernel/uname_-a 파일을 가리키는 심볼릭 링크입니다. uname -a 명령어의 실행 결과를 담고 있으며, 커널 버전, 시스템 아키텍처 등 시스템 기본 정보를 보여줍니다.
</br>
- uptime (심볼릭 링크): sos_commands/host/uptime 파일을 가리키는 심볼릭 링크입니다. uptime 명령어의 실행 결과를 담고 있으며, 시스템 가동 시간, 사용자 수, 시스템 로드 평균 정보를 보여줍니다.
</br>
- usr/: 시스템에서 사용하는 대부분의 실행 파일, 라이브러리 파일, 문서 파일 등이 저장된 디렉토리입니다.
</br>
- var/: 로그 파일, 스풀 파일, 임시 파일 등 시스템 운영 중에 생성되는 가변적인 데이터들이 저장되는 디렉토리입니다. 로그 분석 및 시스템 상태 변화 추적에 중요한 정보를 포함합니다.
</br>
- version.txt (파일): sosreport의 버전 정보를 담고 있는 일반 파일입니다. 어떤 버전의 sosreport가 사용되었는지 확인할 수 있습니다.
</br>
- vgdisplay (심볼릭 링크): sos_commands/lvm2/vgdisplay_-vv_--config_global_metadata_read_only_1_--nolocking_--foreign 파일을 가리키는 심볼릭 링크입니다. vgdisplay -vv --config global{metadata_read_only=1,nolocking=1,foreign} --foreign 명령어의 실행 결과를 담고 있으며, LVM 볼륨 그룹 정보를 상세하게 보여줍니다. LVM 구성 및 상태를 분석할 때 사용됩니다.



