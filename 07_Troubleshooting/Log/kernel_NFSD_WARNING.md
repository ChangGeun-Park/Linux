kernel: NFSD WARNING: Re-exporting NFS is not a supported configuration in RHEL. Unexpected client behavior may result.

---

### 로그 분석

해당 로그는  "마운트 되어있는 NFS 볼륨을 다시 NFS 공유 볼륨으로 re-exporting 할 때" 발생하는 메시지이다.


NFS/CIFS 공유볼륨을 re-exporting 한 후 해당 공유 볼륨을 또 다른 서버에서 mount 해 사용할 경우 lock contention 이 발생할 수 있다.
경우에 따라 NFS 클라이언트 re-exporting  NFS 서버가 서로를 덮어쓸 수 있어 상당한 데이터 손상이 발생할 수 있다.

관련 KCS : How do I make an NFS/CIFS client re-export a share that it has mounted from another server?  
https://access.redhat.com/solutions/79753


또한 NFS/CIFS 공유볼륨을 re-exporting 하는 것은 현재 어떤 Red Hat Enterprise Linux 버전에서도 공식적으로 지원되지 않는 것으로 파악된다.

관련 KCS :  Is re-export of an NFS/CIFS share supported?
https://access.redhat.com/solutions/6973264


---