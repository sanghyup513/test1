
### ETCD 클러스터 상태 확인
 sudo ETCDCTL_API=3 /opt/bin/etcdctl endpoint status --write-out=table --endpoints=https://et01:2379,https://et02:2379 --cacert /etc/etcd/pki/ca.crt --cert /etc/etcd/pki/server.crt --key /etc/etcd/pki/server.key
 
### ETCD 클러스터 상태 확인-2
 sudo ETCDCTL_API=3 /opt/bin/etcdctl endpoint health --write-out=table --endpoints=https://met01:2379,https://met02:2379,https://met03:2379 --cacert /etc/etcd/pki/ca.crt --cert /etc/etcd/pki/server.crt --key /etc/etcd/pki/server.key

### 인증서 유효기간 확인
openssl x509 -enddate -noout -in apiserver-etcd-client.crt

### ETCD 인증서 갱신
etcdadm-cert certs renew (모든 etcd)

### ETCD 서비스 재시작
systemctl restart etcd 

### ETCD 서비스 상태 확인 및 인증서 확인

### ETCD 인증서 모든 Master 서버에 복사
ETCD 서버                           Master
apiserver-etcd-client.crt           /etc/kubernetes/pki
apiserver-etcd-client.key           /etc/kubernetes/pki
ca.crt                              /etc/kubernetes/pki/etcd
ca.key                              /etc/kubernetes/pki/etcd

### 모든 Master Kubelet 서비스 재시작
systemctl restart kubelet

### Mkaster 서버 CERT 인증서 갱신 확인
kubeadm certs check-expiration

### 
