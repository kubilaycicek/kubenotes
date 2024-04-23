MiniKube default context ve hyperV ile ilgili hata gelirse çözüm  :

- minikube start --driver=hyperv
- docker use context default

MiniKube Komutları :

- minikube start  : makinede kubernetes cluster'ı oluşturur.
- minikube start --driver=hyperv | Kullanmak istediğimiz teknolojiyi seçiyoruz.
- minikube status : minikube durumunu gösterir.
- minikube stop   : minikube cluster'ı durdurur.