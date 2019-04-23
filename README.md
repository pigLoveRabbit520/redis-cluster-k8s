# 使用
* 生成StatefulSet：`kubectl create -f redis-sts.yaml`
* 生成Service：`kubectl create -f redis-svc.yaml`
* 启动redis集群：`kubectl exec -it redis-cluster-0 -- redis-cli --cluster create --cluster-replicas 1 $(kubectl get pods -l app=redis-cluster -o jsonpath='{range.items[*]}{.status.podIP}:6379 ')`

# 说明
* 需要使用`StorageClass`动态创建pv
* `StatefulSet`中的serviceName要和Service的metadata中name保持一致

