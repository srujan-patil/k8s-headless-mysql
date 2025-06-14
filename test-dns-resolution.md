kubectl run -n db -it --rm --restart=Never --image=busybox dns-test -- nslookup mysql-statefulset-0.my-db-headless-service.db.svc.cluster.local
Server:         10.100.0.10
Address:        10.100.0.10:53


Name:   mysql-statefulset-0.my-db-headless-service.db.svc.cluster.local
Address: 192.168.89.97
