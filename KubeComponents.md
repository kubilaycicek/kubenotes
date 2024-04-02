Kubernetes Components
=======
* Kube-ApiServer : Komponent ve nodelar ile iletişim noktasıdır.
* Etcd : Tüm metadata cluster verileri key-value şeklinde etcd üzerine tutulur.
* Kube-Scheduler: Yeni oluşturulan ya da bir node ataması yapılmamış Podları izler ve üzerinde çalışcak bir node seçer.
* Kube-Controller-Manager : Cluster durumunu izler istenilen durum ile mevcut durumu izler. Mevcut durum ile istenilen durum arasında fark varsa günceller durumları eşitler.
Örn 3 pod istedik. Mevcutta 2 pod var KCM bunu eşitliyor.

- Node Controller
- Job Controller
- Service Account Token Controller
- Endpoints Controller


Master Node : Control Plane Yönetim Kısmı.
Worker Nodes : Podların olduğu kısım.
Container Runtime : Containerların çalışmasından sorumlu CRI-O.;
Kubelet : Api Server aracılğıyla etcd kontrol eder ve çalışması gereken bir pod varsa bunu çalışmasını sağlar.
kube-proxy: nodelar üzerindeki ağ kurallarını yönetir.




![Kubernets Components](https://github.com/kubilaycicek/kubenotes/blob/main/images/KubeComponents.png?raw=true "Title")
