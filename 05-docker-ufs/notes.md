# 🗂️ Docker Katmanlı Dosya Sistemi (Union File System)

Docker, Union File System (UFS) kullanarak imajları ve konteynerleri katmanlı bir yapı halinde saklar. Bu yapı sayesinde disk alanı verimli kullanılır ve tekrar eden katmanlar birden fazla kez tutulmaz.

## 🔹 Docker Image

- Bir Docker image, temel bir Linux işletim sistemi (ör. alpine, ubuntu) üzerine kurulur.
- Image içerisinde yaptığımız her değişiklik (örneğin hello.sh dosyası oluşturmak, CMD eklemek) yeni bir katman (layer) olarak tutulur.
- Image sadece okunabilir (Read-Only) yapıdadır.

## 🔹 Docker Container

- Bir image çalıştırıldığında üzerine yazılabilir (Read-Write) bir katman eklenir ve buna container denir.
- Container içinde yapılan tüm değişiklikler sadece bu yazılabilir katmana kaydedilir ve yalnızca o container için geçerlidir.
- Her container’ın kendine ait bir yazılabilir katmanı vardır.

## 🔹 Copy-on-Write (COW)

- Eğer Read-Only katmandaki bir dosyada değişiklik yapmak isterseniz:
- Docker dosyayı yazılabilir katmana kopyalar.
- Değişiklikler bu kopya üzerinde yapılır.
- Bu mekanizmaya Copy-on-Write (COW) denir.

## 🔹 Katmanlı Yapının Avantajı

- Docker her imajı katmanlı olarak sakladığından, aynı katman birden fazla image tarafından kullanılabilir.
- Böylece aynı katmanlar tekrar tekrar disk üzerinde yer kaplamaz.
- Depolama alanı ve ağ transferi açısından büyük avantaj sağlar.

## 🔹 Kullanışlı Komutlar
Durmuş containerları temizlemek:
```
docker container prune
```
Sistemdeki tüm imajları silmek:
```
docker image prune -a
```
Komutu çalıştırdığınızda şu uyarıyı alırsınız:
```
WARNING! This will remove all images without at least one container associated to them.
Are you sure you want to continue? [y/N]
```
y dediğinizde kullanılmayan tüm imajlar silinir ve disk alanı boşaltılır.

Örnek çıktı:
```
Deleted Images:
untagged: hello-world:latest
deleted: sha256:1b44b5a3e06a9aae883e7bf25e45c100be0bb81a0e01b32de604f3ac44711634
untagged: nginx:latest
deleted: sha256:41f689c209100e6cadf3ce7fdd02035e90dbd1d586716bf8fc6ea55c365b2d81
...
Total reclaimed space: 476.5MB
```
## 📌 Özet

- Image: Salt okunur katmanlardan oluşur.
- Container: Image üzerine eklenen yazılabilir katmandır.
- Copy-on-Write: Read-Only dosyaları değiştirmek istediğimizde kopyalanıp yazılabilir katmana alınır.
- Katmanlı yapı: Depolama ve performans avantajı sağlar.
