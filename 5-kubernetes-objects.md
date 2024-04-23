# Kubernetes Objects
Kubernetes üzerindeki her şey api objesidir.

* Pod : Kubernetes içindeki en küçük birimdir. Bir veya birden fazla container barındırılabilir.

## Pod Oluşturma
kubectl run pod-name --image = resource --restart=Never
- kubectl run firstpod --image=nginx --restart=Never
```
C:\>kubectl run firstpod --image=nginx --restart=Never
pod/firstpod created
```
## Podları listele
```
C:\>kubectl get pods -o wide
NAME       READY   STATUS    RESTARTS   AGE   IP           NODE       NOMINATED NODE   READINESS GATES
firstpod   1/1     Running   0          50s   10.244.0.4   minikube   <none>           <none>
```
## Describe Komutu

Objeler hakkında daha fazla bilgi almak için bu komut kullanılır.

* kubectl describe object-name

```
C:\>kubectl describe pod firstpod
Name:             firstpod
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Tue, 23 Apr 2024 15:26:23 +0300
Labels:           run=firstpod
Annotations:      <none>
Status:           Running
IP:               10.244.0.4
IPs:
  IP:  10.244.0.4
Containers:
  firstpod:
    Container ID:   docker://c976cb27221ca6031afc50e9e5443009d5cc4e94f8bfc7b16e0ceb1226f74e41
    Image:          nginx
    Image ID:       docker-pullable://nginx@sha256:0463a96ac74b84a8a1b27f3d1f4ae5d1a70ea823219394e131f5bf3536674419
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Tue, 23 Apr 2024 15:26:34 +0300
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-ljw6p (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  kube-api-access-ljw6p:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  3m23s  default-scheduler  Successfully assigned default/firstpod to minikube
  Normal  Pulling    3m24s  kubelet            Pulling image "nginx"
  Normal  Pulled     3m15s  kubelet            Successfully pulled image "nginx" in 8.199s (8.199s including waiting)
  Normal  Created    3m13s  kubelet            Created container firstpod
  Normal  Started    3m13s  kubelet            Started container firstpod
  ```

## Log Komutu

Pod loglarına erişmek için log komutu kullanılır.
```
C:\>kubectl logs firstpod
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/04/23 12:26:34 [notice] 1#1: using the "epoll" event method
2024/04/23 12:26:34 [notice] 1#1: nginx/1.25.5
2024/04/23 12:26:34 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14)
2024/04/23 12:26:34 [notice] 1#1: OS: Linux 5.15.133.1-microsoft-standard-WSL2
2024/04/23 12:26:34 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/04/23 12:26:34 [notice] 1#1: start worker processes
2024/04/23 12:26:34 [notice] 1#1: start worker process 29
2024/04/23 12:26:34 [notice] 1#1: start worker process 30
2024/04/23 12:26:34 [notice] 1#1: start worker process 31
2024/04/23 12:26:34 [notice] 1#1: start worker process 32
2024/04/23 12:26:34 [notice] 1#1: start worker process 33
2024/04/23 12:26:34 [notice] 1#1: start worker process 34
2024/04/23 12:26:34 [notice] 1#1: start worker process 35
2024/04/23 12:26:34 [notice] 1#1: start worker process 36
2024/04/23 12:26:34 [notice] 1#1: start worker process 37
2024/04/23 12:26:34 [notice] 1#1: start worker process 38
2024/04/23 12:26:34 [notice] 1#1: start worker process 39
2024/04/23 12:26:34 [notice] 1#1: start worker process 40
```
Logları canlı olarak izlemek için "-f" ile canlı olarak izleyebiliriz.

## Exec Komutu
Çalışan pod içinde komut çalıştırmak için kullanılır.

```
kubectl exec firstpod -- hostname (hostname,ls, gibi çeşitli terminal komutlarını çalıştırabiliriz.)
```
##  Delete Komutu
Pod silmek için kullanılır.
* kubectl delete pod-name
```
C:\>kubectl delete pods  firstpod
pod "firstpod" deleted
```