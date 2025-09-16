# 🚀 Docker Temelleri

## 🔹 Docker Image ve Container

    Docker Image: Bir uygulamanın çalışması için gereken tüm dosyaları, kütüphaneleri ve bağımlılıkları içeren, paketlenmiş, salt okunur bir şablondur. Örneğin: nginx, ubuntu, redis.

    Docker Container: Bir imajın çalışır halidir. İçinde uygulama izole bir ortamda çalışır.

## 🔹 Docker CLI (Komut Satırı Arayüzü)

### 1. Sistem Bilgilerini Görüntüleme

Docker istemcisinin ve sunucusunun sürüm bilgilerini gösterir.
    
```
docker version
```
Docker'ın kurulu olduğu sistem, aktif konteyner sayısı, depolama sürücüsü ve ağ bilgileri gibi detaylı bilgileri görüntüler.
```
docker info
```
### 2. Konteyner Oluşturma ve Çalıştırma

Belirtilen imajı kullanarak bir konteyner oluşturur ve çalıştırır. Eğer imaj yerel olarak mevcut değilse, otomatik olarak Docker Hub'dan çeker.
    
```
docker run [OPTIONS] IMAGE [COMMAND]
```
Örnek: nginx imajını kullanarak ilkcontainer adında bir konteyner oluşturur ve çalıştırır.
```
docker container run --name ilkcontainer nginx
```
### 3. Konteynerları Yönetme

Çalışan konteynerları listeleme:
```
docker ps
# Veya alternatif olarak
docker container ls
```
Tüm konteynerları (duranlar dahil) listeleme:
```
docker ps -a
# Veya alternatif olarak
docker container ls -a
```
Bir konteyneri durdurma:
```
docker stop <id_or_name>
# Veya
docker container stop <id_or_name>
```
Bir konteyneri silme:
```
docker rm <id_or_name>
# Veya
docker container rm <id_or_name>
```
Birden fazla konteyneri silme:
```
docker rm <id1> <id2> <id3>
```
Çalışan bir konteyneri zorla silme:
```
docker rm -f <id_or_name>
```
### 4. Gelişmiş Komutlar ve Kullanım Örnekleri

Arka planda (detached) konteyner çalıştırma:

-d bayrağı, konteynerın arka planda çalışmasını sağlar.

```  
docker container run -d --name mywebserver nginx
```
Port yönlendirme:
-p bayrağı ile host makinenin bir portunu konteyner içindeki bir porta yönlendirirsiniz. 8080:80 ifadesi, host makinedeki 8080 portunun, konteyner içindeki 80 portuna bağlanacağını belirtir.

```
docker container run -d -p 8080:80 nginx
```

Artık tarayıcınızdan http://localhost:8080 adresine giderek nginx web sayfasını görebilirsiniz.

Konteynerin loglarını görüntüleme:
```
docker logs <id_or_name>
# Veya
docker container logs <id_or_name>
```
Çalışan bir konteynere bağlanma:
exec komutu, çalışan bir konteyner içinde komut çalıştırmak için kullanılır. -it bayrakları, interaktif bir terminal oturumu başlatır.

```
docker exec -it <id_or_name> sh
# Veya
docker container exec -it <id_or_name> sh
```

### Özet Komutlar
```
    docker version : Docker sürüm bilgilerini gösterir.

    docker info : Sistem ve Docker hakkında detaylı bilgi verir.

    docker run : Konteyner yaratır ve çalıştırır.

    docker ps : Çalışan konteynerları listeler.

    docker ps -a : Duranlar dahil tüm konteynerları listeler.

    docker logs : Bir konteynerin loglarını gösterir.

    docker stop : Bir konteyneri durdurur.

    docker rm : Bir konteyneri siler.

    docker exec : Çalışan bir konteyner içinde komut çalıştırır.
```
