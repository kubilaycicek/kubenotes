# Kubectl Genel Kullanımı

Formül şu şekilde : kubectl | verb | object type | object-name 

``` kubectl delete pod test-service ```

Aksini belirtmediğimiz sürece mevcut context ve mevcut namespace ile işlem yapar.

# Kubectl Komutları
* kubectl : tüm komutları listeler.
* kubectl command-name --help : Komut adına göre kullanımını gösterir.
* kubectl cluster-info : Kullandığımız cluster hakkında bilgi edinmek için kullandığımız komut.
* kubectl komut -n (namespace-name) : -n ile namespace belirtilir.
``` kubectl get pods -n kube-system ```
* kubectl get pods -A : Tüm namespacedeki podları getirir.

## -o ile farklı formatlarda gösterim.
* kubectl get pods -A -o wide : Daha detaylı bilgi edinmek için çıktı formatını değiştirdik.
* kubectl get pods -A -o yaml : yaml formatında görüntülüyoruz.
* kubectl get pods -A -o json : json formatında görüntülüyoruz.
* kubectl explain pod | deployment | namespace :  Explain komutu ile objenin nerede olduğunu versiyonunu öğrenebiliriz.
