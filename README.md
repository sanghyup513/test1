# test1

# ETCD 클러스터 상태 확인
 sudo ETCDCTL_API=3 /opt/bin/etcdctl endpoint status --write-out=table --endpoints=https://et01:2379,https://et02:2379 --cacert /etc/etcd/pki/ca.crt --cert /etc/etcd/pki/server.crt --key /etc/etcd/pki/server.key
 sudo ETCDCTL_API=3 /opt/bin/etcdctl endpoint health --write-out=table --endpoints=https://met01:2379,https://met02:2379,https://met03:2379 --cacert /etc/etcd/pki/ca.crt --cert /etc/etcd/pki/server.crt --key /etc/etcd/pki/server.key

# 인증서 유효기간 확인
openssl x509 -enddate -noout -in apiserver-etcd-client.crt
