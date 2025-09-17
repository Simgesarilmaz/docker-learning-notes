# Docker Volume – Container Dışı Veri Saklama

## 📌 Neden Volume?
- Container’lar kısa ömürlüdür (stop / rm sonrası içindeki data kaybolur).
- Uzun ömürlü veri saklamak için volume kullanılır.
- Volume, host makinede `/var/lib/docker/volumes/` altında saklanır.
- İstersek NFS, AWS gibi harici storage driverları da kullanılabilir.

---

## 📂 Volume Oluşturma
```
docker volume create ilkvolume
```
Detayları görmek için:
```
docker volume inspect ilkvolume
```
Çıktıda şunlar bulunur:
- CreatedAt
- Driver
- Mountpoint (dosyaların bulunduğu fiziksel path)
- Name
  
## 🐳 Container ile Volume Kullanımı

Volume’u container içine mount etme:
```
docker container run -it -v ilkvolume:/uygulama alpine sh
```
Container içinde uygulama klasörüne yazılan dosyalar artık volume’de saklanır.
Container silinse bile volume kalır.

## 🔄 Volume Tekrar Kullanımı

Aynı volume farklı containerlarda kullanılabilir:
```
docker container run -it -v ilkcolume:/deneme alpine sh
docker container run -it -v ilkcolume:/deneme2 ubuntu sh
```
Read-only mount:
```
docker container run -it -v ilkcolume:/deneme3:ro ubuntu sh
```
📥 Mount Senaryoları

- Eğer volume boş, container path de boşsa → boş görürsün.
- Eğer container path’te dosya varsa, volume boşsa → dosyalar volume’e kopyalanır.
- Eğer volume doluysa (dosya içeriyorsa) → volume’deki içerik container path’in üzerine yazılır (volume önceliklidir).

## 🧹 Geçici Container

Container kapandığında otomatik silmek için:
```
docker container run --rm -it alpine sh
```
## 🎯 Özet

- Volume = Container dışı, kalıcı data saklama.
- Container silinse bile volume korunur.
- Birden fazla container aynı volume’ü paylaşabilir.
- :ro ile read-only kullanılabilir.
- Mount edilen klasör boş değilse, volume içeriği her zaman önceliklidir.















