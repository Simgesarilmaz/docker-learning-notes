# 01 - Docker Giriş

## Docker Nedir?
Docker, uygulamaları ve onların ihtiyaç duyduğu bağımlılıkları tek bir paket içinde çalıştırmayı sağlayan bir platformdur.  
Geliştiricinin bilgisayarında çalışan bir uygulama, Docker sayesinde test ve üretim ortamında da aynı şekilde çalışır. Böylece “bende çalışıyor ama sende çalışmıyor” sorununu ortadan kaldırır.

---

## İşletim Sistemi ve Çekirdek
Bir bilgisayarın kalbi işletim sistemidir. İşletim sistemi, donanımı yönetir ve üzerinde çalışan uygulamalara hizmet verir.  
İşletim sisteminin en önemli parçası **çekirdek (kernel)**’tir. Kernel, CPU, bellek, disk ve ağ gibi kaynakların düzenlenmesini sağlar.  

Docker ve container teknolojisi, kernelin sunduğu **namespace** ve **cgroups** gibi özellikleri kullanarak her uygulamayı izole eder. Yani aynı işletim sistemi üzerinde birden fazla bağımsız ortam çalıştırılabilir.

---

## Sanallaştırma
Geleneksel olarak, aynı fiziksel sunucuda birden fazla uygulama çalıştırmak için **sanal makineler (VM)** kullanılırdı.  
Her VM, kendi işletim sistemine sahiptir ve bu nedenle daha ağırdır. Bu da açılış sürelerinin uzun, kaynak tüketimlerinin yüksek olmasına sebep olur.  

Docker ise farklı bir yaklaşım getirir:  
- Aynı işletim sisteminin kernelini kullanır.  
- Container’lar sadece gerekli bağımlılıkları içerir.  
- Bu sayede çok daha hafiftir ve saniyeler içinde başlatılabilir.

---

## Container Nedir?
Container, uygulamanın çalışan halidir.  
Bir image’den oluşturulur ve şunları sağlar:  
- İzole bir çalışma ortamı  
- İçinde uygulamanın tüm bağımlılıkları bulunur  
- Hızlı açılır ve kolayca silinebilir  
- İstenildiğinde farklı sunuculara taşınabilir  

Kısacası container, uygulamanın “taşınabilir kutusu” gibidir.

---

## Docker’ın Ortaya Çıkışı
Docker ilk kez 2013 yılında geliştirildi ve kısa sürede popüler oldu.  
Bunun sebebi:  
- Açık kaynak olması  
- Uygulamaları taşınabilir hale getirmesi  
- Geliştiriciler ve sistem yöneticileri arasında köprü oluşturması  

Bugün hemen hemen her bulut platformu Docker’ı destekliyor.

---

## Image ve Container Farkı
- **Image:** Bir şablondur. Uygulamanın çalışması için gerekli tüm dosyaları ve talimatları içerir.  
- **Container:** Image’in çalışan hali, yani uygulamanın canlı ortamda çalışan versiyonu.  

Bir image’den birden fazla container oluşturabilirsin.

---

## Container ve Sanal Makine Farkı
- Sanal makine: Her biri ayrı işletim sistemi barındırır → ağırdır.  
- Container: Ortak kernel üzerinde çalışır → çok daha hafif ve hızlıdır.  
- VM açılışı dakikalar sürebilirken, container saniyeler içinde hazır olur.

---

## Özet
- Docker, uygulamaları taşınabilir ve izole şekilde çalıştırmayı sağlar.  
- Container’lar sanal makinelerden farklı olarak daha hafif ve hızlıdır.  
- Image, container’ın şablonudur.  
- Kernel özellikleri (namespace, cgroups) sayesinde uygulamalar birbirinden bağımsız çalışır.  
- Docker, modern yazılım geliştirme ve devops süreçlerinde vazgeçilmez hale gelmiştir.
